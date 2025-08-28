# MIGRACIÓN ECOFRICALIA

## PASOS PREVIOS ANTES DE MIGRACION

1. Crear una BBDD vacía en postgresq que se llame ecofricalia

2. Cargar todos los módulos (primero sistema y luego lo demás)

3. Entrar a todos los módulos

4. Restaurar las BDs de crm y stock en mysql

5. En la funcionalidad de fun_ecofricalia, hay que configurar las cadenas de conexión en la función "inicializar_conexiones(self)" en los sritps:

	- Facturación/Principal/scripts/plus_sys_mig_ventas.py (CRM-VENTAS) 
	- Facturación/Principal/scripts/plus_sys_mig_stock.py (STOCK-COMPRAS)	
	

```py
     
                """Conecta a la bd origen y destino"""
        # self.print("Conectando a origen ... ")
        driver_mysql_name = "FLMYSQL_INNODB" # MySQL InnoDB (MYSQLDB)
        qsa.sys.addDatabase(
            driver_mysql_name,
            "nombrebbdd",
            "usuariobbdd",
            "password",
            "iporigen",
            "3306",
            "origen"

        )

        query_result = self.execute_query("SELECT current_time", "origen")
        # self.print("Conectando a destino ... ")
        driver_postgres_name = "FLQPSQL" # PostgreSQL (PSYCOPG2)
        qsa.sys.addDatabase(
            driver_postgres_name,
            "nombrebbdd",
            "usuariobbdd",
            "password",
            "ipdestino",
            "5432",
            "destino"
        )

        query_result = self.execute_query("SELECT current_time", "destino")
```

### MIGRACION CRM-VENTAS

1. Crear vista en mysql en BBDD BBDD crm

    ```
        CREATE VIEW crm_tarjetas AS
        ((select
        l.id as eco_idtarjeta,l.date_entered as  fechaalta, l.date_modified as fechamod,
        l.account_id as eco_idcliente,
        left(ltrim(CONCAT(COALESCE(l.first_name,''),' ',COALESCE(l.last_name,''))),100) AS nombre,
        CONCAT('Descripcion: ',COALESCE(l.description,' '),'\n', COALESCE(l.status_description,' '), '\nReferido por: ', COALESCE(l.refered_by,'-'), '\n', COALESCE(l.lead_source_description,' '),'\n',COALESCE(l.title,'')) as observaciones,
        COALESCE(left(l.phone_work,300), '') as telefono1,
        COALESCE(left(l.phone_mobile,300), '') as telefono2,
        COALESCE(left(l.phone_fax,300), '') as fax,
        COALESCE(left(l.primary_address_street,100), '') as direccion,
        COALESCE(left(l.primary_address_city,100), '') as ciudad,
        COALESCE(left(l.primary_address_state,100), '') as provincia,
        COALESCE(left(l.primary_address_postalcode,10), '') as codpostal,
        COALESCE(left(l.primary_address_country,2), '') as pais,
        COALESCE(left(l.refered_by,100), '') as codfuente,
        COALESCE(left(l.status,10), '') as codestado
        FROM leads l INNER JOIN accounts a ON l.account_id = a.id where l.account_id <> '')

        UNION

        (select
        l.id as eco_idtarjeta,l.date_entered as  fechaalta, l.date_modified as fechamod,
        '' as eco_idcliente,
        left(ltrim(CONCAT(COALESCE(l.first_name,''),' ',COALESCE(l.last_name,''))),100) AS nombre,
        CONCAT('Descripcion: ',COALESCE(l.description,' '),'\n', COALESCE(l.status_description,' '), '\nReferido por: ', COALESCE(l.refered_by,'-'), '\n', COALESCE(l.lead_source_description,' '),'\n',COALESCE(l.title,'')) as observaciones,
        COALESCE(left(l.phone_work,300), '') as telefono1,
        COALESCE(left(l.phone_mobile,300), '') as telefono2,
        COALESCE(left(l.phone_fax,300), '') as fax,
        COALESCE(left(l.primary_address_street,100), '') as direccion,
        COALESCE(left(l.primary_address_city,100), '') as ciudad,
        COALESCE(left(l.primary_address_state,100), '') as provincia,
        COALESCE(left(l.primary_address_postalcode,10), '') as codpostal,
        COALESCE(left(l.primary_address_country,2), '') as pais,
        COALESCE(left(l.refered_by,100), '') as codfuente,
        COALESCE(left(l.status,10), '') as codestado
        FROM leads l WHERE l.account_id = '' or account_id is null))
    ```

2. Dentro de fun_ecofricalia, vamos a final y el fichero Facturación/Principal/scripts/plus_sys_mig_ventas.py lo vamos a renombrar a plus_sys.py

3. Cargaremos final de fun_ecofricalia en nuestra bbdd de postgresql.

4. Iremos activando los flags de los distintos bloques de migración y cargando en final, podemos hacerlo en 2 pasadas:

	4.1. Primera pasada activando los flags de clientes, articulos, grupos_articulos, crm y usuarios y el resto no

    ```
	    _procesar_clientes = True
	    _procesar_tarjetas = True
	    _procesar_articulos = True
	    _procesar_grupos_articulos = True
	    _procesar_crm = True
	    _procesar_usuarios = True    
	    _procesar_albaranes = False
	    _procesar_facturas = False	   
	    _observar_forma_pago = False
	    _cod_cliente_simplificada = 'XXXXXX'
	    _id_dir_simplificada = YYYYY
    ```
	    
	4.1.2. Cargaremos final en nuestra BBDD y lanzaremos pineboo-core para que se ejecuten los procesos

    ```
		/usr/local/bin/pineboo-core -s "user:pass:PostgreSQL (PSYCOPG2)@localhost:5432/nombrebbdd" -c "/path/codebase/extensiones_2.5.0/fun_ecofricalia/build/final" -x
	```

	4.2. Después de la primear pasada, abriremos eneboo y crearemos un clientes a mano que será "Cliente factura simplificada" con una dirección.
	
	4.3. Segunda pasada, desactivamos los flags que hemos activado en la primera pasada y activamos el resto de flags que no hemos activado en la primera pasada e informamos el codcliente simplificado que hemos creado y el id de la dirección que hemos creado en sus respectivos flags. 
	
    ```	_procesar_clientes = False
	    _procesar_tarjetas = False
	    _procesar_articulos = False
	    _procesar_grupos_articulos = False
	    _procesar_crm = False
	    _procesar_usuarios = False    
	    _procesar_albaranes = True
	    _procesar_facturas = True	   
	    _observar_forma_pago = True
	    _cod_cliente_simplificada = '015031'
	    _id_dir_simplificada = 83207
	```    
	    
    4.3.1. Cargaremos final en nuestra BBDD y lanzaremos pineboo-core

    ```
		/usr/local/bin/pineboo-core -s "user:pass:PostgreSQL (PSYCOPG2)@localhost:5432/nombrebbdd" -c "/path/codebase/extensiones_2.5.0/fun_ecofricalia/build/final" -x
    ```
		
		
### DESPUÉS DE MIGRACIÓN CRM-VENTAS

1. Al cliente simplificado asignarle la serie 5 que es la de facturas simplificada.

2. Borrar fichero plus_sys.py de la la BD (vamos a modulos desde eneboo, en flfactppal lo buscamos y eliminamos).

3. Renombrar de fun_ecofricalia de final el fichero plus_sys.py a plus_sys_mig_ventas.py



### MIGRACIÓN STOCKS-COMPRAS

1. Dentro de fun_ecofricalia, vamos a final y el fichero Facturación/Principal/scripts/plus_sys_mig_stock.py lo vamos a renombrar a plus_sys.py

2. Cargaremos final de fun_ecofricalia en nuestra bbdd de postgresql.

3. Iremos activando los flags de los distintos bloques de migración y cargando en final, para esta parte como son pocos procesos podemos activarlos todos de una:

```
    _procesar_articulos_almacen = True
    _procesar_proveedores = True
    _procesar_articulosprov = True
    _procesar_pedidosprov = True
    _set_generar_albaranes_prov = True
``` 

4. Para lanzar la migración utilizaremos una llamada a pineboo-core

/usr/local/bin/pineboo-core -s "user:pass:PostgreSQL (PSYCOPG2)@localhost:5432/nombrebbdd" -c "/path/codebase/extensiones_2.5.0/fun_ecofricalia/build/final" -x

### DESPUÉS DE MIGRACIÓN STOCK-COMPRAS

1. Lanzar en nuestra BBDD de postgresql:

    ```
        update proveedores set  codserie = 'A', codpago = 'CONT', coddivisa = 'EUR';
    ```

2. Entrar en gestión documental y configurarla.

3. Borrar fichero plus_sys.py de la la BD (vamos a modulos desde eneboo, en flfactppal lo buscamos y eliminamos).

4. Renombrar de fun_ecofricalia de final el fichero plus_sys.py a plus_sys_mig_stock.py

