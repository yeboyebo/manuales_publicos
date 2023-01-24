# Campañas

---

## Estructura

### Nueva tabla Campañas:

- **Código**
- **Fecha de alta**
- **Nombre**
- **Enviar a todos los contactos (Sí / No)**
- **Fecha de lanzamiento** de campaña
- **Tipo**:
  - _Repetición_
  - _Captación_
  - _Medición_
- **Fecha desde de medición de impacto**
- **Fecha hasta de medición de impacto**
- **Subtipo captación**(solo para campañas de tipo _Captación_). Posibles valores:
  - De leads
  - De venta
- **Umbral** (solo para campañas de tipo _Captación_)
- **Número de días desde la última compra** (en días) (solo para campañas de tipo _Repetición_)
- **Estado**. Posibles valores:
  - _En diseño_ (valor por defecto)
  - _En seguimiento_
  - _Cerrada_

### Gráfico de seguimiento

Consiste en un gráfico en cascada que compara las ventas de los artículos considerados, en el periodo de medición de impacto y en el mismo periodo de años anteriores. Además diferenciarán ventas totales y ventas por tienda online de (serie W).

### Subtabla de Artículos por campaña

Permite la asociación manual de artículos a una campaña

Los tres tipos de campaña tienen asociada una _Lista de artículos_ cuyas ventas vamos a promocionar y analizar.

### Acceso

Los grupos con acceso a campañas serán _Marketing_ y _Dirección_.

## Dinámica

### Crear una campaña de tipo _Repetición_

1. Creamos una nueva campaña indicando _Nombre_ y _Tipo_.
1. Indicamos el _Número de días desde la última compra_.
1. Indicamos los artículos a incluir en la campaña
1. Pulsamos el botón _Calcular_.

   Se mostrará el total de clientes (contactos) que hayan comprado al menos uno de los artículos de la lista en una fecha posterior a la fecha calculada como:

   _Fecha de alta_ - _Número de días desde la última compra_.

1. Revisamos, si es necesario, los valores anteriores para obtener un número de contactos apropiado.
1. Pulsamos el botón _Lanzar campaña_
   - La campaña pasa a estado _En seguimiento_
   - La campaña se sincroniza con Active Campaign
   - Se muestra el _Gráfico de seguimiento_.
1. Una vez finalizado el período de medición, podemos pasar la campaña a estado _Cerrada_.

### Crear una campaña de tipo _Captación_

El funcionamiento es igual al de la campaña de _Repetición_, con las siguientes salvedades:

- No es necesario especificar _Número de días desde la última compra_.

- Es necesario especificar el _Umbral de recomendación_ a usar.

- La lista de clientes (contactos) se conforma con los clientes a los que se asigna una recomendación superior al umbral en al menos uno de los artículos de la lista.

### Crear una campaña de tipo _Seguimiento_

El funcionamiento es igual al de la campaña de _Repetición_, con las siguientes salvedades:

- No se muestra el botón _Calcular_, ni se le asocian contactos.

- Al pulsar el botón _Lanzar campaña_, no hay sincronización con Active Campaign, solo cambio de estado a _En seguimiento_

## Notas de desarrollo

Productos padre??

Productos asimilables, tenerlos en cuenta para nuestras campañas de captación (usan la referencia asimilada si no han vendido más unidades que ella (refproductoasimilable)

¿Crear una tabla de selección con idproducto, refpadre, referencia, asimilable?

API de Active campaign. Se deberá definir la importación inicial de contactos desde Smartsales a Active y viceversa, así como la dinámica de creación de contactos en uno y otro canal.

[Volver al Índice](../index.md)
