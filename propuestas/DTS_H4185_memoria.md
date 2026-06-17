# Memoria técnica del proyecto

**Título del proyecto:** Sistema de Gestión de Almacén (SGA) y Control de Fabricación

**Acrónimo:** SGA

**Empresa solicitante:** DTS-Oabe - Yeboyebo SLU

**Referencia:** #DTS #H4185

---

## 1. ACTIVIDAD Y SITUACIÓN ACTUAL DE LA EMPRESA EN BASE A TECNOLOGÍA

DTS Oabe es un laboratorio especializado en el desarrollo, fabricación y comercialización de productos biocidas orientados a la sanidad ambiental y alimentaria, el control de Legionela y la protección de la madera. La empresa opera con un modelo mixto que combina producción propia —formulación y envasado de productos químicos— con actividad comercial, gestionando tanto materias primas de entrada como producto terminado de salida hacia clientes industriales y profesionales.

Desde el punto de vista tecnológico, DTS Oabe dispone de un sistema ERP personalizado basado en Eneboo que cubre los procesos centrales del negocio: facturación de compras y ventas, contabilidad, gestión de stock y soporte básico a la producción. Esta solución ha permitido digitalizar los procesos administrativos y mantener un control de inventario general, si bien carece de las capacidades necesarias para gestionar de forma precisa y segura un almacén en expansión con productos de naturaleza química.

La gestión actual del almacén se apoya en el ERP para el control de entradas y salidas de stock, pero no dispone de un sistema de ubicaciones estructurado, ni de herramientas específicas para la gestión de zonas diferenciadas por tipo de producto, control de lotes con trazabilidad completa, ni integración con dispositivos de lectura de códigos en planta. Los operarios de almacén realizan las tareas de recepción, ubicación, preparación de pedidos y expedición con un soporte digital limitado, lo que genera dependencia del conocimiento individual y dificulta el escalado operativo.

---

## 2. PROBLEMA/NECESIDAD DETECTADA. OBJETIVOS DEL PROYECTO

### Problema y necesidad detectada

La empresa se encuentra en un proceso de ampliación de sus instalaciones de almacén que hace insostenible el modelo de gestión actual. El incremento de la capacidad física de almacenamiento, junto con el crecimiento del volumen de referencias gestionadas, genera una serie de necesidades específicas que el sistema actual no puede cubrir:

**Control de ubicaciones.** El almacén ampliado requerirá una gestión precisa de la posición de cada artículo dentro de la instalación. Sin un sistema de ubicaciones estructurado por pasillo, estantería y altura, la localización de mercancía se vuelve ineficiente y propensa a errores, especialmente al trabajar con productos de vida útil limitada o con restricciones de proximidad entre familias.

**Recopilación de datos para optimización.** Existe una necesidad estratégica de capturar información detallada sobre los movimientos internos y externos del almacén: condiciones de almacenamiento requeridas por artículo (temperatura, compatibilidad química, almacenamiento en zona APQ), operador que realiza cada operación, lote, caducidad y ubicación en cada momento. Esta información, una vez estructurada, constituirá la base para aplicar herramientas de inteligencia artificial orientadas a la optimización de rutas de picking, propuesta de ubicaciones y análisis de rotaciones.

**Cumplimiento normativo.** DTS Oabe maneja productos químicos que pueden estar sujetos a regulación específica en materia de almacenamiento, etiquetado y trazabilidad. La normativa en este ámbito está en evolución, y la empresa necesita disponer de una infraestructura de gestión capaz de adaptarse a futuros requisitos legales relacionados con el almacenaje de sustancias peligrosas, bases, ácidos y biocidas, incluyendo la gestión documental de Fichas de Datos de Seguridad (FDS) y el control de condiciones de proximidad entre artículos. En este marco, el SGA establecerá zonas especiales dentro del almacén: una zona de cuarentena para los productos que requieran validación antes de su incorporación al stock disponible, y una zona de producto rechazado para aislar aquellas referencias que no superen los controles de calidad o presenten incidencias, garantizando en todo momento la trazabilidad y el cumplimiento de los protocolos de seguridad aplicables.

**Eficiencia en la preparación de pedidos.** La ausencia de un sistema guiado de picking implica tiempos de preparación más elevados de lo necesario, mayor tasa de error y dificultad para gestionar picos de demanda o consolidar varios pedidos en un mismo recorrido de almacén.

**Impacto ambiental no medido.** DTS Oabe fabrica y comercializa productos químicos en distintos formatos de envase. En la actualidad no existe un mecanismo sistemático para evaluar el impacto ambiental de las decisiones de formulación, envasado o gestión operativa del almacén. La ausencia de datos estructurados sobre movimientos, consumos de materiales y composición de envases impide abordar proyectos de mejora ambiental basados en evidencia, tanto en el ámbito del ecodiseño de producto como en la optimización del embalaje de expedición.

### Objetivos del proyecto

El proyecto tiene como finalidad dotar a DTS Oabe de un Sistema de Gestión de Almacén (SGA) integrado en su ERP actual, que resuelva las necesidades identificadas sin generar duplicidad de datos ni procesos manuales de traspaso de información. Los objetivos específicos son:

- **Integración plena con el ERP.** El SGA se desarrollará como un módulo del ERP existente (Eneboo), de forma que las entradas de mercancía deriven automáticamente de los albaranes de compra, y las salidas se generen a partir de los pedidos de venta, eliminando la introducción manual de datos y los errores asociados.

- **Gestión de ubicaciones.** Implementar un sistema de ubicaciones físicas estructurado por pasillo, estantería y altura, con soporte para ubicaciones móviles (carros, gavetas), zonas lógicas diferenciadas (cuarentena, masivo, picking, preparación, APQ) y asignación de familias o rangos de artículos a zonas específicas.

- **Optimización del picking.** Reducir los tiempos de preparación de pedidos mediante órdenes de trabajo guiadas, consolidación de varios pedidos en un mismo recorrido (pick & pack) y sistemas de reposición automática de zonas de picking desde zonas de masivo.

- **Trazabilidad completa.** Registrar por cada movimiento: artículo, lote, fecha de caducidad, ubicación de origen y destino, operador y fecha/hora. Garantizar el seguimiento de cada materia prima, envase, embalaje, máquina y tiempo de máquina, producto terminado o comercializado, operario y tiempo de cada operario durante todo el recorrido interno: desde la recepción hasta la expedición directa o hasta su transformación en producto final a través del proceso de fabricación.

- **Seguridad y compatibilidad de almacenamiento.** Definir condiciones de almacenamiento por artículo y por ubicación (APQ, temperatura, compatibilidad química), y controlar el flujo de productos a través de zonas de cuarentena antes de su incorporación al stock disponible.

- **Base de datos para análisis e IA.** Generar un registro estructurado de todos los movimientos y condiciones de almacén que permita, en una fase posterior, aplicar herramientas de inteligencia artificial para la optimización de ubicaciones, análisis de rotaciones ABC y propuesta de reubicaciones.

- **Sostenibilidad y reducción del impacto ambiental.** Aprovechar los datos acumulados por el SGA —movimientos de mercancías, consumos de materiales y listas de materiales (BOM) del ERP— para iniciar un proyecto de ecodiseño orientado a versionar los productos actuales hacia alternativas con menor impacto ambiental.

- **Optimización del embalaje asistida por IA.** Desarrollar un motor de cálculo que, en el momento de preparar cada pedido, determine automáticamente el tipo y tamaño de embalaje más adecuado en función del volumen, peso y fragilidad de los artículos incluidos. La solución se apoyará en algoritmos de empaquetado tridimensional (3D Bin Packing Problem) y técnicas de optimización matemática, reduciendo el consumo de materiales de embalaje, el peso de los envíos y la huella ambiental de cada expedición. Las restricciones de compatibilidad química propias del catálogo de DTS Oabe se incorporarán como reglas adicionales en el modelo.

---

## 3. DESCRIPCIÓN DE LAS TAREAS DE INGENIERÍA Y/O CONSULTORÍA A REALIZAR

El proyecto se articula en torno a dos grandes bloques de trabajo: la consultoría de procesos y el desarrollo e implantación del módulo SGA.

**Consultoría de procesos logísticos**
Análisis detallado de los flujos actuales de recepción, almacenamiento, preparación y expedición. Diseño de la estructura de zonas y ubicaciones del almacén ampliado. Definición de las reglas de negocio que regirán la propuesta automática de ubicaciones, la reposición de picking y la generación de órdenes de trabajo. Levantamiento del catálogo de artículos con sus condiciones de almacenamiento y compatibilidades.

**Desarrollo del módulo SGA**
- *Gestión de ubicaciones:* Generador de ubicaciones por rangos (pasillo-estantería-altura), soporte para ubicaciones móviles (carros y gavetas), visualización de planta y asignación de características por ubicación o rango.
- *Órdenes de trabajo de almacén:* Entradas de mercancía (con recepción en playa y ubicación posterior), salidas, transferencias entre almacenes, transferencias entre zonas (reposición), inventarios (permanente, aleatorio, ciego) y pick & pack.
- *Configuración de pasos por tipo de orden:* Parametrización de qué operaciones exige cada tipo de orden: lectura de código de producto, lectura de código de lote, confirmación de ubicación de origen y destino, confirmación de cantidad, recuento aleatorio forzoso y registro de incidencias.
- *Generador de órdenes basado en reglas:* Creación automática de órdenes a partir de eventos del ERP (albarán de compra → orden de entrada; pedido de venta → orden de salida o picking) y de reglas de stock (stock mínimo en zona de picking → orden de reposición).
- *Gestión de fabricación:* Órdenes de fabricación y envasado vinculadas a listas de materiales (BOM), registro de cantidades producidas y consumidas, gestión de ubicaciones de origen de materias primas y destino de producto terminado.
- *Motor de optimización de embalaje (3D Bin Packing):* Módulo Python integrado con el ERP que, al generar una orden de preparación, calcula automáticamente qué caja o combinación de cajas minimiza el material utilizado. El motor consulta las dimensiones, peso y atributos de fragilidad y compatibilidad química de cada artículo del pedido, aplica los algoritmos de optimización y presenta la recomendación al operario en el terminal antes de iniciar el embalaje. Los formatos de caja disponibles se parametrizan en el maestro de materiales de embalaje.

**Integración con hardware**
Desarrollo de las interfaces necesarias para la comunicación del módulo SGA con los dispositivos de lectura de códigos de barras/QR y con las impresoras de etiquetas de producto, caja y palet.

**Implantación, formación y soporte**
Parametrización del sistema en el entorno productivo de DTS Oabe, carga inicial de datos (artículos, ubicaciones, condiciones), formación a los usuarios y soporte durante la fase de estabilización.

---

## 4. DESCRIPCIÓN DE LAS INVERSIONES EN HARDWARE Y SOFTWARE A ABORDAR EN EL PROYECTO

### Inversiones en software

| Concepto | Descripción |
|---|---|
| Consultoría de procesos | Análisis, diseño y especificación funcional del SGA |
| Desarrollo del módulo SGA | Programación del módulo integrado en el ERP Eneboo |
| Integración con hardware | Desarrollo de drivers y protocolos de comunicación con lectores e impresoras |
| Implantación y formación | Parametrización, carga de datos, formación de usuarios y soporte inicial |

### Inversiones en hardware

| Concepto | Descripción |
|---|---|
| Impresoras de etiquetas | Impresoras térmicas para etiquetas de producto/caja y etiquetas de palet en distintos formatos |
| Terminales de mano (PDAs) | Lectores industriales de códigos de barras y QR con pantalla, resistentes al entorno de almacén |
| Panel PC de planta | Terminal fijo en almacén para supervisión y gestión de órdenes de trabajo |

---

## 5. ANÁLISIS DETALLADO DE LA SOLUCIÓN A IMPLANTAR. TECNOLOGÍAS A EMPLEAR EN EL PROYECTO

La solución se basa en el desarrollo de un módulo SGA nativo sobre el ERP Eneboo, evitando la integración con un sistema de gestión de almacén externo y manteniendo toda la información en una única base de datos. Este enfoque garantiza la coherencia de los datos, elimina los riesgos de sincronización y permite aprovechar la lógica de negocio ya existente en el ERP (clientes, proveedores, artículos, pedidos, albaranes).

**Arquitectura del sistema**

El módulo SGA extiende el ERP con los siguientes bloques funcionales:

- *Maestro de ubicaciones:* Estructura jerárquica Almacén → Zona → Pasillo → Estantería → Altura, con soporte de ubicaciones móviles. Cada ubicación tiene atributos de capacidad, condiciones ambientales y compatibilidades de producto. Un generador de rangos permite crear conjuntos de ubicaciones de forma masiva a partir de prefijos y rangos numéricos.

- *Maestro de artículos ampliado:* Los artículos incorporan campos de condiciones de almacenamiento (temperatura, zona APQ, compatibilidad química), tipos de envase con factores de conversión y ubicaciones preferentes o fijas. Esta información se utiliza tanto en la propuesta automática de ubicaciones como en los controles de seguridad.

- *Motor de órdenes de trabajo:* Cada tipo de orden (entrada, salida, transferencia, reposición, inventario, pick & pack, fabricación) tiene un flujo de pasos configurables que el operario sigue en el terminal de mano. Los pasos pueden exigir la lectura de códigos de barras o QR para el artículo, el lote, la ubicación de origen, la ubicación de transporte y la ubicación de destino, así como la confirmación de cantidades y la realización de recuentos aleatorios.

- *Zonas lógicas y cuarentena:* La mercancía recibida pasa obligatoriamente por una zona de playa y posteriormente a cuarentena antes de ser validada e incorporada al stock disponible. Desde cuarentena, los palets validados se trasladan a la zona de masivo o picking según corresponda. La zona APQ gestiona el almacenamiento de productos químicos peligrosos con acceso y condiciones controlados.

- *Generador de órdenes por reglas:* Motor de reglas que crea órdenes automáticamente en función de eventos (albaranes, pedidos) o de condiciones de stock (mínimos de zona de picking, periodos de inventario). Las reglas son parametrizables sin necesidad de modificar código.

**Tecnología de hardware**

Los terminales de mano son dispositivos industriales con lector integrado de código de barras 1D/2D (QR), pantalla táctil y conectividad WiFi. La comunicación con el ERP se realiza mediante interfaz web ligera o protocolo directo, permitiendo operar en tiempo real. Las impresoras de etiquetas son de tecnología térmica directa o transferencia térmica, con soporte para distintos formatos de etiqueta (artículo individual, caja, palet). El panel PC fijo en almacén permite a los responsables supervisar el estado de las órdenes de trabajo en curso y reasignar tareas.

**Integración con la app para agentes comerciales**

El SGA se integrará con la aplicación móvil de agentes comerciales ya disponible, extendiendo su funcionalidad con acceso en tiempo real a la información de stock del almacén. A través de esta integración, los agentes podrán consultar la disponibilidad actualizada de cualquier referencia antes de comprometerse con un cliente, y registrar pedidos desde la propia app de forma que el stock correspondiente quede inmediatamente reservado en el SGA. Esta reserva bloquea las unidades comprometidas para el resto de operaciones del almacén, evitando sobreventas y garantizando que la preparación del pedido pueda iniciarse en cuanto el agente lo confirme.

**Orientación a datos e IA**

Cada operación queda registrada con datos de artículo, lote, caducidad, ubicación, operador, fecha y hora. Esta granularidad permite construir análisis de rotaciones ABC, propuestas de reubicación basadas en frecuencia de movimiento y, en una fase posterior, alimentar modelos de inteligencia artificial para la optimización de rutas de picking y la predicción de necesidades de reposición.

**Sostenibilidad y reducción del impacto ambiental**

El sistema abre dos vías de mejora ambiental que se refuerzan mutuamente: el ecodiseño de producto y la optimización del embalaje de expedición.

*Ecodiseño basado en datos.* El ERP de DTS Oabe ya gestiona las listas de materiales (BOM) de los productos fabricados, incluyendo la composición de los envases y el carácter reciclado o no de cada material. El SGA añadirá el histórico detallado de todos los movimientos de materias primas y producto terminado. La combinación de ambas fuentes —BOM con atributos ambientales y datos reales de consumos— constituye la base necesaria para un proyecto de ecodiseño en el que analizar alternativas de formulación, composición y envasado con menor huella ambiental. Este análisis puede abordar, entre otros, la sustitución de materiales no reciclados en envases, la reducción del peso o volumen de embalaje por unidad de producto, y la evaluación del ciclo de vida de las distintas versiones de un mismo artículo.

*Optimización del embalaje en la preparación de pedidos mediante IA.* El sistema de picking incorporará un motor de recomendación de embalaje basado en algoritmos de inteligencia artificial que va más allá de la simple sugerencia de formato. En lugar de utilizar una caja estándar para cualquier expedición, el módulo calcula en tiempo real la distribución tridimensional óptima de los artículos del pedido dentro del conjunto de formatos de embalaje disponibles.

El problema que resuelve este módulo se conoce en el ámbito de la optimización combinatoria como el **Problema de Empaquetado Tridimensional (3D Bin Packing Problem)**. Dado un conjunto de artículos con sus dimensiones y pesos, el algoritmo determina en qué caja o cajas caben, en qué orientación y posición, minimizando el volumen desperdiciado y el número de bultos resultantes.

La solución técnica se construye sobre el ecosistema Python de optimización y se integra con el ERP mediante una API de servicio interno:

- **Algoritmo base de empaquetado geométrico** (ejemplo de herramienta: librería `py3dbinpacking`): resuelve la distribución volumétrica pura para un pedido concreto, iterando sobre los formatos de caja del catálogo y devolviendo la combinación con menor volumen sobrante.
- **Optimización matemática** (ejemplo de herramienta: Google OR-Tools): cuando intervienen restricciones adicionales —peso máximo soportado por caja, incompatibilidades de producto, número máximo de bultos por expedición— se aplica un solver de programación lineal entera que minimiza una función de coste que combina el coste de los materiales, el peso total del envío y las penalizaciones por restricciones incumplidas.
- **Restricciones de compatibilidad química**: el maestro de artículos del SGA incluye ya atributos de compatibilidad entre productos (normativa APQ, incompatibilidades entre familias químicas). Estas restricciones se traducen en reglas del modelo de optimización, de forma que el motor nunca proponga colocar en la misma caja artículos que no deban estar en contacto o proximidad.
- **Clasificación por fragilidad y reserva de espacio para amortiguación**: cada artículo lleva una etiqueta de fragilidad (frágil, normal, robusto). Los artículos frágiles amplían virtualmente su volumen en el modelo para reservar el espacio necesario para el material de amortiguación, garantizando que la propuesta sea físicamente realizable.

Ampliación de aprendizaje adaptativo con datos propios:

- **Capa de predicción por aprendizaje automático**: a partir del histórico de pedidos preparados y almacenado en el SGA, se entrena un modelo de clasificación que anticipa el tipo de embalaje más probable antes de ejecutar el algoritmo completo, acelerando el tiempo de respuesta para los pedidos con patrones recurrentes.
- **Evolución hacia aprendizaje por refuerzo**: en una fase posterior, el motor puede evolucionar hacia un agente de Aprendizaje por Refuerzo (Reinforcement Learning) que aprende de forma continua a partir de la retroalimentación real de los operarios, ajustando las recomendaciones en función de las correcciones manuales y los resultados logísticos observados.

El operario recibe la recomendación en el terminal de mano o panel PC en el momento de iniciar el embalaje: formato de caja, materiales de relleno sugeridos y, opcionalmente, una representación esquemática de la distribución de los artículos. Puede aceptar la propuesta o registrar una incidencia si decide modificarla, retroalimentando así el modelo. Esta funcionalidad reduce el consumo de materias primas de embalaje (cartón, film, relleno), el peso de los envíos y el volumen ocupado en el transporte, contribuyendo tanto a la reducción de costes como a la disminución de la huella ambiental asociada a cada expedición.

---

## 6. CALENDARIO DE EJECUCIÓN DEL PROYECTO

El proyecto se planifica para una duración de 12 meses, distribuidos en las siguientes fases:

| Fase | Período | Actividades |
|---|---|---|
| 1. Consultoría y diseño | Meses 1-2 | Análisis de procesos actuales, diseño de planta y zonas, especificación funcional, definición de reglas de negocio |
| 2. Desarrollo SGA — núcleo | Meses 2-5 | Maestro de ubicaciones, motor de órdenes de trabajo, gestión de entradas y salidas, zonas lógicas y cuarentena |
| 3. Desarrollo SGA — avanzado | Meses 5-7 | Módulo de fabricación, generador de órdenes por reglas, integración con hardware (lectores e impresoras) |
| 4. Implantación | Meses 7-9 | Instalación en entorno productivo, parametrización de zonas y artículos, carga inicial de datos |
| 5. Pruebas y formación | Meses 9-11 | Pruebas piloto con operarios, formación de usuarios, ajustes y correcciones |
| 6. Puesta en marcha y estabilización | Meses 11-12 | Arranque en producción, soporte intensivo, cierre de incidencias y documentación final |

---

## 7. DESGLOSE DEL PRESUPUESTO

*(pendiente de desarrollo)*

---

---

## Referencia: Requerimientos SGA (notas del cliente)

### Requerimientos SGA
1. Gestión de referencias
Configuración Básica de referencias
    • Definir Productos: BBDD de todos los productos que se manejan (materias primas, fabricados y químicos). Para cada producto, incluir:
        ◦ Código de producto
        ◦ Nombre y descripción
        ◦ Categoría (fabricado, químico, etc.)
        ◦ Condiciones de almacenamiento
        ◦ Número de lote y fecha de caducidad
        ◦ Campos de ubicación
        ◦ Volumen de producto
        ◦ Peso de producto
        ◦ Tipo de producto (para identificar si un producto puede estar ubicado al lado de otro o no)
Módulo de Entradas y Salidas (debe registrar cada vez que un producto entra o sale del almacén.)
Campos:
        ◦ Número de lote y cantidad recibida
        ◦ Ubicación en el almacén (multiubicación)
        ◦ Fecha de entrada/salida
        ◦ Operador que gestionó la entrada o salida
    • Registrar Movimientos Internos: Esto permite gestionar transferencias entre diferentes ubicaciones dentro del almacén. Esto hace podamos mantener un historial de la ubicación de cada referencia individualmente.
    • Propuesta de ubicación: El sistema debe proponer una ubicación en la entrada siguiendo criterios cómo ABC de ventas, tamaños, ubicación fija, recepción con una orden de venta,…

Configurar Alerta de Stock y Reorden
    • Configurar para monitorear los niveles de stock mínimo y máximo por producto. Esto ayuda a mantener el inventario adecuado y programar pedidos de reabastecimiento automáticamente cuando el stock alcanza el límite mínimo. (esto ya tenéis)
    • Configurar para monitorear si los niveles de stock en una ubicación son bajos y mandar orden para realizar movimiento interno de mercancía.
    • Configurar el sistema para que se realice automáticamente un ABC de referencias para que las que las referencias con más movimientos el sistema mande una orden para reubicarlas en la zona más cercana al picking.

2. Trazabilidad de Productos
Campos:
    • Número de Serie o Lote: Esto permite rastrear productos a nivel de lote.
    • Historial de Lotes: Añadir un historial de movimientos para cada lote, permitiendo ver todas las entradas, salidas, y transferencias.
    • Fecha de Caducidad: Importante para controlar la vigencia de productos y recibir alertas de productos próximos a vencer.
Control de Trazabilidad
    • Registrar los detalles de cada movimiento, incluyendo el operador, la ubicación, y la fecha.
    • Posibilidad de personalizar un módulo para generar informes de trazabilidad de cada lote, permitiendo saber el historial completo de cada producto, desde su recepción hasta su salida del almacén.

3. Gestión de Seguridad para Productos Químicos
Documentación y Registros (ya lo tenéis)
    • Para los productos químicos, es recomendable gestionar la documentación de seguridad, como las Fichas de Datos de Seguridad (FDS).
Incluir una sección de Notas o Documentos para adjuntar FDS, manuales de seguridad y precauciones de manejo, especialmente en relación a la manipulación y almacenamiento seguro


Condiciones de Almacenamiento
    • Configurar campos de Condiciones de Almacenamiento como temperatura, humedad, y ventilación. (PRO)
    • Implementar un sistema de alertas para notificar si las condiciones no son las adecuadas o si es necesario realizar una inspección. (PRO)
    • Detallar medidas de ubicaciones y peso soportado en cada ubicación
    • Condiciones sobre proximidad de una tipología de producto con otro

3. Inventariado
Tipologías de inventario
    • Inventario permanente: Posibilidad de crear un inventario permanente para enviar ordenes de conteo semanales de zonas
    • Inventario aleatorio: Bajo unas condiciones como puede ser un stock mínimo en el momento de realizar la preparación obligara a contar el producto que está disponible en esa ubicación
    • Inventario tradicional
En todos los casos posibilidad de Inventario ciego: Posibilidad de ocultar los datos de stock
Validación de inventario: Crear diferentes permisos para realizar inventarios ya que algunas actualizaciones de stock de productos o todas deberán ser validados por responsables

4. Informes y Reportes Personalizados
Informes de Inventario
    • Crear informes personalizados de inventario para visualizar el stock actual, el historial de movimientos, los productos próximos a caducar, y los productos con cantidades críticas.
Reportes de Trazabilidad
    • Configurar un reporte de trazabilidad que detalle el historial de cada lote. Esto es fundamental para productos químicos, ya que permite cumplir con las normativas de seguridad y control de calidad.
Control de Caducidad y Seguridad
    • Implementar reportes que muestren el estado de productos químicos: fecha de caducidad, condiciones de almacenamiento, y cualquier incidente registrado.

5. Automatización y Tecnología de Escaneo
Considerar el uso de códigos de barras o códigos QR tanto en los productos como en las ubicaciones:
    • Códigos de Barras: Agregar etiquetas a cada lote, facilitando la lectura rápida de información con escáneres conectados a Eneboo.
    • QR: Puede contener mucha más información que un código de barras tradicional. Esto permite almacenar datos como el nombre del producto, número de lote, fecha de caducidad, composición química, y otros detalles críticos para el manejo de productos químicos.
