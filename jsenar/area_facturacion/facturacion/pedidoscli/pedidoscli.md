# Pedidos de cliente

## Estructura

### Campo estado
El valor del campo no se calcula para los pedidos de agrupación o que están en una agrupación a Canarias.

El valor del estado es, por orden de priodidad:

* **Borrador / Borrador con promoción** si el pedido está siendo generado por un comercial.

* **Pagos pendientes** si el cliente tiene pagos pendientes

* **Forma de pago bloqueada** si la forma de pago del pedido tiene activado el check *Bloqueo de pedido*.

* **Aplicar código aduanas** si la dirección del pedido es de Canarias (por código postal o código de provincia).

* **Bloqueado Riesgo** si el cliente está bloqueado por riesgo.

En las preparaciones de pedido, solo se ven los pedidos con estado...




