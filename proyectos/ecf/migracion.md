# Pasos para la migración

## Pasos previos

### BDs a migrar

Restaurar las BDs de ventas y compras en mysql

Configurar las cadenas de conexión en la función 'inicializar_conexiones(self)' de los scripts:
- Facturación/Principal/scripts/plus_sys_mig_ventas.py (Ventas) 
- Facturación/Principal/scripts/plus_sys_mig_stock.py (Compras) 

### BD de destino

Crear una BD con Eneboo cargando fun_ecofricalia y generando los datos por defecto de flfactppal, flfactalma, ...


## Migración de ventas

- Crear carpeta build/final en fun_ecofricalia con eneboo-tools.
- renombrar fichero plus_sys_mig_ventas.py a plus_sys.py

- Activar flags de ventas del script ...

```py
    _flag1 = True
    ...
```

- especificar en:
```py
    - _cod_cliente_simplificada: codcliente de factura simplificada al importar facturas simplificadas.
    - _id_dir_simplificada: id_direccion de facturas simplificadas.
```
- Activar conexión con ventas en función 'inicializar_conexiones(self)' del script ... 

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

- Lanzar el proceso python: 
/usr/local/bin/pineboo-core -s "user:pass:PostgreSQL (PSYCOPG2)@localhost:5432/nombrebbdd" -c "/path/codebase/extensiones_2.5.0/fun_ecofricalia/build/final" -x

- borrar fichero plus_sys.py de la la BD.


## Migración de compras

- Activar flags de compras en el script renombrado plus_sys.py:

```py  
    _flag1 = True

```

- Activar conexión con compras en en el script renombrado plus_sys.py

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

- Lanzar el proceso python: 
  /usr/local/bin/pineboo-core -s "user:pass:PostgreSQL (PSYCOPG2)@localhost:5432/nombrebbdd" -c "/path/codebase/extensiones_2.5.0/fun_ecofricalia/build/final" -x

- borrar fichero plus_sys.py de la la BD.  


