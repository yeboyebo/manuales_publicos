# Localizar artículos por código de barras

Desde el listado de artículos podemos localizar un artículo leyendo su código de barras con la pistola lectora o escribiéndolo a mano.

## Dónde está

Vamos al formulario de artículos desde el menú **Area de Facturación/Almacen/Artículos**.

Debajo de la barra de botones aparece el campo **Código de barras:**. Al abrir el formulario el cursor ya está situado en este campo, de modo que podemos leer directamente con la pistola sin tener que hacer clic en él.

## Cómo buscar

1. Leemos el código de barras con la pistola o lo escribimos en el campo **Código de barras:**.
2. Pulsamos **Intro**. La mayoría de pistolas envían el Intro automáticamente al final de la lectura, así que normalmente no hace falta pulsarlo.
3. El listado de artículos se filtra y muestra únicamente el artículo encontrado, ya seleccionado. Desde ahí podemos abrirlo, editarlo o imprimir sus etiquetas como de costumbre.

El texto del campo queda seleccionado, así que podemos leer el siguiente código directamente y sustituirá al anterior.

Si no existe ningún artículo con ese código, se muestra el mensaje *No se ha encontrado ningún artículo con el código ...* y el listado no cambia.

## Volver a ver todos los artículos

Borramos el contenido del campo **Código de barras:** y pulsamos **Intro**. El listado vuelve a mostrar los artículos que se veían antes de la primera búsqueda.

## Qué códigos encuentra

El sistema busca el código leído en este orden y se queda con el primer artículo que encuentre:

1. Los **códigos de barras adicionales** del artículo, que se dan de alta en la pestaña **Cód. Barras** de la ficha del artículo. Un mismo artículo puede tener varios.
2. El **código de barras principal** de la ficha del artículo.
3. La **referencia** del artículo, por si queremos buscarlo escribiendo su referencia.

El código tiene que coincidir completo y exactamente: no se buscan coincidencias parciales.

[Volver al Índice](../index.md)
