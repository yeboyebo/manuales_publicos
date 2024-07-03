# Sincronización de contactos con ActiveCampaign

## Script de sincronización

El script utilizado para sincronizar se encuentra en `/home/yeboyebo/sincros/` dentro del `Sanhigia AbanQ Server` y se llama `sincro_activecampaign.sh`.

Este fichero se ejecuta mediante `crontab` cada hora (10 minutos después de en punto) y llama a dos funciones de pinebooapi:

- `synchronize_contactos_from_active_campaign_to_smartsales`
- `synchronize_contactos_from_smartsales_to_active_campaign`

## Script de API que se ejecuta

El script donde se ejecutan estas funciones es `contactos_api.py` (en la clase de SmartSales) y tiene diversas funciones que permiten traer los contactos de ActiveCampaign a Pineboo y viceversa.

## Solución de problemas

En caso de que pensemos que podemos tener problemas de sincronización, podemos hacer ciertas comprobaciones.

### Contactos no sincronizados

Para conocer si hay contactos no sincronizados, podemos lanzar esta query en postgre:

```sql
SELECT COUNT(*) FROM crm_contactos WHERE email IS NOT NULL AND idactivecampaign IS NULL AND email ~ '^[^@:\s]+@[^.\s@][^_@\s]+[^.]\.[a-z]{2,}$';
```

Y con esta otra, podemos ver cuáles son:

```sql
SELECT nombre, email, telefono1 FROM crm_contactos WHERE email IS NOT NULL AND idactivecampaign IS NULL AND email ~ '^[^@:\s]+@[^.\s@][^_@\s]+[^.]\.[a-z]{2,}$' LIMIT 5;
```

### Logs

Podemos intentar ver los logs para conocer porqué está fallando la sincronización, aunque es posible que no esté loggeando correctamente la salida de pinebooapi. Podemos ver 3 logs distintos:

- Supuestamente, `log5.txt` está almacenando toda la salida de la ejecución del fichero `.sh`
- El fichero `from_activecampaign.log` tendrá la salida de la función que sincroniza desde ActiveCampaign hasta SmartSales.
- El fichero `to_activecampaign.log` tendrá la salida de la función que sincroniza desde SmartSales hasta ActiveCampaign.

### Regexp de emails

El error más común de la sincronización se debe a que los contactos incluidos en SmartSales tienen un email (no necesariamente inválido) que ActiveCampaign no quiere/puede recibir. Por tanto, es importante jugar con el filtrado de emails de contacto.

Para ello, podemos ir a la función `get_contactos_smartsales` de `contactos_api.py` y cambiar la expresión regular. Parece difícil, pero no lo es tanto.

Se recomienda jugar con la expresión regular en las consultas SQL anteriores hasta que desaparezca el contacto que nos está causando problemas.

[Volver al Índice](./index.md)
