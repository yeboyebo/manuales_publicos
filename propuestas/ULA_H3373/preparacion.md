# #ULA #H3373 Preparación de kits 

## Contexto
La pantalla a usar tiene especificada la línea en la que está.

Hay una orden en estado Preparada asociada a la línea de la pantalla.

## Estructura
Nuevo formulario _Preparación de kits_. Constará de los siguientes controles:
+ _Código de orden de producción_. Relacionado con _Órdenes de producción de kits_.
+ _Tabla con los componentes a incluir_. Cada elemento de la tabla contiene los siguientes datos:
    + _Referencia_ y _descripción_ del componente.
    + _Lote a usar_.
    + _Cantidad a usar_.
    + _Cubeta_ asociada (por defecto, vacío)
+ _Estado de la preparación_. Su valor será _Pendiente_ hasta que todos los componentes tengan una cubeta asociada. Entonces pasará a estado _Lista_.

## Dinámica
Vamos a _Producción - Principal - Preparación de kits quirúrgicos_.
+ Indicamos la orden a preparar.
    + La orden queda ligada a la línea de preparación.
    + Se muestra la tabla de componentes.
    + El estado es _Pendiente_, y la orden pasa a estado _En preparación_.
+ Para artículos que no llevan lote, el usuario lee el código de barras del artículo y seguidamente el código de barras de la cubeta.
    + Si ambos son correctos, el componente queda ligado a la cubeta.
+ Para artículos por lotes, el usuario lee el código de barras del lote y seguidamente el código de barras de la cubeta.
    + Si ambos son correctos, el componente / lote queda ligado a la cubeta.
+ Cuando todos los componentes tienen cubetas asociadas, el estado de la preparación pasa a ser Lista y la orden pasa a estado _Preparada_.

## Notas de desarrollo
No hay notas de desarrollo

