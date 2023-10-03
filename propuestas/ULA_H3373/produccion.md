# #ULA #H3373 Producción de kits 

## Contexto
La pantalla a usar tiene especificada la línea en la que está.

Hay una orden en estado Preparada asociada a la línea de la pantalla.

## Estructura
Nuevo formulario Composición de kits. Constará de los siguientes controles:
+ _Código de orden a producción_. Relacionado con _Órdenes de producción de kits_.
+ _Lote de Kit_ de producto actual. Autonumérico calculado como Orden de producción + número secuencial / letra secuencial.
+ _Cantidad_ del lote de kit de producto actual. Calculada como la mayor cantidad posible a producir dadas las cantidades en cada cubeta de los componentes que van por lotes (un kit de producto no	 puede tener unidades compuestas con alguno de sus componentes proveniente de distintos kits, todas las unidades deben de componerse de los mismos lotes).
+ Tabla con los componentes a utilizar, sus lotes y sus cubetas. Para componentes en varias cubetas, solo se muestra la cubeta activa.
+ Botón de _Imprimir etiqueta_. Es necesario conocer el formato de la etiqueta a generar.

## Dinámica
+ Vamos a P_roducción - Principal - Montaje de kits quirúrgicos_.
    + Vemos la orden a preparar y su tabla de componentes.
    + Los componentes por cubeta aparecen en estado _Bloqueado_.
    + El botón _Imprimir etiqueta_ está inhabilitado.
+ Indicamos trabajador, fecha y turno.
+ Para artículos que no llevan lote, el usuario lee el código de barras del artículo y seguidamente el código de barras de la cubeta.
    + Si ambos son correctos, la cubeta se desbloquea
+ Para artículos por lotes, el usuario lee el código de barras del lote y seguidamente el código de barras de la cubeta.
    + Si ambos son correctos, la cubeta se desbloquea
+ Cuando todos los componentes están desbloqueados, el botón Imprimir etiqueta se habilita.
+ Pulsamos Imprimir etiqueta.
    + Se imprime la etiqueta
    + Se genera un kit de producto asociado al lote con un código = lote + número secuencial.
    + Se decrementan los contadores
+ Repetimos la operación hasta que el contador de kits pendientes llega a 0
    + Si se ha completado la orden, esta pasa a Finalizada.
    + Si no se ha completado la orden, la/s siguiente/s cubeta/s quedan bloqueadas, el usuario debe desbloquearlas y continuar generando un nuevo lote.

## Notas de desarrollo
No hay notas de desarrollo

