# Previsiones por agente

Las previsiones por agente permiten establecer unos objetivos de venta por cada agente comercial para un determinado período de tiempo.

## Crear una nueva previsión

* Abrimos el formulario de **Previsiones** en **Area de Facturación/Principal/Previsiones** y pulsamos *Insertar*.

* Indicamos el agente, el período de ventas.

* Indicamos el objetivo de ventas y rellenamos las pestañas de comisiones, bonificaciones, familias y subfamilias.

* Pulsamos el botón *Calcular datos*. Esto asociará las facturas del agente a la previsión y calculará los datos de la cabecera del formulario.

![Datos importados](./img/configuracionriesgo.png)
## Datos de cabecera

### Ventas comisionables
Sumatorio del campo *PVP Total* de las líneas de factura asociadas a la previsión, que cumplan los siguientes criterios:

* Que su familia tenga activado el check *Incluir en previsiones*.
* Que su cliente *NO* esté asociado a un grupo de compras.
* Que su cliente *NO* tenga marcado el check *Comisión especial* o que tenga marcado el check *Incluir en ventas comisionables*.

### Ventas alcanzadas
Sumatorio del campo *PVP Total* de las líneas de factura asociadas a la previsión, exceptuando aquellas que pertenezcan a clientes asociados a un grupo de compras.

### Ventas comisión especial
Sumatorio de la columna *Total ventas* de la tabla *Comisiones especiales*.

### Ventas alcanzadas G.C.
Sumatorio de la columna *Ventas* de la tabla *Bonificaciones* para aquellos registros asociados a un grupo de compras.

### Total
Suma de:
* *Comisión*
* *Comisión por Subfamilia*
* *Comisión especial*
* *Comisión G.C.*
* Si está activado el campo **, *Bonificación*

### % Comisión
Porcentaje de comisión a aplicar. Obtenido, si no se establece de forma manual, del tramo más alto de la tabla *Comisiones* cuya columna *Mínimo de ventas* sea menor a la suma de *Ventas alcanzadas* + *Ventas alcanzadas G.C.*

### Comisión
Producto de *Ventas comisionables* x *% Comisión*.

### Comisión por Subfamilia
Suma de la columna *Cantidad Comisión* de la tabla *Subfamilias*.

### Comisión especial
Suma de la columna *Total Comisión* de la tabla *Comisiones especiales*.

### Comisión G.C.
Producto de *Ventas alcanzadas G.C.* x *% Comisión*.

### Bonificación
Suma de la columna *Bonificación* de la tabla *Bonificaciones*.

## Tablas
### Comisiones
Taba manual para incluir los tramos de comisión.

### Facturas
Facturas asociadas a la previsión. Son las facturas que cumplen:
* Pertenecen al agente y al tramo de fechas especificado
* Su serie no está en la lista de *Series excluias de cálculo de previsiones* que se configura en *Área Facturación - Principal - Configuración - Datos generales*

### Bonificaciones
Bonificaciones aplicables.

**Bonificaciones por referencia**

Es posible crear una bonificación manual sobre la venta de una determinada referencia.

Las bonificaciones automáticas se calculan de la siguiente forma:

**Bonificaciones por subfamilia**

Registros de bonificación automáticos para los artículos que pertenecen a una subfamilia de la tabla *Familias* y quehan tenido ventas en facturas asociadas a la previsión, cumpliendo que:

* En las líneas de la factura no se ha activado el check *Excluir de bonificaciones*
* Su cliente no está en un grupo de compras
* Su cliente *NO* tenga marcado el check *Comisión especial*

El porcentaje de bonificación aplicado será el indicado en la familia.

**Bonificaciones por familia**

Mismo comportamiento que en *Bonificaciones por subfamilia*.

**Prioridad de aplicación**

El orden de aplicación de bonificaciones (el tipo de bonificación que se aplica para una referencia) es:

* Bonificación manual por referencia
* Bonificación por subfamilia
* Bonificación por familia


[...]