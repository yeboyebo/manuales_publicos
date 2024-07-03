En ese caso, necesitaríamos un esbozo de lo que sería el sistema: funcionalidades, stack, arquitectura aproximada.

# Funcionalidades estándar

## Funcionalidades de almacén
Las funcionalidades de almacén comprenden:
+ La posibilidad de definir y trazar la entrada, salida y localización de prendas con tallas y colores.
+ Crear escandallos (composiciones) de productos con tallas y colores (compuestos a su vez por componentes que pueden tener talla y color).

Aunque en el textil se suele usar una referencia para cada _modelo_ y cada _modelo_ representa un producto con todas sus tallas (cada _color_ es un _modelo_ diferente), asumiremos el caso general en el que un producto (referencia) puede ser la combinación de T tallas x C colores.

Llamaremos _Barcode_ a cada combinación referencia x talla x color. Un _Barcode_ se corresponde en el dominio de almacén a un _SKU_ (Stock Keeping Unit) o mínima unidad trazable en almacén.

Llamaremos _Partida_ a un grupo de cantidades de combinaciones talla / color con sus correspondientes cantidades. Una partida puede representarse como una estructura JSON de la siguiente forma:
```js
P = {
    { talla:"36", color:"blanco", cantidad: 10 },
    { talla:"38", color:"blanco", cantidad: 14 },
    { talla:"40", color:"blanco", cantidad: 12 },
    { talla:"36", color:"negro", cantidad: 10 },
    { talla:"38", color:"negro", cantidad: 14 },
    { talla:"40", color:"negro", cantidad: 12 },
}
```
Para simplificar, y usando la terminología y convenciones asociadas al sector del calzado, definiremos partidas como combinaciones de un único color, donde la estructura queda limitada a un diccionario de tallas y cantidades asociadas:
```js
P = {
    "36": 10,
    "38": 12,
    "40": 16,
    "42": 14,
    "44": 10,
}
```

### Escandallo adaptado a textil (tallas y colores)
En el escandallo adaptado a textil dispondremos de una tabla de composición con las siguientes columnas:
+ Compuesto: Referencia del producto compuesto
+ Componente: Referencia del componente
+ Talla compuesto: Opcional. Indica que el componente solo aplica cuando el compuesto es de la talla indicada.
+ Color compuesto: Opcional. Indica que el componente solo aplica cuando el compuesto es del color indicado.
+ Talla componente. Necesario para componentes por tallas
+ Color componente. Necesario para componentes por color

Cuando los campos _Talla compuesto_ o _Color compuesto_ no se informan, y el compuesto tiene tallas y colores, se interpreta que el mismo componente se aplica a todas las tallas y/o colores.

### Aprovisionamiento adaptado a textil
Las funcionalidades asociadas al aprovisionamiento comprenden:
+ Emisión de pedidos de componentes en base a stocks reservados de productos a fabricar, stock físico actual y stock pendiente de recibir. Las reservas se producen por pedidos de cliente registrados.
+ Agrupación de pedidos en _partidas_.
+ Entrada mediante códigos de barras de componentes, registro de albaranes de entrada y alta en stock de almacén.

### Venta adaptada a textil
+ Agrupación de pedidos de venta en _partidas_. Representación de estas partidas en formato de tabla en los documentos emitidos de forma digital (pedidos, albaranes, facturas).
+ Gestión de reservas de almacén mediante pedidos.
+ Descuento de stock en almacén al servir (albaranar) pedidos.

## Funcionalidades de producción
Las funcionalidades de producción son las que se necesitarán para registrar los productos solicitados por los clientes a partir de los componentes definidos en el escandallo.

### Uso de partidas como unidad de producción
Dado que la cantidad óptima de productos a producir no tiene por qué estar relacionada con la cantidad pedida por el cliente, se podrá definir una _estrategia de creación de partidas de producción_. Una partida de venta se dividirá así en N partidas de producción:
```
Pv = Pp1 + Pp2 + Pp3
```
Una estrategia común en el sector del calzado es dividir las partidas por tallas, para así tener partidas de producción homogéneas. Ejemplo:
```js
Pv = {
    "36": 100,
    "38": 120,
    "40": 160,
    "42": 140,
    "44": 80,
}
/// Se divide en cinco partidas:
Pp1 = {
    "36": 100
}
Pp2 = {
    "38": 120
}
/// etc.
```
Otra estrategia puede ser simplemente limitar el total de la partida a un determinado número:
```js
Pv = {
    "36": 100,
    "38": 120,
    "40": 160,
    "42": 140,
    "44": 80,
}
/// Se divide en partidas de máximo 300 pares:
Pp1 = {
    "36": 100,
    "38": 120,
    "40": 80,
}
Pp2 = {
    "40": 80,
    "42": 140,
    "44": 80,
}
/// etc.
```

### Asociación de procesos configurables a cada modelo
Definiremos las siguientes entidades de catálogo de procesos:
+ _Tipos de tareas de producción_ (corte, guarnecido, montado, laminado, etc.)
+ _Tipos de proceso de producción_.
+ _Puntos de control_ por proceso de producción, asociados a un tipo de proceso y a un tipo de tarea.
+ _Secuencias_, que indican la relación temporal entre tareas de control.

Cada tipo de proceso de producción se define como un grafo, donde los elementos del grafo son _Puntos de control_ relacionados entre sí por _Secuencias_.

Definimos las siguientes entidades de dinámica de procesos:
+ _Procesos_: Son instancias de un determinado Tipo de proceso, con un identificador único y asociadas a:
    + Un modelo o producto semielaborado
    + Una partida de producción (para el caso de productos de calzado)
+ _Tareas_: Son instancias de un determinado _Punto de control_, con un identificador único y asociados a:
    + Un _Proceso_.
    + Un _Punto de control_.
	Los posibles estados de una _Tarea_ son:

    + _OFF_: La tarea no puede comenzar porque su proceso asociado no se ha iniciado o porque sus tareas predecesoras no han terminado.
    + _PTE_: La tarea puede comenzar.
    + _EN CURSO_: La tarea ha comenzado.
    + _TERMINADA_: La tarea ha terminado.
Una vez creado un proceso, sus tareas iniciales (las que no tienen secuencias de llegada asociadas), son activadas (pasan a estado PTE).

### Catálogo, escandallo y procesos de producción parciales
Cada modelo debe incluir un escandallo sensible a tallas (distintos consumos por talla opcionales) como se ha indicado en el apartado de funcionalidades de almacén.

Cada modelo tendrá un proceso de producción asociado.

La asociación se podrá realizar de forma individualizada o siguiendo reglas globales (modelos de una misma familia tienen un mismo proceso de producción, etc.).

Cuando se produce una incidencia y se resta a la partida de producción una partida de atraso, se asociará a la nueva partida de atraso un proceso de producción, que puede ser parcial, con el que se realizará su seguimiento.

### Generación de órdenes de producción
El sistema permitirá generar órdenes de producción asociadas a pedidos de clientes. Cada partida de pedido de cliente genera N partidas de producción siguiendo _alguna de las estrategias_ antes definidas. Una orden de producción se asocia a una partida de producción.

Una vez activado el proceso de producción, sus tareas iniciales pasarán a estado _PTE_, apareciendo en las colas de cada punto de control asociado.

La cola de cada punto de control podrá ser modificada de forma manual, de manera que pueda darse prioridad a unas partidas respecto de otras.

__Adquisición__. Los trabajadores pueden adquirir la siguiente tarea de la cola, pasando su estado a _En Curso_. La adquisición de la tarea indica:
+ Trabajador que la adquiere
+ Fecha y hora de inicio de la tarea
+ Partida / orden de producción asociada

Una vez adquirida la tarea, el sistema se actualiza y muestra al trabajador información asociada a la misma (materiales a usar, procedimiento, datos a tener en cuenta para ese modelo en concreto, etc.)

__Proceso__. Durante el proceso de la tarea no es necesario interactuar con el sistema, a menos que ocurra alguna incidencia.
El árbol de acción / decisión de una incidencia será:
+ Alta de incidencia > Indicación del tipo (selección de opción en base al punto de control)
+ ¿Consumos asociados? (respuesta sí >): Indicación de consumos extra > Cantidades de material o tiempos no previstos debidos a la incidencia.
+ ¿Genera atraso? (respuesta sí >): Indicación de las prendas (tallas y cantidades) afectados y asociación de tipo de proceso (total o parcial) asociado a la partida de atraso. Ver apartado de _Gestión de incidencias: Atrasos_.

__Completado__. Los trabajadores pueden completar las tareas en estado _En curso_, pasándolas a _Terminada_. El completado indica:
+ Fecha y hora de fin de la tarea
+ Partida de producción asociada

Cuando una tarea pasa a _Terminada_ su siguiente o siguientes tareas pasan a estado _PTE_.

Opción de especificar consumos: Las tareas marcadas con Especificar consumos en alguno de sus consumos asociados, exigirán al usuario que complete la tarea que indique la cantidad real consumida del/los productos así marcados. Aunque el programa deberá descontar de forma automática los materiales usados en base al escandallo, es útil a veces indicar las cantidades reales consumidas, o al menos confirmar la previstas por el programa.

Modo rápido: Las tareas marcadas con Modo rápido en su ficha de proceso, pasarán directamente de _Pendiente_ a _Terminada_, por lo que no se registra el tiempo empleado en completarlas.

__Tareas externas__. Las tareas externas podrán ser asociadas a un trabajador virtual, que estará asociado a un proveedor de facturación. Para las tareas externas se integrará las fases de adquisición y completado con la emisión de pedidos a proveedor y albaranes de entrada respectivamente.

Para el caso de unidades no recibidas, se recurrirá a la división de la partida generando un atraso y asignándole el proceso de producción parcial correspondiente. Ver apartado de _Gestión de incidencias: Atrasos_.

__Fin y consolidación__ de partidas de pedido.

A medida que los proceso de producción de cada partida de producción van terminando, las partidas de pedido van pasando a estado _Completado_.

### Gestión de incidencias: Atrasos
Cuando una prenda se rompe, es necesario volverla a fabricar, o fabricar al menos la pieza dañada, para luego terminar su fabricación y completar la partida de producción inicial. Para ello, se proveerá de una funcionalidad de división de partidas, en la que una partida de producción original se divide en dos, la partida principal y la partida de atraso.

La partida de atraso es asociada de forma manual al proceso de producción total o parcial que necesite para continuar su fabricación.

Las partidas de atraso pueden continuar hasta el fin de su proceso de producción o unirse en cualquier momento a su partida principal


## Estadística
Se generarán hipercubos de datos alimentados por el seguimiento de los procesos de producción que permitirán el análisis de la evolución de determinadas _Medidas_ filtradas o clasificadas por determinadas _Dimensiones_.

### Producción: tiempos y productividad

__Medidas__:
+ Tiempo bruto de fabricación. Tiempo desde que una tarea se puede iniciar hasta que se da por terminada (desde que una tarea pasa a PTE hasta que pasa a TERMINADA).
+ Tiempo neto de fabricación. Tiempo desde que se inicia una tarea en un punto de control hasta que se da por terminada (desde que una tarea pasa a EN CURSO hasta que pasa a TERMINADA).
+ Cantidad de tareas. Número de tareas terminadas.
+ Cantidad de procesos. Número de proceso (producción completa de partidas de producción) terminados.

__Dimensiones__:
+ Modelo (referencia)
+ Fecha de pedido
+ Cliente, grupo de clientes
+ Tipo de tarea / punto de control
+ Trabajador

### Producción: incidencias, frecuencia y coste

__Medidas__:
+ Número de incidencias. Cantidad de incidencias que se han producido.
+ Sobrecoste. Suma de costes asociados a la incidencia (horas de trabajo / máquina + materiales extra).
+ Prendas afectados. Cantidad de prendas que han sufrido las incidencias

__Dimensiones__:
+ Tipo de incidencia
+ Modelo (referencia)
+ Fecha de pedido
+ Fecha de tarea
+ Cliente, grupo de clientes
+ Tipo de tarea / punto de control en el que se produce la incidencia
+ Trabajador

### Almacén: consumos por producto

__Medidas__:
+ Cantidad de material consumido.
+ Valor del material consumido.

__Dimensiones__:
+ Modelo (referencia) fabricado
+ Fecha de pedido
+ Cliente, grupo de clientes
+ Consumo por incidencia (sí / no)


# Funcionalidades ECONOMÍA CIRCULAR

## Funcionalidades de almacén

### Escandallo incluye la generación de subproductos reciclables
El escandallo debe incluir la generación de subproductos, como retales, que pueden ser reciclados. Estos subproductos se registrarán junto con los productos principales para asegurar su trazabilidad y gestión adecuada.

Los productos reciclables se registrarán como _componentes de cantidad negativa_, para reflejar que son generados, no consumidos, durante el proceso de producción.

### Escandallo incluye _opciones_ de materiales / subproductos reciclables
El escandallo también debe incluir opciones para utilizar materiales reciclables y generar subproductos reciclables. Esto permitirá elegir alternativas más sostenibles durante la producción.

Las opciones de componentes reciclables se configurarán asociando el componente tradicional con su opción reciclable, y permitiendo al usuario indicar cuál de las opciones de composición desea usar en cada fabricación.

#### Trazabilidad de algunos materiales reutilizados clave
El sistema debe permitir la trazabilidad de materiales clave que se reutilizan en la producción. Esto incluye el seguimiento desde su entrada en el almacén hasta su uso en el proceso de fabricación.

Un material clave en el sector del calzado es la piel, por ser el componente más caro, con más necesidad de trazabilidad, y que puede generar un subproducto reciclable de mayor valor.

También puede ser necesaria su trazabilidad debido a la obligación de cumplimiento de nueva legislación.

### Venta o registro de salida de subproductos (retales, etc.) reciclables
Registro de la venta o salida de subproductos reciclables, como retales, para asegurar su correcta gestión y reutilización.

La realización de órdenes de producción no solo generará el producto principal, sino que podrá generar otros productos secundarios que tendrán su propia referencia, aumentarán su stock, y cuya salida será registrada. En función de su valor, estos productos podrán ser vendidos o bien solo entregados a clientes o entidades de tratamiento de residuos.

## Funcionalidades de producción

#### Indicación de uso de opción reciclable en órdenes de fabricación
Cada orden de fabricación debe indicar si se está utilizando la opción de materiales reciclables. Esto permitirá un mejor seguimiento y cálculo de la sostenibilidad de la producción.

#### Cómputo de %reciclable de materiales por orden de producción
Se calculará el porcentaje de materiales reciclables utilizados en cada orden de producción. Esto ayudará a medir el impacto ambiental de la producción y fomentar el uso de materiales reciclables.

#### Cómputo de subproductos reciclables generados (retales, etc.)
El sistema debe computar la cantidad de subproductos reciclables generados durante el proceso de producción. Esto incluye retales y otros materiales que pueden ser reciclados.

Los productos reciclables pueden registrarse de forma automática, a través del escandallo, o bien crearse mediante su introducción indirecta. Por ejemplo, mediante pesaje de retales generados a lo largo de un día de trabajo. En este caso la asocicación de productos reciclables a cada órden de producción será más problemática.

## Estadística

### Indicadores y estadísticas de sostenibilidad
Para asegurar la gestión adecuada de los materiales reciclables y subproductos generados durante la producción, se incluirán varios indicadores y estadísticas clave.

#### Estadísticas de Subproductos generados
Se generarán estadísticas sobre la cantidad y tipo de subproductos generados durante la producción. Esto permitirá identificar oportunidades para mejorar la eficiencia y reducir el desperdicio.

#### Estadísticas de Porcentaje de material reciclado utilizado
El sistema debe proporcionar estadísticas sobre el porcentaje de material reciclado utilizado en la producción. Esto ayudará a medir y mejorar los esfuerzos de sostenibilidad de la empresa.


Indicador de reusabilidad, reciclaje
50% sobre el presupuesto
Colaboradores con sus propios gastos

10% a éxito

• La trazabilidad de productos, sustancias, materiales y residuos
• Nuevos modelos de negocio basados en la digitalización como
instrumento para procesos de servitización
• Servicios de retorno de productos usados para reutilizarlos,
remanufacturarlos o reciclarlos

Residuos
Recogida de retales y sobrantes en toda la cadena de producción
Seguimiento de los retales hasta su salida (albaranes de salida)
Gestión de retales como subproductos con referencia específica

Cierre de tarea de corte con pesaje de retales y generación de stock de retal

Reutilización
Identificación de materias primas y semielaborados ya reciclados > cálculo del porcentaje de producto reciclado por producto ¿Indicador?
Catalogación de materias primas en función de toxicidad o posibilidad de reciclaje
Componentes sustitutivos y grado de uso en producciones ¿Indicador?
Catálogo con productos y sustitutivos para ciertas composiciones / tareas de producción
Permitir la introducción paulatina de materiales reciclados en los procesos de producción