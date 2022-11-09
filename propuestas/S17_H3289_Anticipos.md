# #H3289 Anticipos de facturas

El objetivo de este proyecto es incluir en el ERP la información de de facturas anticipadas por el banco, así como la generación de los asientos contables relacionados.

## Estructura

### Anticipos de facturas
Crearemos una nueva acción en *Facturación - Tesorería* llamada *Anticipos de facturas*. Los campos de esta tabla son:
* Id.
* Cuenta bancaria.
* Subcuenta de anticipos de cliente, por defecto la subcuenta marcada con la cuenta especial *ANTCLI* (438.0).
* Empresa. Por defecto la del ejercicio actual.
* Fecha.
* Asiento contable.
* Total.

El formulario de Anticipos de facturas será similar al de remesas, en el sentido de que podremos seleccionar uno o más recibos y estos se asociarán al registro de anticipo de facturas.

### Recibos de venta
Crearemos nuevos campo en recibos de venta:
* Id. Anticipos de facturas.
* Anticipado. Posibles valores:
    (vacío). El recibo no se ha anticipado.
    Pendiente. El recibo se ha anticipado y está pendiente de devolver al banco.
    Hecho. El recibo se ha anticipado y se ha devuelto al banco.
* Fecha de devolución anticipo. Fecha. Indica la fecha en la que se ha devuelto el recibo al banco.
* Id. Asiento devolución.

Formulario:
* Nueva pestaña Anticipo
    * Habilitada solo si el recibo está incluido en un anticipo de recibos.
    * Contiene:
      * Campo Anticipado
      * Campo Fecha de devolución. Solo activa si Anticipado = Hecho
      * Tabla de asiento de devolución
    * Validación:
        * Si *Anticipado* es *Hecho*, *Fecha devolución* debe estar informada.
    * Cálculos:
        * Si *Anticipado* es *Pendiente*, *Fecha devolución* se borra.

## Dinámica

### Crear el registro de Anticipo de facturas
* Vamos a *Facturación - Tesorería - Anticipos de facturas* y pulsamos Crear.
    * Se abre el formulario de inserción de anticipos de facturas.
* Indicamos banco, fecha y modificamos, si es necesario, la subcuenta de anticipos a cliente.
* Pulsamos el botón de asociar recibos.
    * Se abre el formulario de selección de recibos.
* Seleccionamos los recibos y pulsamos Aceptar.
    * Los recibos asociados se asocian al anticipo y marcan su campo *Anticipado* a valor *Pendiente*.
* Comprobamos el total y opcionalmente, sacamos o incluimos más recibos con los botones Incluir / Sacar recibo.
* Guardamos el registro.
    * Se genera un asiento por el total del registro a las subcuentas del banco y a la indicada como subcuenta de anticipos de cliente.

### Indicar la devolución de un anticipo de recibo
* Vamos a *Facturación - Tesorería - Recibos de cliente* y seleccionamos el recibo a marcar como devuelto.
    * Se abre el formulario de recibos de venta.
* Vamos a la pestaña *Anticipo*.
* Modificamos el estado de *Pendiente* a *Hecho*, e indicamos la fecha de devolución.
* Guardamos el recibo.
    * Se genera un asiento en *Id. Asiento devolución* por el importe del recibo que va de la subcuenta de anticipos del anticipo asociado a la cuenta de banco del anticipo asociado.

### Eliminar la devolución de un anticipo de recibo
* Vamos a *Facturación - Tesorería - Recibos de cliente* y seleccionamos el recibo a marcar como devuelto.
    * Se abre el formulario de recibos de venta.
* Vamos a la pestaña *Anticipo*.
* Modificamos el estado de *Hecho* a *Pendiente*.
    * La *Fecha de devolución* se borra.
* Guardamos el recibo.
    * Se elimina el asiento de *Id. Asiento devolución*.


## Notas de desarrollo
Crear extensión anticipos_facturas_banco
