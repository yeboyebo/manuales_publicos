# Inventario valorado

Este informe muestra, según los filtros aplicados los artículos, sus cantidades de stock y su coste. 

## Estructura
En los criterios de búsqueda del informe hay un campa **Valor según** en el que podemos elegir entre las siguientes opciones:

* **Coste medio**  Es el pvp total en lineas de facturas de proveedor dividido entre la cantidad total
* **Coste medio meses** Si está informado el intervalo de fechas del coste medio, el cálculo será el mismo qeu **Coste medio** pero para las para las facturas comprendidas en el intervalo
* **Ultimo coste** Es el precio unitario de la ultima factura de proveedor
* **PVP** Precio de venta del artículo
* **Coste prov** El coste establecido para el proveedor por defecto

Los costes de un artículo compuesto se calcularán como la suma de los costes de sus componentes multiplicado por la cantidad de composición
	
Los costes de un artículo compoente de otro marcado con el check **Contro stock por componentes** se calculará como el coste del compuesto dividido entre la cantidad de composición