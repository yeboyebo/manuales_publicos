# Informe de clientes activos por código postal

## Crear un nuevo informe

* Pulsamos sobre el botón **Insertar Regristro** del formulario principal de **Area de Facturación/Informes/Clientes activos por CP**. Esto abrirá un formulario con los criterios de búsqueda el informe.
* Establecemos una descripción para nuestro informe.
* Establecemos el intervalo de fechas para la búsqueda de datos


## Exportar informe a excel

* En el formulario principal de **Clientes activos por CP** seleccionamos el imforme a generar y pulsamos el botón **Exportar a excel**. Esto generará un excel con la siguiente estructura:


## Formato del informe

* Nivel 0: Agente. Se mostrarán los agentes que hayan facturado en el período de búsqueda. Campos:
    + Código.
    + Nombre.
    + Total de clientes activos.
    + Total facturación.

* Nivel 1: Código postal. Se mostrará, para cada agente, lista de códigos postales con facturación. Campos:
    + Provincia.
    + Código postal.
    + Total de clientes activos.
    + Total facturación.

* Nivel 2: Cliente. Para cada agente y código postal, se mostrará una lista de clientes con facturación. Campos:
    + Código
    + Nombre
    + Dirección (dirección + población + código postal + país)
    + Total facturación.

El valor de _Total facturación_ será el total neto facturado en el período de búsqueda del informe.

El informe estará ordenado por código de agente, provincia, código postal, código de cliente.

Los agentes y códigos postales para los que no haya clientes activos no aparecerán en el informe.

El informe se creará en formato hoja de cálculo ODS (Open Document Sheet).


[Volver al Índice](./index.md)