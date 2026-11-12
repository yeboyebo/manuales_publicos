# Registro de actividad de usuarios (navegación y acciones)

*Análisis, 12/11/2026*

## Contexto

Un cliente quiere saber cómo usan los usuarios la aplicación: a qué pantallas entran y qué hacen en ellas (crear una tarea de CRM, etc.).

Lo mejor es separarlo en dos partes, porque cada una tiene un sitio natural distinto en la arquitectura:

- **Navegación**: se registra en el frontend (`quimera-olula`).
- **Acciones**: se registran en el backend (`olula_servidor`), en el bus de comandos.

## 1. Acciones: interceptar el bus de comandos (backend)

Todas las acciones de escritura pasan por un único sitio: `lanzar_comando` en
`olula_servidor/comun/buses/comandos/infraestructura/memo_bus_comandos.py`. Ahí ya se conocen
el `tipo` del comando, el `usuario` y el `grupo`. Basta con envolver la llamada al manejador:

```python
def lanzar_comando(validar_permiso: ValidarPermiso) -> LanzarComando:
    def _(comando: Comando, usuario: Usuario, grupo: Grupo) -> None:
        tipo = comando.tipo
        if tipo not in manejadores:
            raise ValueError(f"Comando no soportado: {tipo}")

        manejador = manejadores[tipo]
        inicio = time.monotonic()
        try:
            resultado = manejador(validar_permiso)(comando, usuario, grupo)
            registrar_actividad(tipo, usuario, grupo, "ok", inicio)
            return resultado
        except Exception as e:
            registrar_actividad(tipo, usuario, grupo, type(e).__name__, inicio)
            raise
    return _
```

Ventajas:

- Cubre todos los comandos, también los que se añadan en el futuro, sin tocar ningún módulo.
- Registra también los **intentos fallidos** (errores de validación o de permisos), que suelen
  interesar al cliente para ver dónde se atasca la gente.

### ¿Por qué no usar los eventos de dominio?

Los eventos ya llevan `usuario_id` y `timestamp`, pero habría que suscribirse evento a evento y
no recogen las acciones que fallan. Quedan como opción cuando haga falta más detalle de negocio.

### Ojo con el payload

Guardar solo el tipo de comando y, como mucho, el id de la entidad afectada. El comando completo
no, porque puede llevar datos personales de clientes.

## 2. Navegación: hook en el frontend

Las consultas del backend no sirven para esto, porque una pantalla lanza varias consultas y
algunas consultas se usan en varias pantallas. Lo correcto es hacerlo en el router
(`quimera-olula/apps/olula/src/main.tsx` usa `createBrowserRouter`):

- Un hook `useRegistroNavegacion()` en el layout raíz que escucha `useLocation()`.
- Normalizar la URL a su **patrón** con `matchRoutes` (`/crm/tarea/:id` en vez de
  `/crm/tarea/1234`), para poder agregar los datos.
- Guardar entrada y salida para tener el tiempo de permanencia en cada pantalla.
- Mandarlo en lotes (cada N segundos y con `navigator.sendBeacon` al cerrar la pestaña) a un
  endpoint `POST /actividad/navegacion`, para no hacer una petición por cada clic.

### Relacionar navegación y acciones

El frontend genera un `sesion_id` y lo envía como cabecera desde `RestAPI`
(`packages/lib/src/api/rest_api.ts`). El backend lo adjunta al registrar cada comando, y así se
puede reconstruir el recorrido completo:

> entró en Tareas → abrió la tarea → creó una tarea → volvió al listado

## 3. Almacenamiento

Una tabla en PostgreSQL, que con SQL permite sacar los informes para el cliente:

```sql
CREATE TABLE IF NOT EXISTS actividad_usuario (
  id           bigserial PRIMARY KEY,
  momento      timestamptz NOT NULL DEFAULT now(),
  usuario      text NOT NULL,
  grupo        text,
  sesion_id    text,
  tipo         text NOT NULL,   -- 'navegacion' | 'comando'
  nombre       text NOT NULL,   -- '/crm/tarea/:id' | 'crm.tarea.crear'
  resultado    text,            -- 'ok' | nombre del error
  duracion_ms  int,
  detalle      jsonb
);
```

Consideraciones:

- La escritura no debe añadir latencia ni romper el comando si falla: hacerla en segundo plano
  (o a través de la cola de eventos) y capturando cualquier error.
- Ya existe `comun/log` con Loki, pero está pensado para operación. Para informes de uso es más
  cómodo PG.
- La migración debe ser idempotente, como el resto.

### Alternativa: herramienta externa

**PostHog o Matomo autoalojados** resuelven bien la parte de navegación (con embudos y mapas de
calor). Aun así, las acciones conviene seguir registrándolas en el bus de comandos, porque es la
fuente fiable.

## 4. Aviso legal

Registrar la actividad de los empleados de un cliente es monitorización laboral (art. 87 LOPDGDD
y art. 20.3 ET):

- El cliente tiene que informar a sus usuarios.
- Conviene definir cuánto tiempo se guardan los datos.
- Conviene un interruptor por instalación para activarlo o desactivarlo. Encaja bien como
  **plugin** (`activo`/`inactivo`) según la arquitectura del servidor.

## Plan de implementación propuesto

1. Backend: migración de la tabla `actividad_usuario`.
2. Backend: registro en `lanzar_comando` (como plugin activable por app).
3. Backend: endpoint `POST /actividad/navegacion` para recibir los lotes del frontend.
4. Frontend: cabecera `sesion_id` en `RestAPI`.
5. Frontend: hook `useRegistroNavegacion()` en el layout raíz.
6. Consultas/informes para el cliente.

## Decisiones pendientes

- ¿Se guarda el id de la entidad afectada en las acciones?
- ¿Se implementa como plugin activable por app?
- ¿Cuánto tiempo se conservan los registros?
