# Contratos de intervención y colaboraciones por intervenciones

El objetivo de este proyecto es poder crear contratos de intervención a través de contratos marco y comprobar las colaboraciones a la hora de insertarlas si tienen un contrato de intervención vigente.

## Estructura

### Contratos
* Añadiremos un nuevo botón al formulario maestro de *Contratos*:
    * **Crear contrato intervención**
* Crearemos nuevos campos en el formulario de edición (*Panel principal*):
    * **Ámbito (Marco, Intervención, Otros)**, valor por defecto *Otros*.
    * **F.Vencimiento**
* Crearemos nuevos campos en el formulario de edición (pestaña *Intervenciones / caches*):
    * **Cache Plató**
    * **Cache Skype**
    * **Nº intervenciones Plató**
    * **Nº intervenciones Skype**
    * **Periodicidad Plató**
    * **Periodicidad Skype**

### Colaboraciones
* Añadiremos un nuevo botón al formulario maestro de *Colaboraciones*:
    * **Crear contrato intervención**

### Etiquetas
Crearemos dos nuevas etiquetas **CACHE_PLATO** y **CACHE_SKYPE** para la combinación con las plantillas.

## Dinámica

### Crear un contrato de intervención a partir de un contrato marco
Cuando una productora necesite crear un contrato de intervención los pasos a seguir son:
* Vamos a *RRHH > Principal > Contratos* y seleccionamos un contrato marco activo.
* Pulsamos el botón *Crear contrato intervención*.
    * Se muestra un formulario que nos pide:
        * Fecha desde y hasta del contrato (por defecto la fecha hasta es igual a la fecha desde).
        * Tipo de contrato.
* Indicamos las fechas y el tipo de contrato y pulsamos *Aceptar*.
    * Se crea un contrato de *Ámbito* *Intervención*, con las fechas y el tipo indicados, con los siguientes datos obtenidos del contrato marco:
        * Empleado
        * Producción
        * Cachés, nº intervenciones, periodicidad, etc

### Creación de colaboraciones
* Vamos a *RRHH > Principal > Colaboraciones.
* Seleccionamos producción, mes y tipo de caché.
    * Se muestra el listado de empleados ligados a la producción para ese mes.
* Para marcar / desmarcar una colaboración hacemos doble clic en la celda del empleado y día correspondiente.
    * Si no existe un contrato de intervención para el día, empleado y producción indicados, la celda queda marcada con una **P**.

### Creación de contratos desde colaboraciones
* Si seleccionamos una celda marcada con **P**, podemos pulsar el botón *Crear contrato intervención*.
    * Se mostrará el mismo formulario que se indica en *Crear un contrato de intervención a partir de un contrato marco*, con las fecha ya informadas e iguales a la fecha de la casilla seleccionada. A partir de este punto el funcionamiento es el mismo que en el apartado indicado.





