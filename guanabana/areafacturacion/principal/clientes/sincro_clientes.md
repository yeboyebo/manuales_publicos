# Sincronización de clientes mayoristas

El objetivo de este proyecto es crear un botón desde el formulario de clientes para crear los clientes de forma automática en la tienda privada.

### Creación automática de clientes en la tienda online
Los pasos son:
* Vamos a *Facturación - Principal - Clientes* y seleccionamos el cliente a crear.
* Pulsamos el botón *Crear cliente en tienda online*.
    * Si el cliente ya está creado (tiene informado el campo *Id. Magento*), el botón esta deshabilitado.
* Aparece un mensaje en el que se nos pregunta en qué Store view queremos crear el cliente, las opciones serán:
    * USD / Inglés
    * USD / Español
    * EUR / Inglés
    * EUR / Español
* Seleccionamos un website y pulsamos *Continuar*
    * Se apunta un registro del cliente en la cola de sincronizaciones en el website seleccionado, copiando los siguientes datos de la tabla de clientes:
        * *email*
        * *Nombre y apellidos*: (se tomarán automáticamente del nombre del cliente separando por el primer espacio)
        * *CIF / VAT*
        * *Direcciones*
        * *Contraseña*: Por defecto será siempre el 'cs_' mas CIF del cliente, luego podemos entrar en Magento y cambiarla de forma manual, o pedir al cliente que lo haga.
    * El programa ejecuta automaticamente los registros de las sincronizaciónes cada 5 minutos.
    * Cuando se ha creado el cliente en la tienda online, se guarda el Id del cliente creado en el nuevo campo *Id. Magento*.


