# Pruebas antes de instalación

## Pedidos

* Crear pedido
* Editar pedido
* Añadir línea
* Modificar Línea
* Borrar línea
* Enviar pedido(NO EN PRODUCCIÓN)
  * Antes cambiar el email de envío:
    ```sql
    update factppal_general set sh_mailrecepcion = 'EMAIL';
    ```
* Borrar pedido

## Presupuesto

* Crear presupuesto
* Editar presupuesto
* Añadir línea
* Modificar Línea
* Borrar línea
* Borrar presupuesto

## Preparaciones
* Carga de masters y de líneas en details

## Trato

* Crear trato, rellenano todos los campos
* Crear pedido
* Crear presupuesto y aprobarlo
* Borrar trato
* Añadir tarea
* Añadir nota
* Antes de asociar pedido borrar pedidos, presupuestos, tareas, notas y tratos creados
  ```sql
  delete from pedidoscli where idtrato in (ids);
  delete from presupuestoscli where idtrato in (ids);
  delete from ss_tareas where idtrato in (ids);
  delete from ss_notas where idtrato in (ids);
  delete from ss_tratos where idtrato in (ids);
  ```
* Asociar pedido(comprobar si el pedido ya tenía asociado un trato, al terminar actualiza pedido con el idTrato)

## Tarea(trato e incidencia)

* Crear tarea
* Editar tarea
* Completar y crear

## Contacto

* Crear contacto
* Editar contacto

  ```sql
  delete from crm_contactos where email = 'email';
  delete from ss_contactos_agente where email = 'email';
  ```
