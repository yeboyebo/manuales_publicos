# Creación de centros de coste

## Configuración

Podemos crear los centros de coste en Área de Facturación -> Principal -> Más -> Centros de coste

![crear_centroscoste](./img/crear_cc.png)

## Crear centros y subcentros de coste

Creamos un nuevo centro de coste, dentro de los centros de coste podemos crear uno o varios subcentros de coste que se asociarán únicamente al centro de coste desde el cual estan siendo creados.

![crear_subcentroscoste](./img/crear_centro_subcentro.png)

## Crear criterios de distribución

Podemos crear criterios de distribución e informar las subcuentas y los pesos con los que se repartirá los importes en las diferentes partidas.

![criterio_pesos](./img/criterio_distribucion_pesos.png)
![criterio_subcuentas](./img/criterio_distribucion_subcuentas.png)

Una vez informados los centros de coste y los criterios de distribución, al crear una factura de cliente o proveedor el funcionamiento seria el siguiente.

## Facturas de cliente

En las facturas de cliente, tenemos la posibilidad de informar los centros de coste y subcentros de coste en las líneas, en caso de haberlos informado, se crearán partidas en el asiento con las líneas agrupadas por centro y subcentro de coste, ejemplo:

### Ejemplo 1

Si tenemos 2 líneas con el mismo centro y subcentro de coste, se creará una partida con el importe de la suma de de las dos líneas en la subcuenta de venta 700.

![ejemplo_facturacli_1](./img/ejemplo_factcli_1.png)

Si hay líneas con diferentes centros de coste se crearán tantas partidas de venta como agrupaciones se encuentren de centro y subcentro, ejemplo:

### Ejemplo 2

Tenemos 3 líneas, dos de ellas tienen mismo centro y subcentro, la otra tiene un centro y subcentro diferente. En este caso se crearán dos partidas, la primera agrupara las dos líneas con mismo centro y subcentro y la segunda la línea con centro y subcentro diferente a las otras dos.

![ejemplo_facturacli_2](./img/ejemplo_factcli_2.png)

Por otra parte, en caso de que tuvieramos instalada también la extensión de cuentas de venta en artículos, podría darse el caso de que la línea de la factura tuviera informada una subcuenta de venta diferente de la 700, esto implica que la agrupación para la generación de partidas tendría en cuenta también el código de subcuenta.

### Ejemplo 3

Si una de las líneas de la factura anterior tuviera informada una subcuenta, en este caso una de las que tenían mismo centro y subcentro, se crearían 3 partidas.

![ejemplo_facturacli_3](./img/ejemplo_factcli_3.png)

### Ejemplo 4

El último caso que se nos podría dar en facturas de cliente es que alguna de las líneas no tuviera informado ni el centro ni el subcentro de coste, por lo tanto no sabríamos a que centro/subcentro incluir esa partida.

Aquí es donde se tienen en cuenta los criterios de distribución explicados en un apartado anterior. Si existe un criterio de distribución el cual tenga incluida una subcuenta que incluya la partida que se esta creando donde no sabemos el centro de coste, el centro/subcentro de coste se buscará en este criterio y se crearán tantas partidas como registros de pesos tenga dividida con los importes según los porcentajes informados.

![ejemplo_facturacli_4](./img/ejemplo_factcli_4.png)

## Facturas de proveedor

Los posibles casos de facturas de proveedor son similares a las facturas de cliente.