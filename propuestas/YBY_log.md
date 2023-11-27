# #YBY #Log de accesos 

El objetivo de este proyecto es crear un log común para registrar los accesos de los usuarios a las distintas partes del programa.

## Estructura

### Pantalla / Log de accesos
Crearemos una nueva acción *Log de accesos*, de solo lectura.

Su tabla es:
* Id.
* Fecha
* Hora
* Usuario
* Contexto. Ejemplos: Cliente, Factura de cliente.
* Clave Contexto. Clave del contexto
* Tipo de evento. Ejemplos:
    * Alta de cliente
    * Baja de dirección
    * edit
    * edit
    * (Alta / Baja / Modificación de tablas hijas del contexto)
    * Eventos. Son eventos provocados por el usuario a tipificar (pulsación de un botón, acceso a un formulario o página web, etc.)
* Info. Información asociada al acceso. El contenido variará según el tipo de acceso:
    * Alta de registro: JSON con los datos del cursor
    * Baja de registro: JSON con los datos del cursor
    * Modificación de registro: JSON con los datos cambiados del cursor, con sus valores anterior y nuevo

## Precondiciones

## Dinámica

### Hacer X

Para hacer x:
* Vamos a ...

## Notas de desarrollo
Crear una función [] = formCURSOR.getCamposModificados(cursor)
Crear una función formCURSOR.bufferToString(cursor)
Crear una función formCURSOR.bufferChangesToString(cursor)
Crear una función formCURSOR.logEvento(cursor, tabla)

Crear una función formUTIL.logEvento(contexto, tipoAcceso, info)

CURSOR.qs
```js
logEvento(cursor, tablaContexto, idTablaContexto)
{
    const accesos = {
        0: {
            "des": "Alta de "
            "fun": formCURSOR.bufferToString
        },
        1: {

        },
        2: {

        }
    }
    const contexto = tablaContexto ? tablaContexto : cursor.table()
    const idContexto = idTablaContexto ? idTablaContexto : cursor.valueBuffer(PK)
    const tipo = accesos[cursor.modeAccess()]["des"] + " " + cursor.table()
    const info = accesos[cursor.modeAccess()]["fun"](cursor)
    formUTIL.logEvento(contexto, idContexto, tipo, info)
}
```

en afterCommit:
```js
_i.logEvento(cursor, contexto, idContexto)
oficial_logEvento(cursor, tablaContexto:optional, idContexto:optional)
{
    if (!_i.tablaEnLog(cursor.table())) {
        return
    }
    formCURSOR.logEvento(cursor, contexto, idContexto)
}
oficial_tablaEnLog(tabla)
{
    if (!_i.tablasEnLog_) {
        _i.tablasEnLog_ = _i.getTablasEnLog()
    }
    return tabla in _i.tablasEnLog_
}
oficial_getTablasEnLog()
{
    return {
        "facturascli": true,
        // ...
    }
}
```


