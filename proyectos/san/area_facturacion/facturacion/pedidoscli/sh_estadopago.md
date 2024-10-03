# Pedidos de cliente


### Campo estado pago


### El valor del estado es, por orden de prioridad:

* **Cliente no registrado** si el pedido no tiene informado el campo **Código de cliente**.

* **Borrador / Borrador con promoción** si el pedido está siendo generado por un comercial.

* **Pagos pendientes** si el cliente tiene pagos pendientes

* **Forma de pago bloqueada** si la forma de pago del pedido tiene activado el check *Bloqueo de pedido*.

* **Aplicar código aduanas** si la dirección del pedido es de Canarias (por código postal o código de provincia).

* **Bloqueado Riesgo** si el cliente está bloqueado por riesgo.

* **Pendiente validar PA** si la forma de pago del pedido es PA (Pago Anticipado).

* **Devolucion por preparar / Devolucion preparada / Devolucion aprobada** si el pedido es una devolución.

* **Pte. revision observaciones** Este valor se activará cuando el pedido tenga observaciones y no esté en ningún otro estado. Será el estado menos prioritario.

Al aprobar un presupuesto sin código de cliente establecido, el valor del campo estado pago del pedido generado se informa con el valor **Cliente no registrado**.

### App / preparación de pedidos
En las preparaciones de pedido, no se mostrarán y no se podrán preparar los pedidos con estado de pago:

* **Cliente no registrado**.
* **Borrador / Borrador con promoción**.
* **Pagos pendientes**.
* **Forma de pago bloqueada**.
* **Aplicar codigo aduanas**.
* **Bloqueado Riesgo**.
* **Pendiente validar PA**.
* **Devolucion por preparar**.
* **Devolucion preparada**.
* **Devolucion aprobada**.
* **Pte. Validacion promocion**.
* **Pte. revision observaciones**.
