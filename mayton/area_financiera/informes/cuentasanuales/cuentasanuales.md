# Mayton
----------------------

# Informes Cuentas Anuales

* Para el uso de los informes Cuentas anuales seguimos los pasos indicados en [Cuentas anuales](../../../../modulos/area_financiera/informes/cuentasanuales/cuentasanuales.md)

## Recálculo de datos para ejercicios abiertos
El campo *Recálculo de datos para ejercicios abiertos* indica que hay que recalcular los datos solo en caso de que el ejercicio esté abierto.

Cuando se cierra un ejercicio fiscal (ver en *  [Apertura y Cierre Ejercicio](../../../../modulos/area_financiera/principal/apertura_cierre_ejercicio/aperturacierre.md)) se actualiza el campo **Forzar recálculo** a verdadero para todos los registros que tienen como ejercicio actual o ejercicio anterior el ejercicio cerrado. Así conseguimos que los datos de los informes de los balances son actualizados para los ejercicios cerrados.

Al imprimir un informe de Cuentas anuales si esta marcado el campo **Recalcular para ejercicios abiertos** se desmarca el camo **Forzar recálculo**.