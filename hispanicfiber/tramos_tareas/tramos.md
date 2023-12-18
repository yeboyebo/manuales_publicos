# Generar orden produccion

## Configuración

Activamos gestión de tramos.

![activar_configuracion](./img/activar.png)


## Generar pedido

Las ordenes de producción se generar desde un pedido de compra. Una vez el pedido es generado se crean tantas ordenes como lineas contiene este pedido

![lineqa de pedido](./img/linea_pedido.png)



## Lanzar orden producción

Una vez generada la linea de pedido , tenemos que activar la orden de producción

![acceso_orden_producción](./img/acceso_orden_produccion.png)


Pulsamos sobre insertar orden de producción

![insertar_orden_producción](./img/insertar_orden_produccion.png)

Una vez dentro seleccionamos el pedido, pulsamos sobre la lupa y buscamos las posibles ordenes de producción. Estas lineas mostrarán los articulos disponibles y los que realmente necesitamos fabricar (A Fabricar)

![buscar_ordenes_producción](./img/formrecord_ordenes.png)

Hacemos doble click sobre la casilla Sel. de la linea y se marcará con una X

![posible_orden_sel](./img/posible_orden_sel.png)

Una vez seleccionadas las lineas , generamos las ordenes pulsando sobre el icono de rocket.

![icono_rocket](./img/icono_rocket.png)

Recibiremos un mensaje avisando de que los procesos han sido lanzados

![procesos_lanzados](./img/procesos_lanzados.png)

## Gestionar orden produción

Las ordenes se van gestionando desde la pestaña de terminal

![acceso_terminal](./img/acceso_terminal.png)

En esta pestaña el trabajador puede ir activando / desactivando las tareas de la orden de producción y añadiento tramos a esta.

![pestana_tramos](./img/pestana_tramos.png)

Los trabajadores pueden gestionar las tareas identificandose

![iniciar_tarea](./img/iniciar_tarea.png)


## Control de tramos

Si insertamos / editamos tramos o finalizamos una tarea , podemos actualizar la cantidad disponible de producto en el campo cantidad de la tarea.

![insertar_tramo](./img/insertar_tramo.png)

## Movimientos de stock

Cuando la tarea es la responsable de descontar componentes , los descuenta de almacén

![consumo](./img/consumo.png)


Cuando se finaliza la última tarea de la orden de trabajo , se actualiza el stock del articulo.


![lote](./img/lote.png)