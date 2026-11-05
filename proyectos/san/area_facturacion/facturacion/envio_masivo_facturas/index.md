# Envío masivo de facturas por e-mail

Desde **Facturas de cliente** se envían por e-mail, de una vez, todas las facturas pendientes de enviar de un periodo: un correo por cliente con sus facturas en PDF.

Para enviar un único documento desde su ventana de envío (con Para, CC, CCo y adjuntos), ver el manual de [Envío mail](../../../../../extensiones/envio_mail/index.md).

## Configuración

| Qué | Dónde | Detalle |
| --- | --- | --- |
| Series que se envían | **Área de Facturación -> Facturación -> Configuración**, campo *Series facturas para el envío mail* | Series separadas por comas, por ejemplo `A,R`. Sin este campo el envío avisa y no hace nada |
| Ruta de los PDF | **Área de Facturación -> Facturación -> Configuración**, campo *Ruta de ficheros adjuntos* | Carpeta donde se generan los PDF. Es local: se configura en cada ordenador |
| Clientes que reciben las facturas por e-mail | Ficha del cliente, casilla *Enviar facturas por email* | Los clientes sin esta casilla no reciben correo; sus facturas se pueden imprimir |
| Un PDF por factura | Ficha del cliente, casilla *Enviar facturas PDF en ficheros separados* | Sin marcar, todas las facturas del cliente van en un único PDF |
| Destinatarios | Ficha del cliente: e-mail de la pestaña **General** y contactos de facturas de la pestaña **Agenda** | Ver abajo |
| Cuenta de correo, directorio temporal y firma | Ficha del usuario y **Empresa -> Envío mail** | Igual que en el manual de [Envío mail](../../../../../extensiones/envio_mail/index.md) |

## A quién se envía

- **Para:** todos los e-mails de la ficha del cliente (pestaña **General**). Si hay varios separados por comas, se envía a todos.
- **CC:** los contactos configurados para facturas en la pestaña **Agenda** del cliente.
- Si una dirección está a la vez en Para y en CC, se envía una sola vez.

## Cómo se hace

1. Abrir **Área de Facturación -> Facturación -> Facturas de cliente**.
2. Pulsar el botón **Envio Email**.
3. Indicar el intervalo de fechas (*Desde* y *Hasta*) y aceptar.
4. Aparece un resumen con el número de clientes con facturas pendientes de enviar y el número de facturas pendientes de imprimir (clientes sin envío por e-mail). Marcar lo que se quiere hacer:
    - **Enviar:** envía un correo por cliente.
    - **Imprimir:** imprime las facturas de los clientes que no reciben e-mail y las marca como enviadas.
5. Una ventana muestra el progreso cliente a cliente y, al terminar, el resultado: cuántas facturas se enviaron a cada cliente y los errores.

Las facturas enviadas quedan marcadas como **Enviado: Sí** y no se vuelven a enviar en el siguiente envío masivo.

## El correo

- Asunto: *Facturas emitidas*.
- Cuerpo con formato:

> Estimados Sres:
>
> Les remitimos las facturas correspondientes a los pedidos expedidos en las siguientes fechas:
>
> 02-01-2026 - Factura: 20260A000001
>
> Atentamente
>
> *Nombre del usuario*
> *Departamento de ...*

- Debajo, la firma del usuario que hace el envío.
- Adjuntos: un PDF con todas las facturas del cliente, o un PDF por factura si el cliente tiene marcada *Enviar facturas PDF en ficheros separados*.

## Si algo falla

- Los clientes sin e-mail en la ficha no entran en el envío aunque tengan marcada *Enviar facturas por email*: hay que informar su e-mail.
- Si un correo no se puede enviar (cuenta mal configurada, PDF no generado...), el cliente aparece en el resultado con el error y sus facturas **no** se marcan como enviadas: se pueden volver a enviar después.
- Los mensajes de error y su solución están en el manual de [Envío mail](../../../../../extensiones/envio_mail/index.md), apartado *Mensajes de aviso y error*.
