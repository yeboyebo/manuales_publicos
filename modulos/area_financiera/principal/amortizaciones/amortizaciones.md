# Amortizaciones

## Crear un nuevo elemento de amortización

Para crear una nueva amortización, seguiremos los siguientes pasos:

- Vamos a _Financiera - Principal - Amortizaciones_ y pulsamos el botón _Crear_.
- En el formulario de alta, indicamos
  - _Descripción del elemento_
  - _Período de amortización_
  - _Fecha de adquisición_
  - _Valor de adquisición_ y _Valor residual_ (parte no amortizable)
  - _Grupo contable_ (ver siguiente punto)
  - _Amortización por período_, _Porcentaje anual_, etc. Estos campos actúan unos sobre otros calculando los valores correspondientes. Generalmente solo es necesario indicar Fecha Inicio y % Anual.

## Crear un grupo contable de amortización

Los elementos a amortizar de una misma naturaleza comparten un Grupo contable de amortización.

![Grupo contable ](./img/grupo_contable.png)

Para definir el grupo indicamos:

- _Subcuenta del elemento_: Subcuenta que usa el asiento de la factura de compra del elemento.
- _Subcuenta de amortización_: Subcuenta a usar en los asientos de las dotaciones como subcuenta de amortización.
- _Subcuenta de gastos_: Subcuenta a usar en los asientos de las dotaciones como subcuenta de gastos.
- _Subcuenta de pérdidas_: Subcuenta a usar en el caso de que el elemento se venda por un valor inferior a su valor no amortizado.
- _Subcuenta de ganancias_: Subcuenta a usar en el caso de que el elemento se venda por un valor superior a su valor no amortizado.

## Crear la dotación inicial (elementos con amortización en curso)

En el caso de que incorporemos al programa un elemento cuya amortización esté en curso, crearemos una partida con los siguientes datos:

- _Fecha de inicio_: Fecha de inicio de la amortización (generalmente es la Fecha adquisición)
- _Fecha fin_: Fecha hasta la que no vamos a contabilizar dotaciones. A partir de esta fecha crearemos dotaciones por cada período.
- _Importe_: Importe acumulado amortizado en todo el período Fecha Inicio - Fecha Fin.
- _Fecha asiento_: Igual a fecha inicio (no generaremos asiento)
- _Ignorar contabilidad_: **Importante** este valor debe estar activado si no queremos generar la contabilidad correspondiente al período de la dotación inicial.

![Ficha de elemento ](./img/elemento.png)

## Crear una dotación periódica manual

Para crear una nueva dotación, basta con:

- Pulsar el botón de _Crear dotación_ en el formulario del elemento.
  - El formulario se abrirá con los valores informados, calculados automáticamente a partir de los datos de la ficha del elemento con los datos relativos al siguiente período.
- Informamos la _Fecha asiento_. Este será el único dato a incluir, para la fecha en la que queramos que se cree el asiento contable.
- Guardamos el formulario.
  - Se genera automáticamente el asiento de la dotación.

![Ficha de dotación ](./img/dotacion.png)

## Carga de amortizaciones desde fichero EXCEL o CSV.

Para cargar nuevas amortizaciones desde un fichero EXCEL o CSV, seguiremos los siguientes pasos:

- Pulsar el botón de _Importar_ situado en la esquina superior derecha del formulario de amortizaciones. \* Se abrirá un nuevo formulario para la importación de datos
  ![Formulario para importación de datos](./img/FormularioImportar.png)
- Ahora podremos elegir si queremos cargar datos desde csv o desde hoja de cálculo. Pero en ambos casos los datos deben cumplir las siguientes validaciones:
  - Código: Una cadena de texto de 6 carácteres.
  - Nombre: Una cadena de texto de hasta 500 carácteres.
  - Grupo Contable: una cadena de texto de hasta 200 carácteres. **Debe existir un grupo con esta descripción en la base de datos**.
  - Fecha de adquisición: una cadena de texto de 10 caracteres que contengan la fecha en formato **dia-mes-año**.
  - Valor de adquisicion: numero con hasta 10 digitos enteros y 2 decimales, **sin utilizar separador de miles**.
  - Periodicidad: una cadena de texto de hasta 20 carácteres.
  - %Amort. Anual: Un número y un signo de % separados por un espacio.
  - Amort. Acumulada: numero de hasta 10 digitos enteros y 2 decimales, **sin utilizar separador de miles**.
  - Fecha fin amort. Acumulada: una cadena de texto de 10 caracteres que contengan la fecha en formato **dia-mes-año**.
  - Amort. Periodo: Valor de adquisicion: numero con hasta 10 digitos enteros y 2 decimales, **sin utilizar separador de miles**.

### Carga desde hoja de cálculo (EXCEL).

- Abrimos nuestra hoja de cálculo, la cuál debe contener los datos con la siguiente estructura.

![Hoja excel para importación de amortizaciones](./img/formatoCampos.png)

- Seleccionamos los datos que queremos importar de la hoja de cálculo y los copiamos al portapapeles (pulsamos _ctrl+c_, o bien hacemos _click derecho -> Copiar_)

- En el formulario de importación pulsamos el botón _Pegar desde hoja de cálculo_.
  - Se abrirá un pequeño cuádro de diálogo.
- Pegamos el contenido del portapapeles en el cuadro, (Pulsamos _ctrl+v_, o bien hacemos _click derecho -> Pegar_) y pulsamos _aceptar_ para cargar los datos.
  - Se cargarán los datos de la hoja de cálculo en la tabla del formulario.
- Si no encontramos errores, pulsamos en el botón verde de la esquina inferior derecha para cargar las amortizaciones.

### Carga de archivo CSV

#### Cómo generar el archivo

Para generar un archivo csv válido podemos hacerlo desde una hoja de cálculo. Si pulsamos en _Archivo -> Guardar como_ podemos seleccionar csv en el tipo de archivo antes de guardar.

Cuando lo hagamos, si aparece el siguiente mensaje tendremos que pulsar la opción de _Usar Formato Texto CSV_.
![Mensaje de confirmación de formato](./img/mensajeFormato.png)

Y entonces tendremos que seleccionar la configuración del archivo csv. Para que todo funcione la configuración correcta es la siguiente:
![Configuración de archivo csv](./img/configuracionCSV.png)

Si el primer mensaje no aparece al guardar el archivo como csv es porque ya se ha guardado alguna configuración previamente. Si no estás seguro de que se haya guardado con la configuración correcta puedes guardar el archivo como hoja de cálculo y luego volver a guardarlo de nuevo como CSV.

#### Carga de datos

Una vez tenemos el archivo CSV preparado, podemos continuar realizamos los siguientes pasos:

- Pulsamos el botón _Importar CSV_ del formulario.
  - Se abrirá un cuadro de diálogo para especificar el delimitador y las líneas que queremos ignorar del fichero.
- Dejamos el delimitador por defecto "|".
- Si el CSV que generamos tiene una fila de cabecera, marcamos el check para ignorar la primera fila.
- Pulsamos aceptar.
  - Se abrirá el explorador de archivos.
- Seleccionamos el archivo CSV que preparamos previamente.
  - Se cargarán los datos del archivo en la tabla del formulario.
- Si no encontramos errores, pulsamos el botón verde de la esquina inferior derecha para cargar las amortizaciones.
