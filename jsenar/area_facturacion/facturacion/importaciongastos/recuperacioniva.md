# Recuperación de iva

## ¿Cómo selecciono los datos a importar?

* Pulsamos sobre el botón **Importar** del formulario principal de **Area de Facturación/Facturación/Importación Gastos/Recuperación IVA**. Esto abrirá un formulario de importación.

![Formulario de importación](./img/riformimportacion.png)

* En este formulario tenemos dos formas de raalizar la importación:
    - Pulsamos el botón **Importar CSV**. Que importará los datos desde un fichero csv. Se abrirá una ventana en la que debemos especificar algunos datos como el caracter separador del fichero, si debe ignoar o no la primera línea (debe ignorarse en el caso de que la primera línea corresponda a la cabececera con los nombres de las columnas) y número de líneas adicionales a ignorar (en el caso de que quisíeramos ignorar alguna otra línea). Al aceptar el formulario debemos seleccionar en nuestro disco el fichero csv a importar.
    - O también podemos hacerlo pulsando el botón **Pegar desde Hoja Cálculo**. En esta opción se abrirá una ventana con un cuadro de texto en blanco en el que debemos pegar el contenido de la hoja de cálculo que queramos importar

* De ambas formas se leerán los datos a importar, se ejecutarán una serie de validaciones y se mostrará en el formulario de importación una lista con los datos a importar dónde nos dirá si son correctos o hay algún error.


## ¿Como veo los errores antes de hacer la importacion?

* Una vez hemos seleccionado los datos a importar. En la previsualización, si hay algún error en los datos nos lo indicará en la primera columna. Si la línea es correcta en la primera columna pondrá Correcto, pero si hay algún errro pondrá incorrecto y aparecerá en rojo. 

![Errores en formulario de importación](./img/riformimportacionerrores.png)

* Podemos mostrar únicamente los registros con errores pulsando el botón **Mostrar solo errores**

* Para saber qué error hay, hacemos doble click sobre la palabra incorrecto del registro que queramos comprobar y aparecerá un mensaje indicando el error.

* Debemos solucionar los posibles errores en el fichero csv o en la hoja de cálculo y volver a seleccionar los datos a importar.

* Para poder realizar la importación de la recuperación de iva, debe existir previamente una importación de gastos para los mismos registros. Es decir para los registros con el mismo ID AEAT. Si no es así, y algún registro de recuperación no existe en una importación de gastos aparecerá con un error

![Error de importación](./img/rierrorimpgastos.png)

* Una vez que la previsualización salga sin errores pulsamos el botón de aceptar el formulario en la parte inferior derecha


## ¿Cómo veo los datos importados?

* Al finalizar la importación quedará un registro en la tabla **Recuperación Iva** del formulario principal de **Area de Facturación/Facturación/Importación Gastos/Recuperación IVA**. Si editamos ese registro veremos que aparece una tabla con todos los datos que se han importado

![Datos importados](./img/ridatosimportados.png)

* Para cada uno de los registros importados se genera una factura de proveedor.

* Podemos ver los documentos generados seleccionando el registro correspondiente y pulsando el botón **Ver Documento** en la parte superior derecha del formulario. Esto abrirá el formulario de facturas de proveedor