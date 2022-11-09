# Previsiones de compra

Las previsiones de compra nos permiten adelantar las neesidades de los productos de uno o más proveedores en base a fórmulas y estimaciones, y realizar los correspondientes pedidos de abastecimiento.

## Configuración
[NUEVO>]

### Parámetros de almacén

En Facturación - Almacén - Configuración, podemos editar la fórmula de previsión de inteligencia artifucual, en la pestaña *Previsión IA*.

Los parámetros de entrada de la fórmula son:
```js
/* Parmetros del objeto o que pueden ser usados en la formula:
 * o.DS_IA: Dias de servicio según IA
 * o.CM_IA: Consumo mensual según IA
 * o.FS: Factor de seguridad
 * o.RS: Stock reservado
 * o.PR: Stock pendiente de recibir
 * o.SA: Stock actual
*/
o = arguments[0]; /// NO BORRES ESTAS LINEAS
for (d in o) 
  o[d] = parseFloat(o[d]);

// Fórmula por defecto:
return parseFloat(o.RS) - parseFloat(o.PR) - parseFloat(o.SA) + parseFloat(o.CM_IA) * (o.DS_IA/30) * parseFloat(o.FS)
//////////////////////////////////////////////////
```
### Artículos por proveedor
* Factor de seguridad. D(3, 2).

XXX
* Comprobar carga en memoria de jsenar_cargaDatosIA
* Cambiar la carga de las dos columnas a una función que busque en el diccionario y devuelva 0 si no está

### Proveedores
* Factor de seguridad. D(3, 2).
[<NUEVO]

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
* Días. El órden de cálculo es:
    * Campo *Días de servicio* de la cabecera del formulario de previsión de compras.
    * Campo *Plazo* de la tabla *Artículos por proveedor*.
    * Campo *Plazo* de la ficha del proveedor. 
* Fecha Pte. Recibir. Fecha y cantidad del siguiente pedido de compras a recibir. La fecha se calcula como la fecha del pedido más los *Días* de la fila.
* Stock Mín. Valor de stock mínimo en la tabla de stocks para el artículo y almacén indicados.
* Stock Máx. Valor de stock máximo en la tabla de stocks para el artículo y almacén indicados.
* Seg. Stock de seguridad. Orden de cálculo:
    * Campo *Factor de seguridad* del formulario de previsión de compras.
    * Calculado en base a fórmulas.
* A Pedir. Cantidad a pedir. Calculado en base a fórmulas.
* [NUEVO] ! C.M. Consumo mensual. Valor estimado para cada artículo según AI.
* [NUEVO] ! D.S. Días de servicio. Valor estimado para cada artículo según AI.
* [NUEVO] ! F.S. Factor de seguridad. Calculado en este orden:
    * Campo *Factor de seguridad* de la tabla de *Artículos por proveedor*.
    * Campo *Factor de seguridad* de la ficha de proveedor.
    * Valor 1.
* [NUEVO] ! A Pedir. Cantidad a pedir según fórmula de IA

* Coste. Campo *Coste* de la tabla *Artículos por proveedor*.
* %Dto. Campo *Descuento* de la tabla *Artículos por proveedor*.
* Vol.Art. Campo *Volumen* en la ficha del artículo.
* P.Mín. Importe de pedido mínimo que exige el proveedor. Campo *Importe pedido mínimo* de la ficha del proveedor (debe tener activado el check *Exige pedido mínimo* y la opción *Pedido mínimo por* debe estar asignada a *Importe*).
* Importe. Importe del pedido propuesto.
    
    En el caso de que el importe no llega al mínimo, se itera un número fijo de veces para aumentar los días de servicio (columna *Días*) con objeto de llegar al mínimo.

* V. Min. Volumen mínimo de la ficha del proveedor (debe tener activado el check *Exige pedido mínimo* y la opción *Pedido mínimo por* debe estar asignada a *Volumen*).
* FCC. Id del registro de fórmula de *Cantidad a comprar* si hay una fórmula específica para el producto y el proveedor seleccionados (valor 0 si no la hay).
* FSS. Id del registro de fórmula de *Stock de seguridad* si hay una fórmula específica para el producto y el proveedor seleccionados (valor 0 si no la hay).
* Personalizado. Indica si el artículo tiene activo el campo *Personalizado* en su ficha.
* Cons.Mensual. Valor del campo *Consumo mensual* en la ficha del artículo.
* Última Cant. Entregada. Valor del campo *cantidad* en la última línea de albarán de compra registrada.
* Producto Sustitutivo. Valor del campo *Producto sustitutivo* en la ficha del artículo.
* En sustitución. Valor del campo *En sustitución* en la ficha del artículo.
* Sustitutorio. Indica si el producto de la línea actúa como artículo sustitutorio de un artículo en sustitución.
* Sustituye A. Para un artículos sustitutorio, indica a que artículo en sustitución sustituye.

### Prioridad de las fórmulas
Tanto para *Stock de seguridad* como para *Cantidad a comprar*, se busca de la fórmula más concreta a la más general:
* En la tabla de *Artículos por proveedor*.
* En la ficha del proveedor.
* En la fórmula genérica de cada tipo.

## Generar una previsión de compras
* Vamos a *Facturación > Almacén > Más > Previsión de compras > Previsión*.

* Seleccionamos (opcionalmente) el proveedor.

* Seleccionamos (opcionalmente) las fechas desde - hasta.

* Indicampos (opcionalmente) los valores de *Días de Servicio* y *Factor de seguridad*.

* Pulsamos el botón *Buscar*.

    * La tabla de líneas de productos a pedir se informa

* Deseleccionamos (opcionalmente) las líneas que no queramos pedir (columna *Inc*).

* Modificamos (opcionalmente) las cantidades de la columna *A Pedir*.

* Pulsamos el botón *Generar pedidos*.

    * Se genera un pedido por cada proveedor que tenga al menos una línea incluida en la lista con cantidad *A pedir* positiva.

