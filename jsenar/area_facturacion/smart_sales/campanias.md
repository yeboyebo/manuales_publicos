# Campañas
----------------------

## Estructura

### Nueva tabla Campañas:

  * **Código**
  * **Fecha de alta**
  * **Nombre**
  * **Enviar a todos los contactos (Sí / No)**
  * **Fecha de lanzamiento** de campaña
  * **Tipo**:
    * *Repetición*
    * *Captación*
    * *Medición*
  * **Fecha desde de medición de impacto**
  * **Fecha hasta de medición de impacto**
  * **Subtipo captación**(solo para campañas de tipo *Captación*). Posibles valores:
    * De leads
    * De venta
  * **Umbral** (solo para campañas de tipo *Captación*)
  * **Número de días desde la última compra** (en días) (solo para campañas de tipo *Repetición*)
  * **Estado**. Posibles valores:
    * *En diseño* (valor por defecto)
    * *En seguimiento*
    * *Cerrada*

### Gráfico de seguimiento
Consiste en un gráfico en cascada que compara las ventas de los artículos considerados, en el periodo de medición de impacto y en el mismo periodo de años anteriores. Además diferenciarán ventas totales y ventas por tienda online de (serie W).

## Subtabla de Artículos por campaña
Permite la asociación manual de artículos a una campaña

Los tres tipos de campaña tienen asociada una *Lista de artículos* cuyas ventas vamos a promocionar y analizar.

### Acceso
Los grupos con acceso a campañas serán *Marketing* y *Dirección*.

## Dinámica

### Crear una campaña de tipo *Repetición*
1. Creamos una nueva campaña indicando *Nombre* y *Tipo*.
1. Indicamos el *Número de días desde la última compra*.
1. Indicamos los artículos a incluir en la campaña
1. Pulsamos el botón *Calcular*.
  
    Se mostrará el total de clientes (contactos) que hayan comprado al menos uno de los artículos de la lista en una fecha posterior a la fecha calculada como:
    
    *Fecha de alta* - *Número de días desde la última compra*.

1. Revisamos, si es necesario, los valores anteriores para obtener un número de contactos apropiado.
1. Pulsamos el botón *Lanzar campaña*
    * La campaña pasa a estado *En seguimiento*
    * La campaña se sincroniza con Active Campaign
    * Se muestra el *Gráfico de seguimiento*.
2. Una vez finalizado el período de medición, podemos pasar la campaña a estado *Cerrada*.

### Crear una campaña de tipo *Captación*
El funcionamiento es igual al de la campaña de *Repetición*, con las siguientes salvedades:
* No es necesario especificar *Número de días desde la última compra*.

* Es necesario especificar el *Umbral de recomendación* a usar.

* La lista de clientes (contactos) se conforma con los clientes a los que se asigna una recomendación superior al umbral en al menos uno de los artículos de la lista.

### Crear una campaña de tipo *Seguimiento*
El funcionamiento es igual al de la campaña de *Repetición*, con las siguientes salvedades:

* No se muestra el botón *Calcular*, ni se le asocian contactos.

* Al pulsar el botón *Lanzar campaña*, no hay sincronización con Active Campaign, solo cambio de estado a *En seguimiento*

## Notas de desarrollo

Productos padre??

Productos asimilables, tenerlos en cuenta para nuestras campañas de captación (usan la referencia asimilada si no han vendido más unidades que ella (refproductoasimilable)

¿Crear una tabla de selección con idproducto, refpadre, referencia, asimilable?

API de Active campaign. Se deberá definir la importación inicial de contactos desde Smartsales a Active y viceversa, así como la dinámica de creación de contactos en uno y otro canal.
