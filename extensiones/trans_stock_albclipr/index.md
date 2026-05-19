# Transferencias de stock usando albaranes

## Estructura

### Albaranes de venta / Formulario de edición
Añadiremos a la pantalla los siguientes controles:

+ Tipo envío. Posibles valores
    + Albaran (valor por defecto)
    + Transferencia

+ Almacén destino. Relacionado con Almacenes. No requerido.

Cuando se elige Tipo envío = Albaran:
    + El campo _Almacén destino_ está vacío e inhabilitado

Cuando se elige Tipo envío = Transferencia:
    + El campo _Código de cliente_ está vacío e inhabilitado
    + El campo CIF está a un valor constante "-".
    + La dirección y nombre de cliente se obtienen al elegir el _Almacén destino_ de su ficha.


### Albaranes de transferencia / Formulario maestro

Una vez creado el albarán de transferencia podemos imprimirlo o enviarlo por agencia como cualquier otro albarán.

Para que el almacén de destino dé de alta el stock, crearemos un nuevo botón:

+ Recibir transferecia.
    + Al pulsarse:
        + Se genera un _albarán espejo_ en albaranes de compra para dar de alta el stock en el almacén de destino.
        + El albarán de transferencia seleccionado se pone en rojo (como si estuviera facturado) y no se puede modificar.
    + Habilitado solo cuando el albarán seleccionado es de tipo Transferencia y está desbloqueado (no está ya recibido)

+ Eliminar recepción. Usaremos el botón de desbloquear albarán que ya existe
    + Al pulsarse:
        + Se borra el _albarán espejo_ eliminándose el stock en el almacén de destino.
        + El albarán de transferencia seleccionado se pone en verde y se vuelve a poder modificar.
    + Habilitado:
        + Si el albarán es de tipo Albaran, como hasta ahora.
        + Si el albarán es de tipo Transferencia, solo cuando el albarán seleccionado es de tipo está bloqueado (está ya recibido)

Modificamos también la aceptación del formulario de albaranes de venta para que si son de tipo transferencia, se pregunte al usuario:
    `¿Quieres cerrar el albarán de transferencia generando el albarán espejo de entrada de mercancía?`
    Si el usuario contesta Sí, el albarán se cierra generándose la entrada de mercancía en el almacén de destino. 

El albarán de recepción espejo nunca será editable. Es siempre el inverso del albarán de transferencia.

