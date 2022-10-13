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
    * Repetición
    * Captación
    * Medición
  * **Fecha desde de medición de impacto**
  * **Fecha hasta de medición de impacto**
  * **Subtipo captación**(solo para campañas de tipo *Captación*). Posibles valores:
    * De leads
    * De venta
  * **Umbral** (solo para campañas de tipo *Captación*)
  * **Número de días desde la última compra** (en días) (solo para campañas de tipo *Repetición*)
  * **Estado**. Posibles valores:
    * En diseño
    * En seguimiento
    * Cerrada

## Subtabla de Artículos por campaña
Permite la asociación manual de artículos a una campaña

Los tres tipos de campaña tienen asociada una *Lista de artículos* cuyas ventas vamos a promocionar y analizar.

### Acceso
Los grupos con acceso a campañas serán *Marketing* y *Dirección*.

## Dinámica

### Crear una campaña de tipo *Repertición*
1. Creamos una nueva campaña indicando *Nombre* y *Tipo*.
1. Indicamos el *Número de días desde la última compra*.
1. Indicamos los artículos a incluir en la campaña
1. Pulsamos el botón *Calcular*.
  
    Se mostrará el total de clientes (contactos) que hayan comprado al menos uno de los artículos de la lista en una fecha posterior a la *Fecha de alta* de la campaña menos el *Número de días desde la última compra*.




    * Si la campaña es de *Repetición*, indicamos el número de días desde la última compra.

    * Se la campaña es de **Captación*, indicamos el *Subtipo* y el *Umbral*

1. Indicamos los artículos a incluir en la campaña

1. Pulsamos el botón *Calcular*.
  Se mostrará el total de contactos a asociados a la campaña

En recomendaciones, limitar por umbral de recomendación.

Productos padre??

Productos asimilables, tenerlos en cuenta para nuestras campañas de captación (usan la referencia asimilada si no han vendido más unidades que ella (refproductoasimilable)

Mediciones: Consistirá en gráficos en cascada que compararán las ventas de los artículos considerados, en el periodo de medición de impacto y en el mismo periodo de años anteriores. Además diferenciarán ventas totales y ventas por tienda online de la serie W.

API de Active campaign. Se deberá definir la importación inicial de contactos desde Smartsales a Active y viceversa, así como la dinámica de creación de contactos en uno y otro canal.
