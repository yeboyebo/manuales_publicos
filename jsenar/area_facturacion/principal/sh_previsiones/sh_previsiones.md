# Previsiones por agente

Las previsiones por agente permiten establecer unos objetivos de venta por cada agente comercial para un determinado período de tiempo.

## Crear una nueva previsión

* Abrimos el formulario de **Previsiones** en **Area de Facturación/Principal/Previsiones** y pulsamos *Insertar*.

* Indicamos el agente, el período de ventas.

* Indicamos el objetivo de ventas y rellenamos las pestañas de comisiones, bonificaciones, familias y subfamilias.

* Pulsamos el botón *Calcular datos*. Esto asociará las facturas del agente a la previsión y calculará los datos de la cabecera y tablas del formulario.

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
* El *% Descuento equivalente* de la factura a la que pertenece la línea es inferior al *% Umbral de descuento* de la subfamilia.
    * El *% Descuento equivalente* se define como el resultado de:

        100 - (100 * NetoFactura / NetoTeorico)
        
        donde:
        * *NetoFactura* es el Neto de la factura
        * *NetoTeorico* es la suma de los productos de *Cantidad* de la línea x *PVP* de la ficha de artículo de cada una de las líneas de la factura.

        Ejemplo: NetoFactura = 194, NetoTeorico = 200

        % Descuento equivalente = 100 - (100 * 194 / 200) = 3 (3%)

        Hay que notar que al obtenerse el neto teórico del valor **actual** del campo *PVP* de la lista de artículos, la ejecución del cálculo en distintos momentos, con distintos precios de ciertos artículos, puede dar lugar a distintos cálculos de bonificación aún sin modificar las condiciones de la previsión.

    * Si el umbral es nulo, se entiende que no hay umbral y que todas las líneas entran en la bonificación.


El porcentaje de bonificación aplicado será el indicado en la subfamilia.

**Bonificaciones por familia**

Mismo comportamiento que en *Bonificaciones por subfamilia*.

**Prioridad de aplicación**

El orden de aplicación de bonificaciones (el tipo de bonificación que se aplica para una referencia) es:

* Bonificación manual por referencia
* Bonificación por subfamilia
* Bonificación por familia

### Grupos de compra
Esta tabla tiene la misma estructura que la de *Bonificaciones*, y se aplica únicamente a clientes asociados a un grupo de compras.

Columnas:
* **Ventas** es la suma del campo *PVP Total* de las líneas de las facturas asociadas al grupo de compras y a la previsión
* **% Bonificación** es el campo *% Bonificación* del grupo de compras
* **Bonificación** se calcula como el producto de las columnas *Ventas* x *% Bonificación*

### Subfamilias
Esta tabla permite indicar manualmente las subfamilias que tendrán una bonificación especial.

Cuando se realiza el cálculo de la previsión, la tabla informa sus columnas:
* **Cantidad facturada**: es la suma del campo *PVP Total* de las líneas de las facturas asociadas a la subfamilia y a la previsión que:
    * No pertenecen a clientes en grupo de compras
* **% Comisión**: es el porcentaje de comisión que corresponde aplicar según la tabla de *Objetivos por subfamilia* que puede editarse en cada registro de la tabla *Subfamilias*
* **% Comisión**: calculado como el producto de *Cantidad facturada* x *% Comisión*
* **% Umbral de descuento**: D(2, 2). Indica el descuento equivalente máximo para que la factura entre en la bonificación.

### Subfamilias
Esta tabla permite indicar manualmente las familias que tendrán una bonificación especial.

### Comisiones especiales
Esta tabla muestra las comisiones especiales por cliente. Las principales columnas son:
* **Total ventas**: es la suma del campo *PVP Total* de las líneas de las facturas asociadas al cliente y a la previsión, que:
    * Pertenezcan a familias familias con el check *Incluir en previsiones* activado
    * No pertenezcan a clientes en grupo de compras
    * Pertenezcan a clientes con el check *Comisión especial* activado
* **% Comisión**: Campo *% Comisión* de la ficha de cliente
* **Total comisión**: Producto de *Total ventas* x *% Comisión*
* **Es comisionable**: Campo *Incluir en ventas comisionables* del cliente
