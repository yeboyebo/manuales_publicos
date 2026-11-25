# Motivos de tarea

---

Los **motivos de tarea** son la lista de razones que el comercial puede elegir al programar una visita o tarea (campo **Motivo** de [Nueva visita o tarea](./nueva_tarea.md)), por ejemplo "Presentación de producto" o "Seguimiento de pedido". El motivo también forma parte del título automático de la tarea.

La lista se mantiene desde el menú lateral, en **SmartSales > Motivos de tarea**. Solo pueden crear, cambiar o borrar motivos los usuarios del grupo de **administración**; los comerciales solo los ven al crear o editar tareas.

<!-- ![Motivos de tarea](./img/motivos.png) -->
<!-- CAPTURA motivos.png: /crm/motivo_tarea con un usuario de administración, la lista de motivos y el detalle de uno abierto. -->

## Lista de motivos

Muestra todos los motivos con su **Descripción** y si están **Activos**. Al pulsar uno se abre su detalle a la derecha.

## Crear un motivo

El botón **Nuevo motivo de tarea** abre una ventana con:

| Campo           | Qué es                                                       |
| --------------- | ------------------------------------------------------------ |
| **Descripción** | El texto del motivo, tal como lo verán los comerciales.      |
| **Activo**      | Si está marcado, el motivo aparece al crear o editar tareas. |

**Guardar** lo crea; **Cancelar** cierra la ventana sin crearlo.

## Cambiar un motivo

En el detalle se pueden cambiar la **Descripción** y la casilla **Activo**. Al modificar algo aparecen los botones **Guardar** y **Cancelar**.

## Dar de baja un motivo

Para que un motivo deje de ofrecerse a los comerciales, se **desmarca Activo**: deja de aparecer al crear tareas, pero las tareas que ya lo tenían lo conservan. Al editar una de esas tareas, el motivo sigue apareciendo con su nombre y la indicación "(inactivo)", para no perderlo al guardar.

El botón **Borrar** del detalle (con confirmación) elimina el motivo definitivamente, pero solo si **ninguna tarea lo usa** (por ejemplo, uno creado por error). Si alguna tarea lo usa, no se borra y aparece el aviso «No se puede borrar el motivo de tarea "Seguimiento de pedido": hay tareas que lo usan. Desactívalo en lugar de borrarlo.» (con la descripción del motivo); en ese caso hay que desmarcar **Activo**.

[Volver al Índice](./index.md)
