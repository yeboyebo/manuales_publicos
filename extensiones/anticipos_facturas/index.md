# Anticipos facturas banco


### Configuración

Crear la cuenta especial **ANTCLI** desde **Área Financiera -> Principal -> Cuentas especiales** (si no está creada) y crear la subcuenta contable de anticipo y asociar la cuenta especial.

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
