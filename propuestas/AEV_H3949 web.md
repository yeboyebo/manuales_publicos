# #AEV #H3949 ERP Almansa Eventos

Los objetivos de este proyecto son:
+ Disponer de un ERP con las funcionalidades estándar de facturación y contabilidad.
+ Disponer de un sistema de control de eventos (planificación, estado, gastos e ingresos asociados)
+ Disponer de una App en la que consultar y crear eventos, y que terceras personas puedan consultar.

## Propuesta realizada a petición de:
Nacho

## Eventos

### CRUD de Productos (Kraken)

Zona *Rentabilidad*
+ € Ingresos: Importe económico
+ € Gastos. Importe económico
+ Margen: Resta de _Ingresos_ - _Gastos_
+ Empresa que factura. Contra la tabla de empresas.
+ Cliente: Cliente contra clientes
+ Proveedor: Proveedor contra proveedores

Zona *Seguimiento*:
+ Presupuesto: Sí/No
+ C. Cliente enviado: Sí/No
+ C. Cliente recibido: Sí/No
+ C. prov. enviado: Sí/No
+ C. prov. Recibido: Sí/No
+ Factura enviada: Sí/No
+ Hoja de  ruta hecha: Sí/No
+ Hoja de  ruta mandada: Sí/No
+ Altas SS.SS: Sí/No
+ Cartelería: Sí/No
+ Liquidación personal: Sí/No

Zona *Evento*:
+ Horario y lugar: Texto
+ CCF: Texto
+ Observaciones: Texto largo 

+ Impresión de hoja de ruta

### CRUD de Eventos (proyectos)

### Gestión documental en Eventos

### CRUD de trabajadores
    + Coste hora

### Asociar trabajadores a evento

    + Id
    + Id Trabajador.
    + Id Evento.
    + Coste. Se heredará del campo Coste en la tabla Trabajadores y será modificable.
        + Para esto incluiremos un campo _Coste_ en la tabla de _Trabajadores_.
    + `Nuevo` Fecha del evento
    + `Nuevo` Check de _Liquidado_, valor por defecto _No_.



### Trabajadores por evento (listado general)
+ Filtros por evento, fecha, trabajador
+ Exportación a excel


## App web

### Zona privada (con login y pass)
Crearemos una app web que permitirá:
+ Consultar un calendario de eventos, filtrando por año, mes (opcional) y producto.
+ Descargar un pdf / excel con el calendario consultado.
+ Crear un nuevo evento, indicando:
    + Fecha
    + Nombre
    + Cliente
    + Producto

