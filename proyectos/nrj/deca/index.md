# Manual DeCA (Documento de Control del transporte)

El **DeCA** es el documento de control que acompaña a la mercancía durante el transporte. Desde el ERP se genera e imprime a partir de una **salida de almacén** vinculada a un albarán de venta.

Antes de imprimir el primer DeCA hay que hacer la [configuración](#configuración) una sola vez. Después, para cada salida basta con [rellenar sus datos de transporte](#datos-de-transporte-de-la-salida) e [imprimir el DeCA](#imprimir-el-deca).

## Configuración

### Conexión con Olula

Iremos a **Área de Facturación -> Principal -> Configuración** y, en la pestaña **Servidor**, indicaremos en el campo **URL API Olula** la dirección facilitada por Yeboyebo.

<!-- CAPTURA: formulario Configuración, pestaña Servidor, con el campo "URL API Olula" relleno. -->

### Permisos en Olula

Cada usuario que vaya a imprimir el DeCA debe existir en Olula con el **mismo identificador** que en Eneboo, y el **grupo** al que pertenece debe tener permitidas estas reglas de acceso:

| Regla                                   | Para qué se necesita                                                                 |
| --------------------------------------- | ------------------------------------------------------------------------------------ |
| **auth.token.crear**                    | Obtener el token de Olula desde la ficha de usuario (botón **Obtener token Olula**). |
| **ventas.albaran** (Albaranes de venta) | Crear, actualizar e imprimir el DeCA.                                                |

Las reglas se configuran por grupo en Olula, en el menú de usuario (arriba a la derecha) **Administración -> Grupos**. Una regla también queda permitida si no está informada y lo está el nivel superior (el modelo o el acceso general del grupo). Ver el [Manual de reglas de acceso](../../../reglas_acceso/index.md).

<!-- ![Reglas de acceso del grupo](./img/deca_config_permisos_olula.png) -->

<!-- CAPTURA: Olula, Administración -> Grupos, grupo de los usuarios de Eneboo con las reglas "auth.token.crear" y "Albaranes de venta" en Permitido. -->

Si falta alguno de estos permisos, Olula rechazará la petición y Eneboo mostrará un error al obtener el token o al imprimir el DeCA.

### Token de Olula de cada usuario

Cada usuario que vaya a imprimir el DeCA necesita su propio token de acceso a Olula.

- Iremos a **Área de Facturación -> Principal -> Usuarios** y editaremos el usuario.
- En la pestaña **General**, dentro del recuadro **Contraseña**, pulsaremos **Obtener token Olula**.
- Nos pedirá la contraseña del usuario y el número de días de validez del token. Al aceptar, el token se rellena en el campo **Token Olula**.
- Guardaremos la ficha del usuario y **reiniciaremos Eneboo** para que se use el token nuevo.

<!-- ![Obtener token Olula](./img/deca_config_token_usuario.png) -->

<!-- CAPTURA: ficha de usuario, pestaña General, recuadro Contraseña, con el botón "Obtener token Olula" y el campo Token Olula relleno. -->

Cuando el token caduque habrá que repetir este paso.

### Naturaleza de la mercancía por defecto

Iremos a **Área de Facturación -> Principal -> Empresa** y, en la pestaña **Valores por defecto**, rellenaremos el campo **Naturaleza de la mercancía**, por ejemplo _Cítricos_.

Este valor se pondrá automáticamente en las salidas de almacén que no tengan la naturaleza informada.

<!-- ![Naturaleza de la mercancía](./img/deca_config_naturaleza_empresa.png) -->

<!-- CAPTURA: ficha de Empresa, pestaña Valores por defecto, con el campo "Naturaleza de la mercancía" relleno. -->

### Transportistas

Los transportistas de las salidas se gestionan en **Área de Facturación -> Almacén -> Transportistas salidas**. Para cada uno comprobaremos que tiene rellenos el **Nombre** y el **C.I.F./N.I.F.**, que son los datos que se copian a la salida al elegirlo.

<!-- ![Transportista](./img/deca_config_transportista.png) -->

<!-- CAPTURA: ficha de Transportistas salidas con los campos Nombre y C.I.F./N.I.F. rellenos. -->

### Direcciones de almacén y albarán

El origen y el destino del transporte se proponen a partir de direcciones que ya existen en el ERP:

- **Origen**: la dirección del **almacén** del albarán (**Área de Facturación -> Almacén -> Almacenes**).
- **Destino**: la dirección de envío del **albarán**.

Conviene revisar que los almacenes desde los que se sirve tienen la dirección completa.

### Lector de PDF

El DeCA se abre con la aplicación que el equipo tenga asignada para los ficheros PDF. Si se abre con otro programa (por ejemplo LibreOffice Draw), hay que cambiar en el equipo la aplicación predeterminada para PDF: botón derecho sobre cualquier PDF, **Abrir con**, elegir el lector de PDF y marcarlo como predeterminado.

## Datos de transporte de la salida

Iremos a **Área de Facturación -> Almacén -> Salidas de Almacén** y editaremos la salida. La salida debe estar **vinculada a un albarán**: el DeCA se genera para ese albarán.

En el recuadro **Datos del Transporte**:

- **Código Transportista**: elegiremos el transportista. Al hacerlo se rellenan automáticamente su **Nombre Transportista** y su **C.I.F./N.I.F. Transportista**. Estos datos se pueden modificar directamente.
- **Nº Autorización Transporte** (tarjeta MDPE/MDLE) y **Dirección Transportista**: son opcionales. Si se rellenan, salen en el DeCA.
- **Vehículo**: **Matrícula** (tractora, obligatoria), **Matrícula Semirremolque** y **Autorización Especial** (opcionales).
- **Conductor**: **Nombre del Chofer** y **Documento identificativo del Chofer** (DNI) (obligatorios).
- **Origen** y **Destino** del transporte.
- **Naturaleza de la Mercancía**.

Al abrir la ficha (o al cambiar el albarán), si **Origen**, **Destino** o **Naturaleza** están vacíos se proponen automáticamente (ver [Direcciones de almacén y albarán](#direcciones-de-almacén-y-albarán) y [Naturaleza de la mercancía por defecto](#naturaleza-de-la-mercancía-por-defecto)). Se pueden cambiar; los que ya tienen valor no se tocan.

<!-- ![Datos del Transporte](./img/deca_salida_transporte.png) -->

<!-- CAPTURA: ficha de salida de almacén, recuadro Datos del Transporte con transportista, vehículo, conductor, origen, destino y naturaleza rellenos. -->

Otros datos que usa el DeCA y que ya tiene la salida:

- **Fecha de Salida**: es la fecha del transporte.
- **Peso Bruto**: es el peso de la mercancía. Se calcula a partir de los palets asignados a la salida y debe ser mayor que 0.

Guardaremos la salida antes de imprimir el DeCA: el DeCA se genera con los datos **guardados**.

### Datos obligatorios

| Dato                                       | Dónde se rellena                                                |
| ------------------------------------------ | --------------------------------------------------------------- |
| Código del albarán y almacén               | Albarán vinculado a la salida                                   |
| Fecha del transporte                       | Salida, campo Fecha de Salida                                   |
| Nombre y C.I.F./N.I.F. del transportista   | Transportistas salidas (se copian al elegir el transportista)   |
| Matrícula tractora                         | Salida, recuadro Datos del Transporte                           |
| Nombre y DNI del conductor                 | Salida, recuadro Datos del Transporte                           |
| Origen, destino y naturaleza               | Salida, recuadro Datos del Transporte (se proponen por defecto) |
| Peso de la mercancía                       | Salida, Peso Bruto (palets asignados)                           |

Son opcionales: dirección y número de autorización del transportista, matrícula semirremolque y autorización especial.

## Imprimir el DeCA

- En **Área de Facturación -> Almacén -> Salidas de Almacén**, seleccionaremos la salida en la lista.
- Pulsaremos el botón **Imprimir DeCA**. El botón solo se muestra cuando hay una salida seleccionada.

<!-- ![Botón Imprimir DeCA](./img/deca_boton_imprimir.png) -->

<!-- CAPTURA: listado de salidas de almacén con una salida seleccionada, señalando el botón "Imprimir DeCA". -->

- Si la salida tiene vacíos el origen, el destino o la naturaleza, se completan y guardan con los valores por defecto antes de generar el DeCA.
- La primera vez que se imprime el DeCA del albarán, se **crea** el documento en Olula. Las siguientes veces se **actualiza** con los datos que hayan cambiado. En ambos casos se abre el PDF, desde el que podremos imprimirlo.

<!-- ![DeCA en PDF](./img/deca_pdf.png) -->

<!-- CAPTURA: el PDF del DeCA abierto en el lector de PDF. -->

- Si falta algún dato obligatorio, no se envía nada a Olula y se muestra un mensaje con **todos** los datos que faltan. Los completaremos en la salida, guardaremos y volveremos a pulsar el botón.

<!-- ![Datos que faltan](./img/deca_error_datos.png) -->

<!-- CAPTURA: mensaje "No se puede imprimir el DeCA. Faltan los siguientes datos del albarán:" con la lista de datos. -->

## Problemas frecuentes

| Mensaje o situación                                                                                              | Solución                                                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| _La salida de almacén no está asociada a ningún albarán_                                                         | Vincular la salida a su albarán y volver a imprimir.                                                                                                           |
| _No se puede imprimir el DeCA. Faltan los siguientes datos del albarán_                                          | Completar los datos indicados en la salida, guardar y volver a imprimir.                                                                                       |
| Falta el nombre o el NIF del transportista aunque la ficha del transportista los tiene                           | Volver a elegir el transportista en la salida para que se copien sus datos, y guardar.                                                                         |
| Falta el origen o el destino                                                                                     | Rellenarlos a mano en la salida, o completar la dirección del almacén o del albarán para que se propongan.                                                     |
| Falta el peso de la mercancía                                                                                    | Asignar los palets a la salida para que se calcule el Peso Bruto.                                                                                              |
| _No se han podido completar los datos del DeCA en la salida de almacén_                                          | No se pudo guardar la salida con los valores por defecto. Abrir la salida, revisar los datos, guardar y volver a imprimir.                                     |
| _Error al acceder a la API: No se ha podido conectar con el servidor_                                            | Revisar la **URL API Olula** en la configuración y que el servidor de Olula esté accesible.                                                                    |
| _El usuario ... no tiene un token de refresco de conexión asociado en su ficha de usuario_                       | Obtener de nuevo el **token Olula** del usuario y reiniciar Eneboo.                                                                                            |
| Error de permisos o de usuario no autorizado (_Usuario <<...>> no autorizado_) al obtener el token o al imprimir | Revisar que el grupo del usuario en Olula tiene permitidas las reglas **auth.token.crear** y **ventas.albaran** (ver [Permisos en Olula](#permisos-en-olula)). |
| _No se ha podido obtener el PDF del DeCA_                                                                        | Leer el detalle del mensaje (lo devuelve Olula). Si persiste, avisar a Yeboyebo.                                                                               |
| El PDF se abre con un programa que no es un lector de PDF                                                        | Cambiar la aplicación predeterminada para PDF del equipo (ver [Lector de PDF](#lector-de-pdf)).                                                                |

### Más

- [Volver al índice](../index.md)
