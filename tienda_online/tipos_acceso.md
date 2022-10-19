# Tipos de acceso

## Precondiciones
Debemos tener dos grupos creados en la tabla de grupos del ERP:
* *GUESTS*: Será el grupo de visitantes sin identificar
* *CUSTOMERS*: Será el grupo de clientes registrados

Debemos tener al menos también un usuario de la tabla *Usuarios* del ERP que esté marcado como *superusuario*.

Debemos eliminar el acceso del grupo GUESTS a la regla de *Area de clientes > Puede acceder al área de clientes en tienda online*.

## Acceso como invitado
Nos da acceso a la tienda como miembro del grupo *GUEST*. No hay acceso a la zona de clientes (mis pedidos, etc.)

## Acceso como cliente registrado
Nos da acceso a la tienda como miembro del grupo *CUSTOMERS*. No hay acceso a la zona de clientes (mis pedidos, etc.)

Los clientes se validan contra el email y password de la tabla de clientes.

## Acceso como administrador
Nos da acceso a la tienda como administrador.

Debemos entrar en la URL */admin*

Los usuarios se validan contra el usuario y password de la tabla de usuarios, solo se permite acceder a aquellos que son administradores.



