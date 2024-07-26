# Cambios masivos de escandallo

En **Facturción->Almacén** tenemos una nueva acción **Cambios Masivos de Escandallo**. Este formulario se divide en las siguientes partes:

+ Cabecera. En esta parte encontramos datos referentes al usuario y fecha que realizará el cambio así como el Modo de cambio. Este modo tiene 3 posibles valores: Añadir, Modificar y Eliminar. (Más adelante se explica cada uno de ellos)
    
+ Búsqueda. En este apartado estbleceremos algunos filtros para realizar una búsqueda de los componentes sobre los que deseamos realizar el cambio masivo.

Los campos de búsqueda serán:

    - Referencia producto desde.
    - Referencia producto hasta.
    - Referencia componente. Habilitados en modos Modificar / Eliminar.
Una vez establecidos estos valores, si pulsamos sobre el botón **Buscar**, en la tabla inferior se mostrará el resultado de la búsqueda

+ Datos. En esta última parte debemos establecer los datos que queremos cambiar: 

        - Nueva referencia de componente. Habilitado en modo Añadir / Modificar.
        - Cantidad.
        - Tarea de consumo. Relacionado con tipos de tareas y filtrado por el tipo de proceso del rango. Todas las referencias deben fabricarse con el mismo tipo de proceso.

Una vez establecidos los datos a cambiar pulsaremos el botón Lanzar para hacerlos efectivos. Dependiendo del modo que hayamos seleccionado se realizará una acción diferente.

`IMPORTANTE:` Todas las búsquedas y acciones se realizarán por componentes en los que sus campos de Talla compuesto, Color compuesto y Barcode componente tengan valor nulo. No podrá operar con componentes de talla y color.

## Crear nuevos componentes
+ Creamos un registro de **Cambio Masivo de Escandallo** y elegimos el modo _Añadir_.

+ Indicamos en la zona de búsqueda el rango de referencias de productos afectados
+ En el apartado datos, la referencia del nuevo componente.

+ Pulsamos **Buscar** para ver los artículos afectados. La lista muestra todos los productos del rango y sus columnas de componente estarán informadas solo si el producto ya tiene el componente a crear.

+ En el apartado Datos, informamos la cantidad del componente a crear (valor por defecto 1).

+ Pulsamos el botón **Lanzar**.
    + Los componentes se crean. Si algún producto ya tenía un componente con la referencia de compuesto indicada, no se crea uno nuevo, sino que se actualiza el ya existente.
    + Se refresca la lista de búsqueda, buscando por el nuevo componente.
    + Se recalculan los costes de los artículos afectados

## Modificar componentes
+ Creamos un registro de **Cambio Masivo de Escandallo** y elegimos el modo _Modificar_.
+ Indicamos en la zona de búsqueda:
    + Rango de referencias de productos afectados.
    + Referencia del componente a modificar. Al hacer esto se copiará automáticamente la referencia del componente al campo Nuevo Componente de la zona de Datos.

+ Pulsamos **Buscar** para ver los artículos afectados. La lista mostrará todos los productos del rango.

+ En el apartado Datos, informamos:
    + Nueva referencia del componente. Por defecto será la misma o podremos establecer otra. Si dejamos la misma referencia será para modificar solamente la cantidad
    + Cantidad. Si la cantidad no está informada (valor vacío), se entenderá que se debe respetar la cantidad actual en cada componente. 

+ Pulsamos el botón **Lanzar**.
    + Los componentes se modifican en referencia y cantidad (si alguna de ellas tiene valor, si no, el campo se mantiene). Si algún artículo no tiene asociado dicho componente, el artículo no se modifica.
    + Se refresca la lista de búsqueda.
    + Se recalculan los costes de los artículos afectados

## Eliminar componentes
+ Creamos un registro de **Cambio Masivo de Escandallo** y elegimos el modo _Eliminar_.
    + Los controles del apartado datos se vacían e inhabilitan.

+ Indicamos en la zona de búsqueda:
    + Rango de referencias de productos afectados.
    + Referencia del componente a eliminar
+ Pulsamos **Buscar** para ver los artículos afectados.
+ Pulsamos el botón **Lanzar**.
    + Los componentes se eliminan.
    + Se refresca la lista de búsqueda, que debe quedar vacío en sus columnas de componente.
    + Se recalculan los costes de los artículos afectados

[Volver al Índice](../index.md)