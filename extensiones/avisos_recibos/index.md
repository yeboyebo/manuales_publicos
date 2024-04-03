# Avisos y reclamaciones de recibos de venta
El objetivo de esta funcionalidad es avisar a los clientes de que sus recibos están próximos a vencer o han vencido ya, y llevar un control de a qué clientes se ha avisado.

### Estructura

#### Tesorería - Recibos:
Hay dos nuevos campos en Recibos de cliente:

***Aviso enviado. (Sí/No). Valor por defecto No.***

***Reclamación enviada. (Sí/No). Valor por defecto No.***
#### Tesorería - Configuración
Hay dos nuevos campos en la configuración de tesorería:

***Días aviso cobro de recibos.***

***Días reclamación cobro de recibos.***
#### Principal - Usuarios
Hay un nuevo campo en la ficha de usuario:

***Recibir avisos de cobro de recibos. (Sí/No). Valor por defecto No.***
### Dinámica
#### Avisos automáticos
Cuando un usuario que en su ficha tiene activo el check Recibir avisos de cobro de recibos abre el programa, el sistema realizará la comprobación de si hay Avisos pendientes o Reclamaciones pendientes siendo:

##### Avisos pendientes 
Hay avisos pendienes si hay recibos:
Pendientes de pago (estado Emitido)
No domiciliados
Con vencimiento anterior a la fecha de hoy + Días aviso cobro de recibos días hábiles
Que no tienen activo su check de Aviso enviado.
##### Reclamaciones pendientes.
Hay reclamaciones pendientes si hay recibos:
Pendientes de pago (estado Emitido)
No domiciliados
Con vencimiento superior a la fecha de hoy - Días reclamación cobro de recibos días hábiles
Que no tienen activo su check de Reclamación enviada.
Si hay recibos con aviso o reclamación pendiente, el usuario verá un diálogo con el siguiente texto:

	_Hay X recibos con aviso pendiente de envío_
	_Hay Y recibos con reclamación pendiente de envío_
(si X o Y son 0, esta parte del mensaje no se mostrará)

### Envío de avisos y reclamaciones.
##### Envío de avisos
Hay una nueva acción Envío avisos en tesorería, similar a Envío cliente en facturación, que permitirá asociar recibos a un envío que cumplan los criterios de Avisos pendientes, que haga el envío y que marque los recibos como Aviso enviado

##### Envío de reclamaciones
Hay una nueva acción Envío reclamaciones en tesorería, similar a Envío cliente en facturación, que permitirá asociar recibos a un envío, que cumplan los criterios de Reclamaciones pendientes, que haga el envío y que marque los recibos como Reclamación enviada


### Más

  * [Volver al Índice](../index.md)