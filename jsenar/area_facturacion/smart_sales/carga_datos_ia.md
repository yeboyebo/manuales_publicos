# Carga de datos IA

---

## Tareas

Se ejecutan 5 scripts configurados desde crontab del usuario. Los scripts se encuentran ubicados en _/home/usuario/Documentos/RScripts/_

- **NOTA**: Para ver posbiles errores de CRON con _cat /var/mail/usuario_

### Scripts

Los scripts a ejecutar son los siguientes:

- runMyUnsupervisedLearningAndSupervisedForParentrefAndSaveInDB.R . Todos los meses, el día 2 a las 22:00.
- runSupervisedLearningForSubfamilyAndSaveInDB.R. Todos los meses, el día 3 a las 21:00.
- runMyTimeSeriesAndSaveInDB.R. Todos los meses, el día 1 a las 01:00.
- runCombinationOfSupervisedAndUnsupervisedLearningAndSaveInDB.R. Todos los meses, el dia 4 a las 23:00.
- runCorreosDataExtractionAndSaveInDB.R. Febrero, Mayo, Agosto y Noviembre, el día 4 a las 22:00.

Todos los debugs devueltos por estos scripts se guardan en _/home/usuario/Documentos/RScripts/cron.log_, junto con la hora y el script que causó el log.

[Volver al Índice](../index.md)
