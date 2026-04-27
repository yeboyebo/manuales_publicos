TODO

+ Ciclo de aprobación - desaprobación
+ Ciclo de generación de evento > cola de firmas > firma (ver si postgre tiene ya algo)

```py
@dataclass(kw_only=True, frozen=True, eq=True)
class Empleado(Agregado):
    id: EmpleadoId
    empresa_id: EmpresaId
    nombre: NombreEmpleado
    dni: Dni
    supervisor_id: EmpleadoId | None

@dataclass(kw_only=True, frozen=True, eq=True)
class PausaJornada(EntidadConId):
    id: PausaJornadaId
    fechahora_inicio: FechaHoraJornada
    fechahora_fin: FechaHoraJornada | None = None

class EstadJornada(Enum):
    BORRADOR = 'BORRADOR'
    FIRMADA = 'FIRMADA'
    APROBADA = 'APROBADA'


class DatosPausaRegistroJornada(TypedDict):
    fechahora_inicio: str
    fechahora_fin: str

class DatosEventoFirmaRegistroJornada(TypedDict):
    jornada_id: str
    empleado_id: str
    fechahora_inicio: str
    fechahora_fin: str
    pausas: list[DatosPausaRegistroJornada]

@dataclass(kw_only=True, frozen=True, eq=True)
class EventoControlHorario:
    id: EventoControlHorarioId
    firma: FirmaControlHorario
    timestamp: Timestamp

@dataclass(kw_only=True, frozen=True, eq=True)
class EventoFirmaRegistroJornada(EventoControlHorario):
    datos: DatosEventoFirmaRegistroJornada

class DatosEventoAprobacionRegistroJornada(TypedDict):
    jornada_id: str
    firmante_id: str
    fechahora_firma: str

@dataclass(kw_only=True, frozen=True, eq=True)
class EventoAprobacionRegistroJornada(EventoControlHorario):
    datos: DatosEventoAprobacionRegistroJornada

@dataclass(kw_only=True, frozen=True, eq=True)
class Jornada(Agregado):
    id: JornadaId
    empleado_id: EmpleadoId
    fechahora_inicio: FechaHoraJornada
    fechahora_fin: FechaHoraJornada | None = None
    pausas: list[PausaJornada]
    estado: EstadoJornada
    eventos: list[EventoControlHorario]

```
Reglas:
+ Solo puede haber una jornada por empleado y día



Funcionalidades:

+ Comprobación de cadena de firmas
+ Generación de tablas de jornadas, etc. a partir de tabla de eventos

API:

+ Crear jornada (empleado_id, fecha_hora_inicio)
