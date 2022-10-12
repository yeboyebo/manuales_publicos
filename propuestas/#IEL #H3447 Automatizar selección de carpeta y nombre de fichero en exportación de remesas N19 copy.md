

# #IEL #H3447 Automatizar selección de carpeta y nombre de fichero en exportación de remesas N19

El objetivo de este proyecto es facilitar la localización de la carpeta y automatizar la construcción del nombre del fichero de remesa para la norma 19 (norma AEB anterior a SEPA)

## Estructura

### Ventana de exportación N19
Crearemos dos nuevos campos:
* **Carpeta**: Carpeta donde guardar el fichero. Campo con selector de carpeta. Recuerda cuál fue la última carpeta usada para esta norma en el ordenador de la instalación.
* **Nombre fichero**: Nombre del fichero (sin extensión) que se usará. Se calculará automáticamente como *AAAA-mm-dd_numero_remesa*.

    Ejemplo: *2022-11-31_150*

Modificaremos el actual campo *Fichero* para:
* Mostrar la concatenación de los campos *Carpeta* y *Nombre fichero*.
* Eliminar el botón de selección de fichero
* Hacer el campo no editable

## Dinámica

### Generar una remesa norma 19 AEB

* Vamos a *Facturación - Tesorería - Remesas a clientes*, seleccionamos la remesa y pulsamos  remesas, *Volcar remesa en disco en norma 19*.
* Se abre el formulario de *Volcado a disco de remesas*
    * Si ya habíamos guardado una remesa anteriormente en nuestro puesto, el campo *Carpeta* recuerda la carpeta de grabación*.
    * El campo *Nombre fichero* contiene el nombre construido según el formato descrito en el apartado *Estructura*.
* Modificamos, si es necesario, la carpeta o el nombre del fichero, y pulsamos *Aceptar*.
    * El fichero de remesa se genera en la ruta indicada con el nombre indicado.


