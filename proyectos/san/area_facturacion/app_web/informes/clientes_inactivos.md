# Informe Clientes Inactivos

## ¿Qué hace este informe?

El informe **Clientes Inactivos** identifica clientes que compraron determinados artículo **antes** de una fecha de corte indicada, pero que **no han vuelto a comprarlos desde** esa fecha.

Es útil para detectar clientes que han dejado de consumir uno o varios productos concretos y orientar acciones comerciales de reactivación.

---

## Datos que muestra

### Tabla de clientes inactivos

| Columna       | Descripción                                                                                        |
| ------------- | -------------------------------------------------------------------------------------------------- |
| _(checkbox)_  | Permite seleccionar el cliente para obtener su email                                               |
| **Código**    | Código de cliente                                                                                  |
| **Nombre**    | Nombre o razón social del cliente                                                                  |
| **Dirección** | Dirección de facturación (tipo de vía + calle + número + localidad + CP)                           |
| **Teléfono**  | Teléfono de contacto                                                                               |
| **Email**     | Correo electrónico del cliente                                                                     |
| **Fecha**     | Fecha del último pedido que incluía alguna de las referencias indicadas antes de la fecha de corte |

---

## Cómo usar el informe

### 1. Indicar las referencias de artículo

En la parte superior hay tres campos de búsqueda de artículo (**Ref. 1**, **Ref. 2**, **Ref. 3**). Debes rellenar **al menos uno**. Puedes filtrar por hasta tres referencias distintas a la vez.

Al seleccionar una referencia, la etiqueta muestra entre paréntesis el código elegido para confirmar la selección.

### 2. Indicar la fecha de corte

El campo **Desde fecha** define el punto de corte temporal:

- Un cliente aparece en el informe si tiene pedidos con ese artículo **anteriores** a dicha fecha **y ninguno desde** esa fecha.
- Si un cliente ha pedido el artículo tanto antes como después de la fecha, **no** aparece en el resultado (no se considera inactivo para ese producto).

### 3. Lanzar el informe

Con al menos un artículo y la fecha rellenadas se activa el botón **Lanzar**. Al pulsarlo se carga la tabla con los clientes inactivos.

> Si el botón **Lanzar** permanece desactivado, comprueba que:
>
> - Hay al menos un artículo seleccionado.
> - La fecha de corte está informada.
> - Si el informe ya fue lanzado previamente, cambia algún parámetro o pulsa **Limpiar** primero.

### 4. Navegar por los resultados

La tabla se carga de forma progresiva mediante usando el scroll vertical. Al llegar al final del listado se cargan automáticamente los siguientes 20 registros si existen más.

Se puede **ordenar por cualquier columna** haciendo clic en su cabecera. Un segundo clic invierte el orden (ASC ↔ DESC). La ordenación solo está disponible cuando el filtro _Solo seleccionados_ no está activo.

### 5. Seleccionar clientes y obtener emails

1. Marca el **checkbox** de cada cliente que te interese.
2. Una vez hay al menos un cliente seleccionado, aparece la opción **Solo seleccionados** en la barra de acciones. Al activarla la tabla muestra únicamente los clientes marcados.
3. Pulsa el botón **Obtener emails** para abrir un diálogo con la lista de emails de los clientes seleccionados (uno por línea, separados por coma).
4. Dentro del diálogo, pulsa el icono de **Copiar** para copiar toda la lista al portapapeles y usarla en tu gestor de correo.

> Solo se incluirán en la lista los clientes que tengan email registrado.

### 6. Limpiar el formulario

El botón **Limpiar** restablece todos los filtros (referencias y fecha) y vacía la tabla de resultados. Se activa siempre que haya datos introducidos o resultados cargados.

---

## Reglas de negocio

- Se consideran **inactivos** los clientes que cumplen **ambas** condiciones simultáneamente:
  - Tienen al menos un pedido que incluye alguna de los artículos indicadas con fecha **anterior** a la fecha de corte.
  - **No** tienen ningún pedido con esos artículos con fecha **igual o posterior** a la fecha de corte.
- Solo se muestran clientes asignados a los agentes permitidos **(el agente y sus subordinados)** del usuario que está conectado.
- La **Fecha** mostrada en la tabla corresponde a la fecha del pedido más reciente con esas referencias antes de la fecha de corte.

---

## Preguntas frecuentes

**¿Por qué no aparece ningún cliente?**
Puede deberse a que todos los clientes que compraron las referencias indicadas antes de la fecha de corte han vuelto a comprarlas después, o a que no hay pedidos en ese período para los agentes asignados al usuario.

**¿Para qué sirve indicar varias referencias?**
El informe tratará como inactivo a cualquier cliente que haya comprado _al menos una_ de las referencias indicadas antes del corte y no haya repetido _ninguna_ de ellas después. Es útil para identificar inactividad en una familia o grupo de productos relacionados.

**¿El botón Lanzar está desactivado aunque tengo la fecha?**
Comprueba que hay al menos una referencia seleccionada en los campos de artículo. Ambos datos son obligatorios.

**¿Puedo usar el informe sin fecha?**
No. La fecha de corte es obligatoria; sin ella no es posible determinar qué clientes son inactivos.

[Volver al Índice](./index.md)
