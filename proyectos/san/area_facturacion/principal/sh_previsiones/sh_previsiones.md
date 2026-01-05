# Previsiones por agente

Las previsiones por agente permiten establecer unos objetivos de venta por cada agente comercial para un determinado período de tiempo.

## Crear una nueva previsión

- Abrimos el formulario de **Previsiones** en **Area de Facturación/Principal/Previsiones** y pulsamos _Insertar_.

- Indicamos el agente, el período de ventas.

- Indicamos el objetivo de ventas y rellenamos las pestañas de comisiones, bonificaciones, familias y subfamilias.

- Pulsamos el botón _Calcular datos_. Esto asociará las facturas del agente a la previsión y calculará los datos de la cabecera y tablas del formulario.

## Datos de cabecera

### Ventas comisionables

Sumatorio del campo _PVP Total_ de las líneas de factura asociadas a la previsión, que cumplan los siguientes criterios:

- Que su familia tenga activado el check _Incluir en previsiones_.
- Que su cliente _NO_ esté asociado a un grupo de compras.
- Que su cliente _NO_ tenga marcado el check _Comisión especial_ o que tenga marcado el check _Incluir en ventas comisionables_.

### Ventas alcanzadas

Sumatorio del campo _PVP Total_ de las líneas de factura asociadas a la previsión, exceptuando aquellas que pertenezcan a clientes asociados a un grupo de compras.

### Ventas comisión especial

Sumatorio de la columna _Total ventas_ de la tabla _Comisiones especiales_.

### Ventas alcanzadas G.C.

Sumatorio de la columna _Ventas_ de la tabla _Bonificaciones_ para aquellos registros asociados a un grupo de compras.

### Total

Suma de:

- _Comisión_
- _Comisión por Subfamilia_
- _Comisión especial_
- _Comisión G.C._
- Si está activado el campo \**, *Bonificación\*

### % Comisión

Porcentaje de comisión a aplicar. Obtenido, si no se establece de forma manual, del tramo más alto de la tabla _Comisiones_ cuya columna _Mínimo de ventas_ sea menor a la suma de _Ventas alcanzadas_ + _Ventas alcanzadas G.C._

### Comisión

Producto de _Ventas comisionables_ x _% Comisión_.

### Comisión por Subfamilia

Suma de la columna _Cantidad Comisión_ de la tabla _Subfamilias_.

### Comisión especial

Suma de la columna _Total Comisión_ de la tabla _Comisiones especiales_.

### Comisión G.C.

~~Producto de _Ventas alcanzadas G.C._ x _% Comisión_.~~
Suma de la columna _Bonificación_ de la pestaña _Grupos de compras_.

### Bonificación

Suma de la columna _Bonificación_ de la tabla _Bonificaciones_.

## Tablas

### Comisiones

Taba manual para incluir los tramos de comisión.

### Facturas

Facturas asociadas a la previsión. Son las facturas que cumplen:

- Pertenecen al agente y al tramo de fechas especificado
- Su serie no está en la lista de _Series excluias de cálculo de previsiones_ que se configura en _Área Facturación - Principal - Configuración - Datos generales_

### Bonificaciones

Bonificaciones aplicables.

**Bonificaciones por referencia**

Es posible crear una bonificación manual sobre la venta de una determinada referencia.

Las bonificaciones automáticas se calculan de la siguiente forma:

**Bonificaciones por subfamilia**

Registros de bonificación automáticos para los artículos que pertenecen a una subfamilia de la tabla _Familias_ y quehan tenido ventas en facturas asociadas a la previsión, cumpliendo que:

- En las líneas de la factura no se ha activado el check _Excluir de bonificaciones_
- Su cliente no está en un grupo de compras
- Su cliente _NO_ tenga marcado el check _Comisión especial_
- El _% Descuento equivalente_ de la factura a la que pertenece la línea es inferior al _% Umbral de descuento_ de la subfamilia.

  - El _% Descuento equivalente_ se define como el resultado de:

    100 - (100 \* NetoFactura / NetoTeorico)

    donde:

    - _NetoFactura_ es el Neto de la factura
    - _NetoTeorico_ es la suma de los productos de _Cantidad_ de la línea x _PVP_ de la ficha de artículo de cada una de las líneas de la factura.

    Ejemplo: NetoFactura = 194, NetoTeorico = 200

    % Descuento equivalente = 100 - (100 \* 194 / 200) = 3 (3%)

    Hay que notar que al obtenerse el neto teórico del valor **actual** del campo _PVP_ de la lista de artículos, la ejecución del cálculo en distintos momentos, con distintos precios de ciertos artículos, puede dar lugar a distintos cálculos de bonificación aún sin modificar las condiciones de la previsión.

  - Si el umbral es nulo, se entiende que no hay umbral y que todas las líneas entran en la bonificación.

El porcentaje de bonificación aplicado será el indicado en la subfamilia.

**Bonificaciones por familia**

Mismo comportamiento que en _Bonificaciones por subfamilia_.

**Prioridad de aplicación**

El orden de aplicación de bonificaciones (el tipo de bonificación que se aplica para una referencia) es:

- Bonificación manual por referencia
- Bonificación por subfamilia
- Bonificación por familia

### Grupos de compra

Esta tabla tiene la misma estructura que la de _Bonificaciones_, y se aplica únicamente a clientes asociados a un grupo de compras.

Columnas:

- **Ventas** es la suma del campo _PVP Total_ de las líneas de las facturas asociadas al grupo de compras y a la previsión
- **% Bonificación** es el campo _% Bonificación_ del grupo de compras
- **Bonificación** se calcula como el producto de las columnas _Ventas_ x _% Bonificación_

### Subfamilias

Esta tabla permite indicar manualmente las subfamilias que tendrán una bonificación especial.

Cuando se realiza el cálculo de la previsión, la tabla informa sus columnas:

- **Cantidad facturada**: es la suma del campo _PVP Total_ de las líneas de las facturas asociadas a la subfamilia y a la previsión que:
  - No pertenecen a clientes en grupo de compras
- **% Comisión**: es el porcentaje de comisión que corresponde aplicar según la tabla de _Objetivos por subfamilia_ que puede editarse en cada registro de la tabla _Subfamilias_
- **% Comisión**: calculado como el producto de _Cantidad facturada_ x _% Comisión_
- **% Umbral de descuento**: D(2, 2). Indica el descuento equivalente máximo para que la factura entre en la bonificación.

### Subfamilias

Esta tabla permite indicar manualmente las familias que tendrán una bonificación especial.

### Comisiones especiales

Esta tabla muestra las comisiones especiales por cliente. Las principales columnas son:

- **Total ventas**: es la suma del campo _PVP Total_ de las líneas de las facturas asociadas al cliente y a la previsión, que:
  - Pertenezcan a familias familias con el check _Incluir en previsiones_ activado
  - No pertenezcan a clientes en grupo de compras
  - Pertenezcan a clientes con el check _Comisión especial_ activado
- **% Comisión**: Campo _% Comisión_ de la ficha de cliente
- **Total comisión**: Producto de _Total ventas_ x _% Comisión_
- **Es comisionable**: Campo _Incluir en ventas comisionables_ del cliente

[Volver al Índice](../../../index.md)
