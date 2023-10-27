# Firma de contratos

La firma de contratos se realiza de forma interactiva a través de una API de terceros.

## Prerrequisitos
* Debemos disponer del contrato a firmar en formato PDF
* Para el empleado del contrato, debemos tener informado su email y teléfono en su ficha.

## Envío para firmar
* Vamos a Recursor Humanos > Principal > Contratos, seleccionamos el contrato a firmar y pulsamos (botón carpeta azul).
* Seleccionamos el fichero con el documento PDF del contrato.
    * Se lanza el proceso de forma y el campo (X) del contrato pasa a estado (X)

## Firma del contrato por parte del empleado
+ El empleado recibe en su email un correo indicando que tiene un documento para firmar.
+ Pulsa en el enlace de firma y sigue las instrucciones para realizarla (describir).
+ El contrato cambia su estado de firma a (X).

Ver flrrhhppal.qs para quitar el string "Andres" del envío y ver si podemos cambiar "Test.pdf" a "(código de contrato).pdf"

## Inicio de la firma de un documento ya asociado al contrato
Podemos iniciar el proceso con el (segundo botón)...

## Actualización del estado de firma
Podemos consultar a la API de firma el estado de firma de un contrato con el botón (tercer botón).

