# Genrar pedidos con lector de codigo de barras

## Configuraciones previas

* Entramos en la opción **Area de facturación -> Facturación -> Almacén -> Configuración** y en la pestaña **Datos generales** informamos el campo **Familia servicios**

* Entramos en la opción **Area de facturación -> Facturación -> Almacén -> Colores** y creamos tantos registros de colores como sean necesarios

* Entramos en la opción **Area de facturación -> Facturación -> Almacén -> Materiales** y creamos tantos registros de materiales como sean necesarios

* Para cada cliente para el que queramos crear pedidos o albaranes con el lector de codigo de barras debemos informar el valor de etiqueta. PAra ello entramos en **Area de facturación -> Facturación -> Principal -> Clientes**. Abrimos el formulario de edición del cliente que corresponda y en la pestaña **Comercial** Informamos el campo **Etiqueta** Este campo debe ser un código numérico de 4 dígitos.
  Nota: Para que funcione correctamente, los clientes que vayamos a utilizar y tengan cofigurado un código de etiqueta deben tener creada una **dirección de facturación** en la pestaña de **Direcciones**

## Creación de pedidos

* Entramos en **Area de facturación -> Facturación -> Pedidos de Venta**

* En el cuadro de texto en blanco de la parte superiro, al lado de la barra de botones leemos el código de barras de la prenda.
  El código de barras debe componerse de 10 dígitos. Los cuatro primeros deben corresponder a la etiqueta del cliente configurada previamente. El siguiente dígito será un guión, y después 5 dígitos numéricos identificativos de la prenda. Ej. 1234-56789

* Después de leer el código de barras aparecerá una ventana en la que debemos indicar:
  - el color y material de la prenda obtenidos de las tablas de colores y materiales infromadas anteriormente.
  - La referencia del ariculo que deberá ser una referencia perteneciente a la familia de servicios especificada especificada anteriormente.
  - Opcionalmente podremos establecer las observaciones necesarias. 

* Una vez establecidos los datos se creará de forma automática un pedido, con el cliente correspondiente y una línea para la prenda
  Si ya existiése un pedido para el mismo cliente, con fecha de hoy y no servido, en lugar de crear un pedido nuevo, se creará una línea nueva en el pedido existente.

## Creación de albaranes

* Entramos en **Area de facturación -> Facturación -> Pedidos de Venta**

* En el cuadro de texto en blanco de la parte superiro, al lado de la barra de botones leemos el código de barras de la prenda. Esa prenda ha debido de crearse anteriormente en un pedido. 
  - Si no existe esa prenda en ningún pedido aparecerá un mensaje de error.
  - Si existe generará un albarán para ese cliente y lo asociará al pedido generado, dejando el pedido como servido.
  Antes de generar la línea de albarán aparecerá la misma ventana que en pedidos informando de los datos de esa prenda (color, material y referencia)