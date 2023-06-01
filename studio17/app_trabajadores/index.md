# App Trabajadores

## Crear un nuevo parte

* Pulsamos el botón + del listado de partes
  * Se abre el formulario de alta de parte con la fecha actual como valor de fecha por defecto.
* Modificamos la fecha si es necesario y pulsamos *Crear parte*
  * Si ya hay un parte para el trabajador conectado y la fecha, obtenemos el error _Ya hay un parte para el trabajador y fecha indicados_.
  * Si no hay un parte ya creado, se crea un parte y aparece en el listado de partes.

## Asignar horas a un parte
* Seleccionamos el parte de la lista
  * El parte se visualiza en la parte derecha de la pantalla. Podemos ver:
    * Nombre del trabajador
    * Fecha
    * Horas totales

* Pulsamos el botón +
  * Se muestra el formulario de alta de ĺínea de parte
* Indicamos los siguientes valores:
  * Referencia de manor de obra. Se muestran todos los artículos de la familia de mano de obra
  * Proyecto. Se muestran todos los proyectos en estado Abierto
  * Horas. Valor entero
  * Minutos: Valor entero, máximo 59
* Pulsamos _Guardar_.
  * La línea se guarda y aparece en el listado de líneas

## Listado de líneas
Cada elemento línea consta de la siguiente información:
* Avatar (círculo verde)
* Título izquierdo: Descripción de la referencia
* Subtítulo izquierdo: Código y nombre del proyecto
* Título derecha: Horas y minutos en formato hh:mm

## Editar una línea
* Selecccionamos la línea a editar y pulsamos sobre ella
  * Se despliega el formulario de edición de línea
* Editamos y guardamos los datos correspondientes
* Pulsamos _Cerrar_ para colapsar la línea

## Borrar una línea
* Pulsamos _Borrar_
  * Se abre un dialogo de confirmación.

## Borrar un parte
* Pulsamos botón de icono _papelera_ en la cebecera
  * Se abre un dialogo de confirmación.

