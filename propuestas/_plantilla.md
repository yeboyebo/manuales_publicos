# #H____ Descripción del proyecto

Los objetivos de este proyecto son:
+ 

## Propuesta realizada a petición de:


## Estructura

### Pantalla / Zona 1
Añadiremos a la pantalla los siguientes controles:
+ Campo. Descripción.

## Precondiciones

## Dinámica

### Hacer X

Para hacer x:
+ Vamos a ...

## Notas de desarrollo
No hay notas de desarrollo

### Cursos
Estados:
+ Curso sin campaña
+ Curso con campaña

Lectura:
+ Cursos (eventos tipo Curso), por paginación y filtro
+ Curso (cabecera)
+ Materiales (líneas de curso)
+ Contactos de curso

Casos de uso:
+ _Cargar contactos_. Params:
    + idCurso
    + excel de contactos mismo formato que ERP
+ _Añadir contacto_. Params: idCurso, email
+ _Quitar contacto_. Params: idCurso, email
+ crearCampaña. Estados: Curso sin campaña. Params: idCurso

UI:
+ Maestro
    + Título: Cursos
    + Filtro:
        + Nombre de curso
        + Estado. *Todos, Abierto, Cerrado
    + Lista de tarjetas:
        + Icono: Circulo. Estado (icono verde / rojo)
        + NO. Nombre de curso
        + NE. Fecha
+ Detalle
    + Título. Nombre de curso
    + Cabecera:
        + Línea
            + Nombre de curso
        + Línea
            + Estado
            + Fecha
        + Línea
            + Control _Campaña de Curso_. Modos:
                + _Campaña no creada_. Botón texto. _Crear campaña_. Icono _campaign_ > Diálogo _Crear campaña_ > Caso de uso _Crear campaña_ > Cambio a modo Campaña creada_
                + _Campaña creada_. Enlace _Ir a campaña asociada_. Icono _campaign_.
    + Tab
        + Contactos
            + Barra botones
                + Botón de texto _Cargar contactos_. Icono _upload_ > Diálogo _Cargar contactos_ > Caso de uso _Cargar contactos_
                    + Éxito: Refresco de Lista de tarjetas de contactos
                    + Error: Diálogo _Errores de carga_
                + Botón de texto _Añadir contacto_. Icono _add_ > Diálogo _Añadir contacto_ > Caso de uso _Añadir contacto_ > Nuevo contacto Lista de tarjetas de contactos
                + Botón de texto _Quitar contacto_. Icono _remove_ > Diálogo _Quitar contacto_ > Caso de uso _Quitar contacto_ > Contacto fuera de Lista de tarjetas de contactos
            + Lista de tarjetas de contactos
                + Icono. _accountCircle_. Fijo.
                + NE. Nombre
                + SE. Email
                + NO. Teléfono
        + Materiales
            + Lista de tarjetas de materiales
                + Icono. _handyman_. Fijo
                + NO. Descripción
                + SO. Referencia
                + NE. Cantidad x Precio. Ej. 1 x 14,50€

+ Dialogo _Añadir contacto_
    + Email
    + Enlace a _Crear nuevo contacto_. Lleva a crear contacto y recupera el id del contacto creado.
    + Añadir / Cancelar

+ Diálogo _Quitar contacto_
    + Aviso: _Se va a quitar el contacto (email)_
    + Quitar / Cancelar

+ Diálogo _Crear campaña_
    + Aviso: _Se va a crear una campaña de marketing asociada al curso_
    + Crear / Cancelar

+ Diálogo _Cargar contactos_
    + Fichero. _Seleccione el fichero de contactos_
    + Enlace Formato del fichero. Abre diálogo FormatoFichero
    + Cargar / Cancelar

+ Diálogo _Errores de carga_
    + _El fichero no ha podido ser cargado. Se han producido los siguientes errores de carga:..._
        + Fila N: (error)
    + Aceptar

### Campañas
Estados:
+ Campaña de curso de formación (hay un evento de tipo Curso asociado)
+ Otros estados

Casos de uso:
+ generarTratosCampañaCurso.
    + Estados: Campaña de curso de formación
    + Params: idCampaña
    + Regla de acceso: editarCampañasMarketing

## Tareas
+ H___ ...
(mismas que puntos de estructura)

## Manual
El manual constará de...
No es necesario manual

## Asistencia a puesta en marcha
No es necesaria.

## Presupuesto
+ H___ Análisis X€
+ H___ Desarrollo e instalación X€
+ H___ Documentación X€
