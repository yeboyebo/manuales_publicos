# Manual Reglas de acceso

## ¿Dónde puedo configurar las reglas de acceso?

  * Las **reglas de acceso** se configuran a nivel de grupo, esto quiere decir que para cada grupo debemos decidir a que reglas se le permite acceder.

  * Por lo tanto, las configuraremos en la **pantalla de Grupos** a través del menú de usuario (arriba a la derecha) pulsando en Administración/Grupos.

  * En las siguientes secciones veremos como hacerlo

## ¿Qué valores pueden tener las reglas de acceso?

  * Solamente hay 3 valores posibles: permitido, prohibido y no informado.

  ![Permitido](./img/permiso-true.png)
  ![Prohibido](./img/permiso-false.png)
  ![No informado](./img/permiso-noinf.png)

  * `Permitido` y `Prohibido` se explican por sí solos.

  * `No informado` permite utilizar el valor de un nivel superior, para no tener que informar cada regla en cada grupo

## ¿Cuáles son los niveles de reglas?

  * **Nivel 1: Regla esplícita**. (Ej: Pedidos de cliente / Modificación). En este nivel podemos permitir/denegar el acceso a **una acción concreta** de un modelo.

  * **Nivel 2: Regla de modelo**. (Ej: Pedidos de cliente). En este nivel podemos permitir/denegar el acceso a **todas las acciones** no informadas de un modelo.

  * **Nivel 3: Regla general de grupo**. (Ej: Acceso general). En este nivel podemos permitir/denegar el acceso a **todas las acciones y modelos** no informados.

  * **Nivel 4: Regla general de aplicación**. (Permitido por defecto). En este nivel podemos permitir/denegar el acceso a **todas las acciones y modelos** no informados **de todos los grupos**.

## Caso real

  * Queremos saber si un usuario perteneciente a un grupo X tiene acceso a crear presupuestos. Para ello, se van a comprobar todas las reglas para este grupo X por niveles:

  * Nivel 1: Presupuestos de cliente / Creación. Si está permitido, podrá crearlo, si está prohibido, no podrá. En caso de no estar informado, pasamos al nivel 2.

  * Nivel 2: Presupuestos de cliente. Si está permitido, podrá crearlo, si está prohibido, no podrá. En caso de no estar informado, pasamos al nivel 3.

  * Nivel 3: Acceso general del grupo. Si está permitido, podrá crearlo, si está prohibido, no podrá. En caso de no estar informado, pasamos al nivel 4.

  * Nivel 4: Acceso global. Si está permitido, podrá crearlo, si está prohibido, no podrá.