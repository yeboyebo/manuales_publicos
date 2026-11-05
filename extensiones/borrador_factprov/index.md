# Borrador de facturas de proveedor (borrador_factprov)

Esta extensión hace que las facturas de proveedor se creen como **borrador**. El número definitivo, el asiento contable y los recibos solo se generan cuando el usuario pulsa el botón __Registra Factura__.

Así, varias personas pueden crear, copiar o modificar facturas de proveedor a la vez sin que el programa se bloquee.

### Funcionalidad anterior

Al crear una factura de proveedor se le asignaba el número definitivo y se generaban el asiento y los recibos. Todo eso quedaba pendiente de guardar mientras el usuario seguía editando la factura.

Si en ese momento otra persona creaba o copiaba otra factura de la misma serie, el programa le asignaba el mismo número y se quedaba esperando hasta que la primera persona aceptara o cancelara su factura.

### Funcionalidad nueva

#### 1. La factura se crea como borrador

Toda factura de proveedor nueva, se cree a mano, copiando otra desde el listado o asociando albaranes, recibe un código provisional con este formato:

`#<serie>/<identificador interno>`, por ejemplo `#A/24502`

Mientras el código empiece por `#`, la factura es un borrador:

+ Se puede modificar con normalidad: cabecera, líneas, totales.
+ No tiene número definitivo de la serie.
+ No tiene asiento contable.
+ No tiene recibos.

#### 2. Registrar la factura

Cuando la factura está completa, se registra desde el listado (formulario maestro) de facturas de proveedor:

1. Seleccionar la factura en borrador.
2. Pulsar el botón __Registra Factura__.
3. Confirmar el mensaje.

Al registrarla:

+ Se le asigna el siguiente número de la serie y el ejercicio, y su código definitivo (por ejemplo `20260A001245`).
+ Se genera el asiento contable, salvo que la factura tenga marcado _No generar asiento_.
+ Se generan los recibos según la forma de pago.
+ Si la factura mueve stock (facturas sin albarán), el concepto de los movimientos de stock pasa a mostrar el código definitivo.

Al terminar se muestra el código asignado y el listado se coloca sobre la factura registrada.

Si algo falla, por ejemplo una subcuenta sin configurar al generar el asiento, la operación se deshace entera: la factura sigue como borrador y no se consume ningún número.

El botón __Registra Factura__ solo está activo cuando la factura seleccionada es un borrador.

### A tener en cuenta

+ __Registrar antes de cerrar un periodo.__ Las facturas en borrador no aparecen en contabilidad ni en tesorería, y no se incluyen en los modelos __303__, __347__ ni __115__. Antes de presentar modelos o cerrar un periodo, hay que comprobar que no quedan borradores. En el listado se reconocen porque su código empieza por `#`.
+ __La fecha no cambia al registrar.__ Es la fecha de la factura del proveedor, y se mantiene.
+ __El orden de numeración es el de registro.__ El número se asigna al registrar, no al crear la factura.
+ __Facturas anteriores.__ Las facturas creadas antes de instalar la extensión ya tienen código definitivo y se consideran registradas. No hay que hacer nada con ellas.
+ __Borrar un borrador__ no deja huecos en la numeración, porque todavía no tenía número.
+ Una factura registrada se modifica como hasta ahora.

### Información técnica

+ Una factura es borrador cuando su campo `codigo` empieza por `#`. No hay ningún campo de estado nuevo.
+ Dependencias: `recibos_prov` y `prevision_rec`. En tesorería, la clase se coloca encima de `prevision_rec` para que tampoco se generen ni ajusten recibos de previsión mientras la factura es borrador. Al registrar se fuerza la regeneración de recibos mediante `siRegenerarRecibosPrevProv` (`prevision_rec`) y `siGenerarRecibosProv` (`recibos_prov`).
+ Funciones principales:
    + `flfacturac`: `beforeCommit_facturasprov` (código de borrador al insertar), `generarAsientoFacturaProv` (no genera asiento en borrador), `registraFacturaProv` (registro en una transacción).
    + `flfactteso`: `regenerarRecibosProv`, `siGenerarRecibosProv`, `siRegenerarRecibosPrevProv`.
    + `masterfacturasprov`: botón `pbnRegistraFactura`.
    + Modelos: `co_modelo347.whereFacturas`, `co_masterfacturacionprov347.calcularTotal` y `co_modelo115.pbnCalcularValores` / `pbnVerDetalle` excluyen los códigos `#%`.

### Más

  * [Volver al Índice](../index.md)
