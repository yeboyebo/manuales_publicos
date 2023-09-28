# #ULA #H3373 Producción de kits para operaciones quirúrgicas

Los objetivos de este proyecto son:
+ Modificar el ERP de forma que sea posible dar soporte a las nuevas funcionalidades de fabricación de kits.

## Estructura

### Tablas auxiliares
+ Nueva tabla de Cubetas.
+ Nueva tabla de Tipos de caja.
+ Nueva tabla de Cajas.
+ Nueva tabla de Palets.
+ Nueva tabla Líneas de producción.
+ Nueva tabla de Kits quirúrgicos:
+ Referencia de producto
+ Código de lote
+ Código de kit 
+ Código de caja

### Configuración de artículos tipo Kit
El formulario de artículos contendrá los siguientes nuevos campos y opciones:
+ _Kit quirúrgico_ (Sí/No, valor por defecto No).
+ _Tipo de caja_. Relacionado con _Tipos de caja_.
+ _Cantidad por caja_
+ Tabla de composición (se usará la actual tabla de escandallo)

### Órdenes de producción
Nuevo formulario Órdenes de producción de Kits. Constará de los siguientes controles:
+ _Código de orden_ (autonumérico).
+ _Fecha_.
+ _Tipo de Kit_. Relacionado con la tabla de artículos filtrada por los que son kits quirúrgicos.
+ _Cantidad a fabricar_.
+ _Estado_ (_Pendiente_ / _En curso_ / _Finalizada_).
+ Botón _Lanzar orden_.

### Reservas de producción
Nueva tabla _Reservas de composición de kits_. Campos asociados:
+ _Orden de producción_. Relacionado con _Órdenes de producción_.
+ _Referencia del compuesto_. Relacionado con _Artículos_.
+ _Código de lote del compuesto_. Relacionado con _Lotes_.
+ _Cantidad_.
+ _Cubeta_. Relacionado con _Cubetas_.

## Dinámica
Los pasos para generar una orden de producción son los siguientes:
+ Vamos a _Producción - Principal - Órdenes de producción de kits quirúrgicos_.
+ Indicamos el _Tipo de kit_ y la _Cantidad a fabricar_.
+ Guardamos el registro, que queda en estado _Pendiente_.
+ Seleccionamos el registro y pulsamos _Lanzar orden_.
    + Se reserva de los lotes en stock las cantidades de componentes correspondientes, creándose los correspondientes registros en la tabla _Reservas de composición de kits_.
    + Si hay falta de lotes se avisa al usuario y la operación se cancela.
    + La orden pasa a estado En curso.
    + (opcional) Se imprime un informe de orden (formato a definir) para pasarlo a la planta de fabricación que describa la composición y lotes a usar.


## Notas de desarrollo
+ __Un kit de producto no	puede tener unidades compuestas con alguno de sus componentes proveniente de distintos kits, todas las unidades deben de componerse de los mismos lotes__.

