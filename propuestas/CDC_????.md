# #CDC #H**** Actualizaciones en migración, equipos y tesorería

El objetivo de este proyecto es:

- Mover la base de datos a un nuevo equipo e instalar el cliente de Eneboo en dicho equipo y otro más.
- Desarrollar algunas mejoras en recibos de cliente / proveedor
- Actualizar la contabilidad de los tiques anteriores al segundo trimestre

## Cambios a realizar

### Equipos

- Instalaremos linux, el gestor de base de datos (PostgreSQL) y Eneboo en el nuevo servidor.
- Instalaremos el cliente de Eneboo en el ordenador que se usará como TPV, y configuraremos si es necesario la impresora de tiques.

### Datos

- Generaremos los asientos contables de los pagos de facturas correspondientes a tiques de 2023 que todavía no tengan generada esta contabilidad.

### Tesorería

- Incluiremos un campo _Total_ en la cabecera del formulario maestro de recibos de cliente / proveedor para mostrar:
  - Importe total
  - Importe pagado
  - Importe pendiente

## Notas de desarrollo
``` sql
select r.codcliente, r.fecha, r.nombrecliente from reciboscli r inner join pagosdevolcli p on r.idrecibo = p.idrecibo left outer join co_asientos a on p.idasiento = a.idasiento where a.idasiento is null and r.fecha >= '2023-01-01' order by r.codcliente, r.fecha;
fun_crema=# select r.codcliente, r.fecha, r.nombrecliente from reciboscli r inner join pagosdevolcli p on r.idrecibo = p.idrecibo left outer join co_asientos a on p.idasiento = a.idasiento where a.idasiento is null and r.fecha >= '2023-01-01' AND not p.nogenerarasiento order by r.codcliente, r.fecha;
```

Usar señal _refreshed_ en punto de tesorería.

## Precio

#CDC #H**** Cambios en equipos: 120

#CDC #H**** Cambios en datos: 60

#CDC #H**** Cambios en tesorería: 120
