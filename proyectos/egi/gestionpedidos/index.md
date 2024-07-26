# Gestión de pedidos

Podemos acceder a la ficha clicando en el botón *Ir al pedido* tanto de la ficha de una [orden de producción](../ordenesproduccion/index.md) como de la pantalla de una [tarea](../gestiontareas/index.md) del terminal.

## Datos del pedido

En la ficha veremos los datos del cliente(código y nombre) y la fecha del pedido.

## Botón generar albarán

En la parte superior izquierda está el botón *generar albarán* que utilizaremos para generar un albarán parcial sobre el pedido. Utilizaremos las cantidades a enviar asociadas a las líneas del pedido que sean mayor de 0. Se no pedirá una confirmación para generar el albarán. Podremos firmar el albarán desde la pantalla [firmar](../firmaalbaranes/index.md) del menu de albaranes.
 
## Líneas del pedido

Veremos un listado con las diferentes líneas de producto realcionadas con el pedido, en cada línea se mostrará la siguiente información:

- **Pedida**: Cantidad total de producto pedida.

- **Servida**: Cantidad total de producto ya servida.

- **Pendiente**: Cantidad pendiente de servir.

- **Fabricada**: Cantidad total fabricada.

- **Lista para servir**: Cantidad fabricada aún no servida.

- **A enviar**: Es la cantidad que se asignará al albarán que generemos con el botón *generar albarán*, por defecto será la misma cantidad que *Lista para servir*. Será una cantidad editable al hacer clic sobre la misma, nunca pudiendo superar la cantidad de *Lista para servir*.


[Volver al Índice](../index.md)