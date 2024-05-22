En ese caso, necesitaríamos un esbozo de lo que sería el sistema: funcionalidades, stack, arquitectura aproximada.

# Funcionalidades estándar

## Funcionalidades de almacén

### Escandallo adaptado a textil (tallas y colores)

### Aprovisionamiento adaptado a textil
`ITIS` > Registro de entrada

### Venta adaptada a textil
`ITIS` > Registro de salida producto


## Funcionalidades de producción

### Uso de partidas como unidad de venta y producción

### Asociación de procesos configurables a cada modelo

### Seguimiento de tareas (inicio / fin)
`ITIS` > Registro de inicio y fin de tarea

### Descuento de materiales por tarea
`ITIS` > Registro de consumo

### Registro de incidencias y creación de subpartidas


## Estadística

### Producción: tiempos y productividad

### Producción: incidencias, frecuencia y coste

### Almacén: consumos por producto


# Funcionalidades economía circular

## Funcionalidades de almacén

### Escandallo incluye la generación de subproductos (retales, etc.) reciclables

### Escandallo incluye _opciones_ de materiales / subproductos reciclables

### Trazabilidad de algunos materiales reutilizados clave
`ITIS` > Trazabilidad

### Venta o registro de salida de subproductos (retales, etc.) reciclables
`ITIS` > Registro de salida subproducto reciclable

## Funcionalidades de producción

### Indicación de uso de opción reciclable en órdenes de fabricación

### Cómputo de %reciclable de materiales por orden de producción

### Cómputo de subproductos reciclables generados (retales, etc.) 
`ITIS` > Pesaje y alta automática, distintos tipos de material / contenedores.

## Estadística

### Subproductos generados

### Porcentaje de material reciclado utilizado


# Stack

## Frontend gestión: App javascript

## Frontend planta (almacén y fábrica): App javascript

### Sensores, antenas frontend planta
`ITIS` > Infraestructra __describir opciones para entrada, salida, alta, inicio tarea, fin tarea, consumo y trazabilidad__

## Frontend estadística: App javascript

## Backend: App node / typescript

## Backend estadística: Python / librerías de gestión de datos

Indicador de reusabilidad, reciclaje
50% sobre el presupuesto
Colaboradores con sus propios gastos

10% a éxito

• La trazabilidad de productos, sustancias, materiales y residuos
• Nuevos modelos de negocio basados en la digitalización como
instrumento para procesos de servitización
• Servicios de retorno de productos usados para reutilizarlos,
remanufacturarlos o reciclarlos

Residuos
Recogida de retales y sobrantes en toda la cadena de producción
Seguimiento de los retales hasta su salida (albaranes de salida)
Gestión de retales como subproductos con referencia específica

Cierre de tarea de corte con pesaje de retales y generación de stock de retal

Reutilización
Identificación de materias primas y semielaborados ya reciclados > cálculo del porcentaje de producto reciclado por producto ¿Indicador?
Catalogación de materias primas en función de toxicidad o posibilidad de reciclaje
Componentes sustitutivos y grado de uso en producciones ¿Indicador?
Catálogo con productos y sustitutivos para ciertas composiciones / tareas de producción
Permitir la introducción paulatina de materiales reciclados en los procesos de producción