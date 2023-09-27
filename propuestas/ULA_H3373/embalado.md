# #ULA #H3373 Embalado

## Embalado en cajas. Estructura 
Nuevo formulario Cajas de kits. Constará de los siguientes controles:
+ Campo _Caja_, indica el tipo y el código de la caja activa.
+ Campo _Unidades usadas_ / _Unidades por caja_
+ Botón de _Nueva caja_.
+ Lista de _Lotes asociados_ a la caja.
+ Campo _Código de kit_.

## Embalado en cajas. Dinámica
+ Vamos a _Producción - Principal - Embalado de kits en cajas_.
    + Vemos la orden a preparar, el tipo de caja que usa y su capacidad (unidades por caja).
    + El botón _Nueva caja_ está habilitado.
+ Pulsamos el botón _Nueva caja_.
    + Se imprime una pegatina con el código de caja.
    + Se muestra el código de caja.
    + Se inicializa el contador de kits y se limpia la tabla.
    + El botón _Nueva caja_ está inhabilitado.
+ Leemos el código de un kit a meter en la caja
    + Se asocia el kit a la caja.
    + Se muestra el kit en la tabla y se decrementa el contador.
+ Cuando llenamos la caja (contador a 0), aparece un mensaje de _Validar_ caja, pidiéndonos que volvamos a leer el código de la caja.
    + Si el código es correcto, el botón Nueva caja se habilita
+ Si hay más kits que embalar, pulsamos el botón Nueva caja y continuamos.

## Embalado en palés. Contexto
La pantalla a usar tiene especificada la línea en la que está.

Hay una orden en estado Preparada asociada a la línea de la pantalla.

## Embalado en palés. Estructura 
Nuevo formulario Palets de kits. Constará de los siguientes controles:
+ Campo _Palet_, indica el tipo y el código de la caja activa.
+ Campo _Cajas usadas_ / _Cajas por palet_.
+ Botón de _Nuevo palet_.
+ Lista de cajas asociadas al palet.
+ Campo _Código de caja_.

## Embalado en palés. Dinámica
+ Vamos a _Producción - Principal - Embalado de cajas en palets_.
    + Vemos la orden a preparar, el tipo de caja que usa y su cantidad en palet (cajas por palet)
    + El botón _Nuevo palet_ está habilitado.
+ Pulsamos el botón Nuevo palet.
    + Se imprime una pegatina con el código de palet.
    + Se muestra el código de palet.
    + Se inicializa el contador de cajas y se limpia la tabla
    + El botón Nuevo palet está inhabilitado.
+ Leemos el código de una caja a meter en el palet.
    + Se asocia la caja al palet.
    + Se muestra la caja en la tabla y se decrementa el contador.
+ Cuando llenamos el palet (contador a 0), aparece un mensaje de Validar palet, pidiéndonos que volvamos a leer el código del palet.
    + Si el código es correcto, el botón Nuevo palet se habilita
+ Si hay más kits que embalar, pulsamos el botón Nuevo palet y continuamos.

## Notas de desarrollo
No hay notas de desarrollo

