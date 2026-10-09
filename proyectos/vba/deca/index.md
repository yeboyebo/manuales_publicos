# Manual DeCA (Documento de Control del transporte)

El **DeCA** es el documento de control que acompaña a la mercancía durante el transporte. Desde el ERP se genera e imprime a partir de un albarán de venta.

Antes de imprimir el primer DeCA hay que hacer la [configuración](#configuración) una sola vez. Después, para cada albarán basta con [rellenar sus datos de transporte](#datos-de-transporte-del-albarán) e [imprimir el DeCA](#imprimir-el-deca).

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

Iremos a **Área de Facturación -> Principal -> Empresa** y, en la pestaña **Valores por defecto**, rellenaremos el campo **Naturaleza de la mercancía**, por ejemplo _Plantas ornamentales_.

Este valor se pondrá automáticamente en los albaranes que no tengan la naturaleza informada al abrirlos.

<!-- ![Naturaleza de la mercancía](./img/deca_config_naturaleza_empresa.png) -->

<!-- CAPTURA: ficha de Empresa, pestaña Valores por defecto, con el campo "Naturaleza de la mercancía" relleno. -->

### Transportistas

Los transportistas son proveedores. Para cada uno iremos a **Área de Facturación -> Principal -> Proveedores** y comprobaremos:

- En la pestaña **General**:
  - Marcar el check **Transportista**.
  - Rellenar el **Nombre** y el **C.I.F./N.I.F.**
  - **Número autorización transporte mercancías** (tarjeta MDPE/MDLE): es opcional, porque la inspección la comprueba en el Registro de Empresas y Actividades de Transporte (REAT). Si se rellena, saldrá en el DeCA. Este campo solo se puede editar cuando el check **Transportista** está marcado.
- En la pestaña **Direcciones**: el transportista debe tener una dirección marcada como **principal**. Es la que aparece en el DeCA.

<!-- ![Transportista](./img/deca_config_proveedor_transportista.png) -->

<!-- CAPTURA: ficha de proveedor, pestaña General, con el check "Transportista" marcado y el campo "Número autorización transporte mercancías" visible. -->

### Lector de PDF

El DeCA se abre con la aplicación que el equipo tenga asignada para los ficheros PDF. Si se abre con otro programa (por ejemplo LibreOffice Draw), hay que cambiar en el equipo la aplicación predeterminada para PDF: botón derecho sobre cualquier PDF, **Abrir con**, elegir el lector de PDF y marcarlo como predeterminado.

## Datos de transporte del albarán

Iremos a **Área de Facturación -> Facturación -> Albaranes de venta** y editaremos el albarán.

- **Transportista**: elegiremos el transportista. Al hacerlo se rellenan automáticamente, su nombre, C.I.F./N.I.F., dirección principal y número de autorización. Estos datos se pueden modificar directamente.
- En el cuadro de la deracha se construye la secuancia que ya se usaba en el albarán y no es editable directamente.
- **Vehículo**: **Matrícula tractora** (obligatoria), **Matrícula semirremolque** y **Autorización especial** (opcionales).
- **Conductor**: **Nombre** y **DNI** del conductor (obligatorios).

<!-- ![Pestaña Transportista](./img/deca_albaran_transportista.png) -->

<!-- CAPTURA: albarán, pestaña Transportista, con los recuadros Transportista (minipestaña "Datos DeCA" abierta y rellena), Vehículo y Conductor. -->

### Pestaña CMR

- **Origen** y **Destino** del transporte.
- **Naturaleza** de la mercancía. Si estaba vacía, al abrir el albarán se rellena con el valor por defecto de la empresa; se puede cambiar.
- **Peso** de la mercancía (debe ser mayor que 0).

<!-- ![Pestaña CMR](./img/deca_albaran_cmr.png) -->

<!-- CAPTURA: albarán, pestaña CMR, con los campos Origen, Destino, Naturaleza y Peso rellenos. -->

Guardaremos el albarán antes de imprimir el DeCA: el DeCA se genera con los datos **guardados**.

### Datos obligatorios

| Dato                                                | Dónde se rellena                                           |
| --------------------------------------------------- | ---------------------------------------------------------- |
| Código del albarán y almacén                        | Albarán                                                    |
| Nombre, C.I.F./N.I.F. y dirección del transportista | Ficha del proveedor (se copian al elegir el transportista) |
| Matrícula tractora                                  | Albarán, pestaña Transportista, recuadro Vehículo          |
| Nombre y DNI del conductor                          | Albarán, pestaña Transportista, recuadro Conductor         |
| Origen, destino, naturaleza y peso                  | Albarán, pestaña CMR                                       |

Son opcionales: matrícula semirremolque, autorización especial y número de autorización del transportista.

## Imprimir el DeCA

- En **Área de Facturación -> Facturación -> Albaranes de venta**, seleccionaremos el albarán en la lista.
- Pulsaremos el botón **Imprimir DeCA** de la barra de botones.

<!-- ![Botón Imprimir DeCA](./img/deca_boton_imprimir.png) -->

<!-- CAPTURA: listado de albaranes de venta con un albarán seleccionado, señalando el botón "Imprimir DeCA" en la barra de botones. -->

- La primera vez que se imprime el DeCA de un albarán, se **crea** el documento en Olula. Las siguientes veces se **actualiza** con los datos que hayan cambiado en el albarán. En ambos casos se abre el PDF, desde el que podremos imprimirlo.

<!-- ![DeCA en PDF](./img/deca_pdf.png) -->

<!-- CAPTURA: el PDF del DeCA abierto en el lector de PDF. -->

- Si falta algún dato obligatorio, no se envía nada a Olula y se muestra un mensaje con **todos** los datos que faltan. Los completaremos en el albarán (o en la ficha del transportista), guardaremos y volveremos a pulsar el botón.

<!-- ![Datos que faltan](./img/deca_error_datos.png) -->

<!-- CAPTURA: mensaje "No se puede imprimir el DeCA. Faltan los siguientes datos del albarán:" con la lista de datos. -->

## Problemas frecuentes

| Mensaje o situación                                                                                              | Solución                                                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| _No se puede imprimir el DeCA. Faltan los siguientes datos del albarán_                                          | Completar los datos indicados en el albarán o en la ficha del transportista, guardar y volver a imprimir.                                                      |
| Faltan nombre, NIF o dirección del transportista aunque la ficha del proveedor los tiene                         | Volver a elegir el transportista en el albarán para que se copien sus datos, y guardar.                                                                        |
| Falta la dirección del transportista                                                                             | Dar de alta una dirección **principal** en la pestaña Direcciones del proveedor y volver a elegir el transportista en el albarán.                              |
| _Error al acceder a la API: No se ha podido conectar con el servidor_                                            | Revisar la **URL API Olula** en la configuración y que el servidor de Olula esté accesible.                                                                    |
| _El usuario ... no tiene un token de refresco de conexión asociado en su ficha de usuario_                       | Obtener de nuevo el **token Olula** del usuario y reiniciar Eneboo.                                                                                            |
| Error de permisos o de usuario no autorizado (_Usuario <<...>> no autorizado_) al obtener el token o al imprimir | Revisar que el grupo del usuario en Olula tiene permitidas las reglas **auth.token.crear** y **ventas.albaran** (ver [Permisos en Olula](#permisos-en-olula)). |
| _No se ha podido obtener el PDF del DeCA_                                                                        | Leer el detalle del mensaje (lo devuelve Olula). Si persiste, avisar a Yeboyebo.                                                                               |
| El PDF se abre con un programa que no es un lector de PDF                                                        | Cambiar la aplicación predeterminada para PDF del equipo (ver [Lector de PDF](#lector-de-pdf)).                                                                |

### Más

- [Volver al índice](../index.md)
