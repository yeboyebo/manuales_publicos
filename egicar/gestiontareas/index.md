# Cómo gestionar tareas

Desde la pantalla **Tareas de terminal** tendremos acceso a la gestión de tareas. Solo tendrán acceso los usuarios que tengan asociado un trabajador, si no lo está veremos el mensaje *'Este usuario no está asociado a ningún trabajador'*.

Una vez hayamos accedido a la pantalla, veremos un cuadro de búsqueda en el que ingresar un código de tarea, este se buscará y si la tarea existe veremos su descripción y código, la orden de producción al que pertence, el árticulo a fabricar, los utillajes que se encesitan en el proceso de fabricación, obsrvaciones a la tarea y el estado y las posibles acciones a realizar dependiendo del mismo. Si el código de tarea buscado no se encuentra veremos un mensaje de aviso indicando que la tarea no existe.

Podremos navegar a la ficha de la [orden de producción](../ordenesproduccion/index.md) a la que pertence la tarea clicando en el botón *Ir a la orden* situado junto a al código de la orden.

Podremos navegar a la ficha del del pedido al que pertence la tarea clicando en el botón *Ir al pedido* situado junto a al código de la orden, desde donde podremos generar albranes parciales de envío con la cantidad ya fabricada..

## Estados de tarea

- **Pendiente**: Podremos iniciarla haciendo clic en el botón.

- **En curso**: Podremos detenerla haciendo clic en el botón. Debemos introducir la cantidad que se ha producido en el tramo durante el cual la tarea ha estado en curso y si deseamos terminar la tarea, en caso afirmativo la tarea pasará al estado *terminada* y si no al estado *en pausa*.

- **En pausa**: Podremos reiniciar haciendo clic en el botón y la tarea pasará al estado *en curso*.

- **Terminada**: Este estado solo permitirá ver la información de la tarea.

## Tramos de tarea

En la parte inferior podremos ver los tramos que se han producido para la tarea. En el mostramos el usuario que lo creó, la cantidad que se produjo en ese tramo y la fecha y hora de inicio y fin.

También podremos eliminar el tramo. ¿Permisos?¿Tarea terminada?

[Volver al Índice](../index.md)