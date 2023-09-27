# Nuevo informe ADR

El objetivo de este proyecto es mostrar en un nuevo informe datos de ADR y valores de carga, descarga y embalaje

## Estructura
Crearemos una nueva acción Informe ADR en _Facturación/Informes_.
Los criterios de búsqueda del informe serán:
* **Tipo ADR**: Mismos valores que el campo _Tipo ADR_ de artículos. Valor por defecto: ADR.
* **Intervalo de fechas** desde - hasta

El informe se realizará en formato excel, incluyendo las siguientes columnas:
* **Tipo operación**. Posibles valores:
	* Descarga
	* Carga
	* Embalaje
	
* **Clase ADR**. Con el valor del campo _Clasificación ADR_ de la ficha de artículos.
* **Grupo embalaje**. Con el valor del campo _ADR GE_ de la ficha de artículos.
* **Cantidad**. Producto de la cantidad calculada por el campo _Peso_ de la ficha del artículo . Siendo la cantidad:
	* **Descarga**: Suma de cantidad en albaranes de entrada (compra) en el intervalo.
	* **Carga**: Suma de cantidad en albaranes de salida (venta) en el intervalo.
	* **Embalaje**: Suma de cantidad en inventario a fecha fin del intervalo.