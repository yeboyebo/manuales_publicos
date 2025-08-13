# Pasos para la migración

## Pasos previos

### BDs a migrar

Restaurar las BDs de ventas y compras en mysql

Configurar las cadenas de conexión en la función 'inicializar_conexiones(self)' de los scripts:
- Facturación/Principal/scripts/plus_sys_mig_***.py (Ventas) 
- Facturación/Principal/scripts/plus_sys_mig_stock.py (Compras) 

### BD de destino

Crear una BD con Eneboo cargando fun_ecofricalia y generando los datos por defecto de flfactppal, flfactalma, ...


## Migración de ventas

Activar flags de ventas del script Facturación/Principal/scripts/plus_sys_mig_ventas.py:

```py
    _flag1 = True
    ...
```

Activar conexión con ventas en función 'inicializar_conexiones(self)':

```py
     
        
```

Lanzar el proceso python: ....


## Migración de compras

Activar flags de compras del script Facturación/Principal/scripts/plus_sys_mig_stock.py:

```py  
    _procesar_proveedores = True
    _procesar_articulos_almacen = True
    _procesar_articulosprov = True
    _procesar_pedidosprov = True
    _set_generar_albaranes_prov = True

```

Activar conexión con compras en función 'inicializar_conexiones(self)':

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

Lanzar el proceso python: 
/usr/local/bin/pineboo-core -s "user:pass:PostgreSQL (PSYCOPG2)@localhost:5432/nombrebbdd" -c "plus_sys_mig_stock.main" -x


