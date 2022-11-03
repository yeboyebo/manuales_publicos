# Previsiones de compra

Las previsiones de compra nos permiten adelantar las neesidades de los productos de uno o más proveedores en base a fórmulas y estimaciones, y realizar los correspondientes pedidos de abastecimiento.

## Estructura de la tabla de previsiones
Las columnas de la tabla son las siguientes:
* Inc. Indica si la fila se incluirá en el pedido a proveedor.
* Proveedor
* Referencia
* Artículo
* R.E. Requiere embalaje. Obtenido del campo *Requiere embalaje* la tabla de *Artículos por proveedor*.
* U/E. Unidades por embalaje, del campo *Unidades por embalaje* la tabla de *Artículos por proveedor*.
* T1 ... T4. Unidades consumidas (albaranes de venta) en los cuatro trimestres anteriores al campo *Hasta* especificado.
* Total. Suma de T1 + T2 + T3 + T4.
* Actual. Cantidad física del artículo (stock) para el almacén indicado.
* Por servir. Cantidad reservada del artículo (stock) para el almacén indicado.
* Por recibir. Cantidad pendiente de recibir del artículo (stock) para el almacén indicado.
* Días. Campo *Plazo* de la tabla *Artículos por proveedor*. Si está vacío, se toma el campo *Plazo* de la ficha del proveedor.
* Fecha Pte. Recibir. Fecha y cantidad del siguiente pedido de compras a recibir. La fecha se calcula como la fecha del pedido más los *Días* de la fila.
* Stock Mín. Valor de stock mínimo en la tabla de stocks para el artículo y almacén indicados.
* Stock Máx. Valor de stock máximo en la tabla de stocks para el artículo y almacén indicados.
* Seg. Stock de seguridad. Calculado en base a fórmulas.
* A Pedir. Cantidad a pedir. Calculado en base a fórmulas.
* Coste. Campo *Coste* de la tabla *Artículos por proveedor*.
* %Dto. Campo *Descuento* de la tabla *Artículos por proveedor*.
* Vol.Art. Campo *Volumen* en la ficha del artículo.
* P.Mín. Importe de pedido mínimo que exige el proveedor. Campo *Importe pedido mínimo* de la ficha del proveedor (debe tener activado el check *Exige pedido mínimo* y la opción *Pedido mínimo por* debe estar asignada a *Importe*).
* Importe. Importe del pedido propuesto.
    
    En el caso de que el importe no llega al mínimo, se itera un número fijo de veces para aumentar los días de servicio (columna *Días*) con objeto de llegar al mínimo.

XXXX

### Prioridades de las fórmulas
Hay dos tipos de fórmulas:
* Stock de seguridad. Calcula el valor de la columna *Seg.* de la tabla.
* Cantidad a pedir. Calcula el valor de la columna *A Pedir* de la tabla.

El orden de cálculo es el siguiente

1. En el caso del *Stock de seguridad*, si se ha establecido un valor en el campo *Factor de seguridad*, se toma dicho valor ignorando las fórmulas.

1. Si el artículo está marcado en su ficha como *Personalizado*, la fórmula que se usa es la que hay establecida en el formulario de *Configuración* del módulo de *Almacén*, pestaña *A. Personalizados*.

1. Si existe una fórmula definida para el artículo y proveedor (tabla *Artículos por proveedor*), se usa dicha fórmula.

1. Si existe una tabla en la ficha del proveedor, se usa dicha fórmula.

### Proceso de cálculo


## Crear una nueva previsión

* Abrimos el formulario de **Previsiones de compra** en *Area de Facturación/Almacén/Más/Prev. Compras/Previsión*.

* Seleccionamos (opcionalmente) un proveedor.

* Si el almacén sobre el que vamos a aprovisionarnos nos es el almacén principal, lo modificamos.

* Indicamos las fechas *Desde* y *Hasta* si no queremos usar el año anterior como base de los cálculos.

* Pulsamos el botón de búsqueda (prismáticos)
    * La tabla se muestra con las siguientes columnas

* Indicamos el objetivo de ventas y rellenamos las pestañas de comisiones, bonificaciones, familias y subfamilias.

* Pulsamos el botón *Calcular datos*. Esto asociará las facturas del agente a la previsión y calculará los datos de la cabecera y tablas del formulario.

