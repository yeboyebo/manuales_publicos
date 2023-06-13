# Generar pedidos con lector de código de barras

## Configuraciones previas

* Entramos en la opción **Area de facturación -> Facturación -> Almacén -> Configuración** y en la pestaña **Datos generales** informamos el campo **Familia servicios**

* Entramos en la opción **Area de facturación -> Facturación -> Almacén -> Configuración** y en la pestaña **Datos generales** informamos el campo **Serie servicios**

* Entramos en la opción **Area de facturación -> Facturación -> Almacén -> Colores** y creamos tantos registros de colores como sean necesarios

* Entramos en la opción **Area de facturación -> Facturación -> Almacén -> Materiales** y creamos tantos registros de materiales como sean necesarios

* Para cada cliente para el que queramos crear pedidos o albaranes con el lector de codigo de barras debemos informar el valor de etiqueta. Para ello:
  - entramos en **Area de facturación -> Facturación -> Principal -> Clientes**.
  - Abrimos el formulario de edición del cliente que corresponda y en la pestaña **Comercial** Informamos el campo **Etiqueta**. Este campo debe ser un código numérico de 4 dígitos.

  Nota: Para que funcione correctamente, los clientes que vayamos a utilizar y tengan cofigurado un código de etiqueta deben tener creada una **dirección de facturación** en la pestaña de **Direcciones**

## Creación de pedidos

* Entramos en **Area de facturación -> Facturación -> Pedidos de Venta**

* En el cuadro de texto en blanco de la parte superior leemos el código de barras de la prenda. El código de barras debe componerse de 10 dígitos:
  - Los cuatro primeros deben corresponder a la etiqueta del cliente configurada previamente.
  - El siguiente dígito será un guión
  - Los últimos 5 dígitos son identificativos de la prenda. 
  
  Ej. 1234-56789

* Después de leer el código de barras aparecerá una ventana en la que debemos indicar:
  - El color y material de la prenda obtenidos de las tablas de colores y materiales infromadas anteriormente.
  - La referencia del ariculo que deberá ser una referencia perteneciente a la familia de servicios.
  - Opcionalmente podremos establecer las observaciones que luego irán en la cabecera del pedido. 

* Una vez establecidos los datos se creará de forma automática un pedido donde:
  - El cliente será el cliente con numero de etiqueta del codigo de barras
  - La serie del pedido será la serie establecida previamente en los datos de configuración del módulo de Almacén.
  - Y una línea para la prenda, con la configuración de color y material y artículo especificados

  Nota: Si ya existiése un pedido para el mismo cliente, con fecha de hoy y no servido, en lugar de crear un pedido nuevo, se creará una línea nueva en el pedido existente.

## Creación de albaranes

* Entramos en **Area de facturación -> Facturación -> Pedidos de Venta**

* En el cuadro de texto en blanco de la parte superior leemos el código de barras de la prenda. Esa prenda ha debido de crearse anteriormente en un pedido. 
  - Si no existe esa prenda en ningún pedido aparecerá un mensaje de error.
  - Si existe generará un albarán para ese cliente y lo asociará al pedido generado, dejando el pedido como servido.
  - La serie del albarán será la serie establecida previamente en los datos de configuración del módulo de Almacén.
  - Antes de generar la línea de albarán aparecerá la misma ventana que en pedidos informando de los datos de esa prenda (color, material y referencia)
  - Si ya existe un albarán para ese cliente, fecha de hoy y no facturado se creará una nueva línea en el albarán existente.