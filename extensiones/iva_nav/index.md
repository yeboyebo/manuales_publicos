# Gestión contable de IVA Navision Style

### Objetivo

Los consumidores y las empresas pagan el impuesto sobre el valor añadido (IVA) cuando compran mercancías o servicios. El importe de IVA a pagar puede variar, dependiendo de varios factores. En la extensión IVA_NAV, puede configurar el IVA para especificar las tasas que se usarán para calcular los importes de impuesto a partir de lo siguiente:

   * A quién vende
   * A quién compra
   * Qué vende
   * Qué compra

### Para configurar grupos contables de IVA
Conviene utilizar códigos que sean fáciles de recordar y que describan el tipo, como SIN IVA o Cero, IVA10 o Reducido para el IVA del 10 % e IVA21 o General para el 21 %.
1. Ir a **Área de Facturación -> Principal -> Impuestos**
2. Pulsaremos sobre el botón de *Insertar registro*
3. Rellenemos los campos según sea necesario.



### Para configurar grupos de registro de IVA de negocio

* El grupo de registro de IVA de negocio debería representar los mercados en los que trabaje con clientes y proveedores, y definir cómo calcular y registrar el IVA en cada mercado. Ejemplos de grupos de registro de IVA de negocio son Nacional y Unión Europea (EU).

Use códigos fáciles de recordar y que describan el grupo de registro de negocio, como UE, No UE o Nacional. El código debe ser único. Puede configurar tantos códigos como desee, pero no puede aparecer el mismo código más de una vez en una tabla.

Para configurar un grupo de registro de IVA de negocio, realice los pasos siguientes:
1. Ir a **Área Financiera -> Principal -> Mas -> Grupos contables -> Grupos I.V.A negocio**
2. Pulsaremos sobre el botón de *Insertar registro*
3. Rellenemos los campos según sea necesario.

### Para configurar grupos de registro de IVA de producto

Los grupos de registro de IVA de producto representan los productos y los recursos que compra o vende, y determinan cómo se calcula y se registra el IVA en función del tipo de producto o que se adquiera o se venda.


Para configurar un grupo de registro de IVA de producto, realice los pasos siguientes:

1. Ir a **Área Financiera -> Principal -> Mas -> Grupos contables -> Grupos I.V.A producto**
2. Pulsaremos sobre el botón de *Insertar registro*
3. Rellenemos los campos según sea necesario.

### Combinar grupos de registro de IVA producto en configuraciones de registro de IVA de negocio

La extensión calcula los importes de IVA de ventas y compras en función de las configuraciones de registro de IVA, que son combinaciones de grupos de registro de IVA de negocio y de producto. En cada combinación puede especificar el porcentaje de IVA, el tipo de cálculo del IVA y las cuentas de contabilidad para el registro del IVA de ventas, compras y los cargos invertidos. 

Configuremos tantas combinaciones como necesitemos.
Para combinar las configuraciones de registro de IVA, realicemos los pasos siguientes:

1. Ir a **Área Financiera -> Principal -> Mas -> Grupos contables -> Grupos I.V.A producto**
2. Pulsaremos sobre el botón de *Modificar registro*
3. Creamos registros en la tabla *Subcuentas por grupo de negocio*
4. Rellenemos los campos según sea necesario.

### Combinar grupos de registro de IVA negocio en configuraciones de registro de IVA de producto

Para combinar las configuraciones de registro de IVA, realicemos los pasos siguientes:

1. Ir a **Área Financiera -> Principal -> Mas -> Grupos contables -> Grupos I.V.A negocio**
2. Pulsaremos sobre el botón de *Modificar registro*
3. Creamos registros en la tabla *Configuración por grupo IVA de producto*
4. Rellenemos los campos según sea necesario.

### Para asignar grupos de registro de IVA a clientes y proveedores
1. Ir a **Área de Facturación -> Principal -> Clientes o Proveedores**
2. Pulsaremos sobre el botón de *Modificar registro*
3. Desde la pestaña *Contabilidad* rellenemos el campo *Grupo IVA negocio* según sea necesario.

### Para asignar grupos de registro de IVA a productos
1. Ir a **Área de Facturación -> Almacén -> Artículos**
2. Pulsaremos sobre el botón de *Modificar registro*
3. Desde la pestaña *Contabilidad* rellenemos el campo *Grupo Producto* según sea necesario.