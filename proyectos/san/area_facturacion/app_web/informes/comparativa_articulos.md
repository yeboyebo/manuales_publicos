# Informe Comparativa Clientes

## ¿Qué hace este informe?

El informe **Comparativa Clientes** permite analizar la evolución de las ventas (pedidos de clientes) comparando dos períodos —normalmente dos años distintos— y calcular automáticamente la variación porcentual entre ambos.

Incluye dos niveles de detalle:

1. **Vista de clientes** — lista de todos los clientes con su facturación en cada período y la variación.
2. **Vista de artículos** — al seleccionar un cliente concreto se muestra el detalle por artículo/referencia para ese cliente.

---

## Datos que muestra

### Tabla de clientes

| Columna         | Descripción                                                              |
| --------------- | ------------------------------------------------------------------------ |
| _(checkbox)_    | Permite seleccionar el cliente para obtener su email                     |
| **Código**      | Código de cliente                                                        |
| **Nombre**      | Nombre o razón social del cliente                                        |
| **Dirección**   | Dirección de facturación (tipo de vía + calle + número + localidad + CP) |
| **Teléfono**    | Teléfono de contacto                                                     |
| **Email**       | Correo electrónico del cliente                                           |
| **Total 1**     | Suma de pedidos del período 1 (año/trimestre seleccionado en _Año 1_)    |
| **Total 2**     | Suma de pedidos del período 2 (año/trimestre seleccionado en _Año 2_)    |
| **Variación %** | Incremento o decremento porcentual de Total 2 respecto a Total 1         |

> El color de cada fila indica la tendencia:
>
> - **Verde** → variación positiva (el cliente ha comprado más en el período 2).
> - **Rojo** → variación negativa (el cliente ha comprado menos en el período 2).

Solo aparecen clientes que tengan ventas en al menos uno de los dos períodos, y que estén asignados a los agentes del usuario que consulta.

### Tabla de artículos (detalle de cliente)

Se accede haciendo clic en una fila de la tabla de clientes.

| Columna         | Descripción                      |
| --------------- | -------------------------------- |
| **Referencia**  | Referencia del artículo          |
| **Descripción** | Descripción del artículo         |
| **Cantidad 1**  | Unidades pedidas en el período 1 |
| **Cantidad 2**  | Unidades pedidas en el período 2 |

> El color de fila también indica tendencia:
>
> - **Verde** → Cantidad 2 mayor que Cantidad 1.
> - **Rojo** → Cantidad 2 menor o igual que Cantidad 1.

La cabecera de esta tabla muestra un resumen del filtro activo:  
`Cliente: <nombre>; Año 1: <año>; Año 2: <año>; Trimestre: <T1/T2/T3/T4 | Todos los trimestres>`

---

## Cómo usar el informe

### 1. Seleccionar los períodos a comparar

En la parte superior del informe hay tres selectores:

- **Año 1** _(obligatorio)_ — período base de comparación. El desplegable muestra los últimos ~10 años.
- **Año 2** _(obligatorio)_ — período que se compara contra el Año 1.
- **Trimestre** _(opcional)_ — filtra ambos períodos al mismo trimestre del año. Si se deja vacío se usa el año completo.

  | Valor     | Período                  |
  | --------- | ------------------------ |
  | _(vacío)_ | 1 enero – 31 diciembre   |
  | T1        | 1 enero – 31 marzo       |
  | T2        | 1 abril – 30 junio       |
  | T3        | 1 julio – 30 septiembre  |
  | T4        | 1 octubre – 31 diciembre |

### 2. Lanzar el informe

Una vez elegidos al menos **Año 1** y **Año 2**, se activa el botón **Lanzar**. Al pulsarlo se carga la tabla de clientes.

> Si el botón **Lanzar** permanece desactivado, comprueba que:
>
> - Los dos años están seleccionados.
> - Si ya se lanzó y no se ha limpido el formulario, cambia algún parámetro o pulsa **Limpiar** primero.

### 3. Navegar por los resultados

La tabla carga resultados de forma progresiva usando el scroll vertical. Al llegar al final de la lista se cargan automáticamente los siguientes 20 registros, siempre que existan más.

Se puede **ordenar por cualquier columna** haciendo clic en su cabecera. Un segundo clic invierte el orden (ASC ↔ DESC).

### 4. Ver el detalle de artículos de un cliente

Haz clic en cualquier fila de la tabla de clientes. Se abrirá la vista de artículos para ese cliente con los mismos filtros de período activos. La tabla de artículos también soporta carga por scroll vertical y ordenación por columna.

Para volver al listado de clientes usa el botón de navegación atrás del navegador o la navegación de la aplicación.

### 5. Seleccionar clientes y obtener emails

1. Marca el **checkbox** de cada cliente que te interese. Los clientes seleccionados quedan destacados.
2. Una vez hay al menos un cliente seleccionado, aparece la opción **Solo seleccionados** (icono de checkbox en la barra de acciones). Al activarla la tabla muestra únicamente los clientes marcados.
3. Pulsa el botón **Obtener emails** para abrir un diálogo con la lista de emails de los clientes seleccionados (uno por línea).
4. Dentro del diálogo, pulsa el icono de **Copiar** para copiar toda la lista al portapapeles y usarla en tu gestor de correo.

> Solo se incluirán en la lista los clientes que tengan email registrado.

### 6. Limpiar el formulario

El botón **Limpiar** restablece todos los filtros y vacía la tabla de resultados. Se activa siempre que haya algún dato introducido o resultados cargados.

---

## Reglas de negocio

- La fórmula de variación aplicada es:

$$
\text{Variación \%} =
\begin{cases}
0 & \text{si } \text{Total}_1 = 0 \text{ y } \text{Total}_2 = 0 \\
100 & \text{si } \text{Total}_1 = 0 \text{ y } \text{Total}_2 \neq 0 \\
\dfrac{(\text{Total}_2 - \text{Total}_1) \times 100}{\text{Total}_1} & \text{en el resto de casos}
\end{cases}
$$

El resultado se redondea a 2 decimales.

- Solo se muestran clientes asignados a los agentes permitidos **(el agente y sus subordinados)** del usuario que está conectado.
- Solo aparecen clientes con al menos un total distinto de cero (en cualquiera de los dos períodos).
- Los totales provienen de la tabla de pedidos de clientes, no de facturas.

---

## Preguntas frecuentes

**¿Por qué no aparece ningún cliente tras lanzar el informe?**  
Es posible que no haya pedidos en los períodos indicados para los clientes asignados a tu agente, o que el usuario no tenga agentes asociados.

**¿Por qué el botón Lanzar está desactivado?**  
Necesitas seleccionar obligatoriamente _Año 1_ y _Año 2_. Si el informe ya fue lanzado, el botón se reactiva al cambiar cualquier parámetro.

**¿Puedo comparar el mismo año con sí mismo?**  
Sí. Si seleccionas el mismo año en _Año 1_ y _Año 2_ la variación será siempre 0 %, lo que puede ser útil para ver el listado de clientes activos en un período determinado.

**¿El trimestre afecta a los dos años por igual?**  
Sí. El filtro de trimestre se aplica al mismo rango de meses en ambos años.
