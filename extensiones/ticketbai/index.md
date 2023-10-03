# Manual TicketBAI

## ¿Donde puedo configurar el garante TicketBAI?

* El Garante TicketBAI se puede configurar el la pestaña **servidor** de **Area de Facturación/Principal/Configuración**. El servidor se encargaŕa de firmar digitalmente las facturas nuevas y anularlas, además de mantener la cadena garante.

![Configuración garante TicketBAI](./img/config.png)



## ¿Como puedo firmar una factura?

* Por defecto las facturas se crean en modo borrador. Este modo nos permitirá modificar la factura, hasta que la consideremos definitiva. 

![Estado borrador de una factura](./img/estado_borrador.png)

* Para firmar una factura. Seleccionamos la linea de esta y pulsamos sobre el botón **Firmar**. Nos mostrará un diálogo donde confirmaremos la inteción de firmar la factura.

![Diálogo firmar factura](./img/dialogo_firma.png)

*  La factura antes de ser enviada a firmar, pasara a estado *Pte.Firma*. 

![Estado pendiente firma de una factura](./img/estado_pendiente_firma.png)

* Este proceso durará unos segundos y nos cambiará el estado de una factura. Si la factura se firma correctamente pasará a estado *Firmado*. 

![Diálogo firma satisfactoria](./img/dialogo_firma.png)

![Estado firmado](./img/estado_firmado.png)

* De lo contrario , mostrará un error y pasara a estado *Error firma*.

![Diálogo error firma](./img/dialogo_error_firma.png)

![Estado error firma de una factura](./img/estado_error_firma.png)


## ¿Como puedo anular una factura?

* Ya que no podemos modificar facturas una vez firmadas, tenemos que anular las facturas con un proceso similar al usado para la firma, pero esta vez,  creando una anulación.

* Pulsaremos sobre el botón **Anular**. Estço cambiará nuestra factira al estado *Pte.Anulación*.



![Botón anular](./img/boton_anular.png)

* Nos mostrará un diálogo donde confirmaremos la inteción de anular la factura.

![Diálogo firmar factura](./img/dialogo_anular_factura.png)

* La factura antes de ser anulada cambiará estado *Pte.Anulación*

![Estado pendiente anulación](./img/estado_pendiente_anulacion.png)

* Este proceso durará unos segundos y nos cambiará el estado de una factura. Si la factura se anula correctamente cambiará de estado a *Anulado*. 

![Estado anulado](./img/estado_anulado.png)

* De lo contrario, mostrará un error y pasará a estado *Error Anulación*

![Estado error anulación](./img/estado_error_anulacion.png)


## ¿Donde puedo cambiar los datos de la factura relacionados con TicketBAI?

* Mientras la factura esté en modo borrador, podremos realizar cambios en la **pestaña Ticket BAI**.

![Pestaña facturascli ticketbai](./img/ventana_facturascli_ticketbai.png)


## ¿Como puedo ver si una factura está firmada?

* En la pantalla de **Garante SIGN** , podemos ver la información relacionada con las firmas y anulaciones de facturas. En la parte de abajo encotramos información de la cadena garante que valida que no ha sido alterada, ninguna factura una vez firmada.

![Entrada garante tbai](./img/arbol_garante.png)
![Pestaña garante tbai](./img/pantalla_garante.png)

* También disponemos de opciones para exportar firma o anulación de una factura en formato xml.

![Opciones exportar](./img/opcion_exportar.png)


