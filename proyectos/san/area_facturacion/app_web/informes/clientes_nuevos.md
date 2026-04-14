# Informe Clientes Nuevos

## ¿Qué hace este informe?

El informe **Clientes Nuevos** identifica clientes que **no habían realizado ningún pedido antes** de una fecha de corte indicada, pero **sí han pedido desde** esa fecha en adelante.

Opcionalmente se puede restringir la búsqueda a una o varias referencias de artículo concretas, de modo que la condición de "nuevo" se evalúa solo para esos productos.

Es útil para conocer qué clientes se han incorporado como compradores en un período determinado, ya sea en general o para un producto específico.

---

## Datos que muestra

### Tabla de clientes nuevos

| Columna       | Descripción                                                                          |
| ------------- | ------------------------------------------------------------------------------------ |
| _(checkbox)_  | Permite seleccionar el cliente para obtener su email                                 |
| **Código**    | Código de cliente                                                                    |
| **Nombre**    | Nombre o razón social del cliente                                                    |
| **Dirección** | Dirección de facturación (tipo de vía + calle + número + localidad + CP)             |
| **Teléfono**  | Teléfono de contacto                                                                 |
| **Email**     | Correo electrónico del cliente                                                       |
| **Fecha**     | Fecha del pedido más reciente desde la fecha de corte (primera compra en el período) |

---

## Cómo usar el informe

### 1. Indicar las referencias de artículo _(opcional)_

En la parte superior hay tres campos de búsqueda de artículo (**Ref. 1**, **Ref. 2**, **Ref. 3**). Son **opcionales**:

- Si se deja todo vacío, el informe busca clientes nuevos en sentido amplio: aquellos que no habían realizado ningún pedido antes de la fecha pero sí lo han hecho después, independientemente del artículo.
- Si se rellena al menos uno, la condición de "nuevo" se aplica solo a pedidos que contengan alguna de esas referencias.

Al seleccionar una referencia, la etiqueta muestra entre paréntesis el código elegido para confirmar la selección.

### 2. Indicar la fecha de corte

El campo **Desde fecha** es **obligatorio** y define el punto de corte temporal:

- Un cliente aparece si **no tiene** pedidos (con las referencias indicadas, si las hay) con fecha **anterior** a la fecha de corte.
- Y **sí tiene** al menos un pedido (con esas referencias) con fecha **igual o posterior** a la fecha de corte.

### 3. Lanzar el informe

Con la fecha rellenada se activa el botón **Lanzar**. Al pulsarlo se carga la tabla con los clientes nuevos.

> Si el botón **Lanzar** permanece desactivado, comprueba que:
>
> - La fecha de corte está informada.
> - Si el informe ya fue lanzado previamente, cambia algún parámetro o pulsa **Limpiar** primero.

### 4. Navegar por los resultados

La tabla se carga de forma progresiva mediante el scroll vertical. Al llegar al final del listado se cargan automáticamente los siguientes 20 registros si existen más.

Se puede **ordenar por cualquier columna** haciendo clic en su cabecera. Un segundo clic invierte el orden (ASC ↔ DESC). La ordenación solo está disponible cuando el filtro _Solo seleccionados_ no está activo.

### 5. Seleccionar clientes y obtener emails

1. Marca el **checkbox** de cada cliente que te interese.
2. Una vez hay al menos un cliente seleccionado, aparece la opción **Solo seleccionados** en la barra de acciones. Al activarla la tabla muestra únicamente los clientes marcados.
3. Pulsa el botón **Obtener emails** para abrir un diálogo con la lista de emails de los clientes seleccionados (uno por línea, separados por coma).
4. Dentro del diálogo, pulsa el icono de **Copiar** para copiar toda la lista al portapapeles y usarla en tu gestor de correo.

> Solo se incluirán en la lista los clientes que tengan email registrado.

### 6. Limpiar el formulario

El botón **Limpiar** restablece todos los filtros (referencias y fecha) y vacía la tabla de resultados. Se activa siempre que haya datos introducidos o resultados cargados.

---

## Reglas de negocio

- Se considera **nuevo** un cliente que cumple **ambas** condiciones simultáneamente:
  - **No tiene** ningún pedido (con las referencias indicadas, si las hay) con fecha **anterior** a la fecha de corte.
  - **Sí tiene** al menos un pedido (con esas referencias) con fecha **igual o posterior** a la fecha de corte.
- Solo se muestran clientes asignados a los **agentes permitidos** del usuario conectado.
- La **Fecha** mostrada corresponde al pedido más reciente desde la fecha de corte.

---

## Preguntas frecuentes

**¿Por qué no aparece ningún cliente?**
Puede deberse a que todos los clientes que han pedido desde la fecha de corte ya tenían pedidos anteriores, o a que no hay pedidos en ese período para los agentes asignados al usuario.

**¿Es obligatorio indicar referencias?**
No. Si no se indica ninguna referencia, el informe considera todos los artículos para determinar si un cliente es nuevo.

**¿El botón Lanzar está desactivado aunque tengo referencias?**
Las referencias son opcionales. Solo la fecha de corte es obligatoria para poder lanzar el informe.

**¿Puedo usar este informe para ver clientes que han empezado a comprar un producto concreto?**
Sí. Indica ese producto en uno de los campos de referencia y la fecha desde la que quieres considerar la actividad. Aparecerán los clientes que hayan pedido ese artículo desde esa fecha sin haberlo pedido antes.

[Volver al Índice](./index.md)
