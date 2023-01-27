# Casación banco norma 43

Esta extensión permite importar los movimientos bancarios desde ficheros de norma 43 y realizar de forma semiautomática su asociación a distintos elementos del módulo de tesorería y contabilidad (recibos pendientes, remesas, asientos, etc.)

## Configuración

Crear la Cuenta Bancaria desde **Área de Facturación -> Principal -> Cuentas Bancarías** (si no está creada) y crear su subcuenta contable.

## Carga de ficheros
Para cargar ficheros de movimientos, seguiremos los siguientes pasos:

1. Vamos a **Área de Facturación -> Tesorería -> Importar Norma 43: Conciliación Bancaria**. Desde ahi se creará el registro de importación del fichero norma43.
1. Algunos datos como ejercicio, usuariom, fecha de importación y tipo de fichero se van a informar al iniciar el formulario. Faltará informar el banco y la descripción de la importación. Una vez informados desde el botón **Importar** seleccionamos el fichero de importación. Una vez importado veremos en la tabla del formulario el registro creado.
1. Guardar el formulario.

## Ventana de casación
Accedemos a la ventana de casación desde **Área de Facturación -> Tesorería -> Norma 43: Procesar Movimientos**
Desde el bóton **Seleccionar la cuenta bancaria** informamos la cuenta bancaría desde cual vamos a casar movimientos. Una vez informados lso campos de fecha (desde - hasta) podemos usar el botón **Importar movimientos** para cargar la tabla **Movimientos** .
Tenemos la opción de filtrar los moviminetos por varios criteriós.
La segunda tabla en la pantalla tiene varias pestañas. Por defecto están habilitadas la de **Recibos de clientes**, **Remesas de clientes** y **Asiento directo a Subcuenta**. Según de la extensiones de Eneboo que tenga el cliente se habilitan las demas pestañas. 

### Casación de recibos pendientes (cliente y proveedor)
Los pasos para casar los recibos son:

1. Seleccionamos el movimiento de la tabla **Movimientos** y también el recibo deseado. Una vez hecho con el botón **Asociar** se va a crear el pago del recibo y su correspondiente asiento contable. 
1. Para desacociar un movimiento solo es necesario seleccionarlo y ir el botón **Desacociar**. Si queremos dejar unos movimientos sin asociar se puede usar el botón **No asociar**.
1. Si el importe del recibo es menor que el importe del recibo, al asociar el movimiento el recibo se divide a dos. El primero por el importe del movimiento y el segundo con la diferencia. El pago se crea automaticamente para el primer recibo.

### Resto de casaciones implementadas
1. Casación de **Remesas de clientes**. El proceso es simular de los recibos con la diferencia que aqui el importe (HABER) del movimiento debe de coincidir con el total de la remesa para que se puede casar el movimiento.
1. Casación de **Asiento directo a Subcuenta**. El proceso es simular. Al click del botón **Asociar** se abrirá formulario de revisar los datos de la subcuenta selecionada y el concepto del asiento. Al guardar el formulario se creará asiento. Tenemos que estar en el mismo ejercicio que son los movimientos bancarios para que se cargan las subcuentas correctas.


