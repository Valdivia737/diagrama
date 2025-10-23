
# Documentacion modelo ERD empresa retail!

Este modelo entidad–relación representa la estructura de datos de un sistema de ventas, que gestiona información de clientes, tiendas, productos, proveedores y promociones. Su objetivo es permitir el análisis de ventas por cliente, producto, tienda y/o período temporal, facilitando además la trazabilidad de proveedores y promociones aplicadas.


## Entidades y Atributos

#### Entidad: **CLIENTE**
**Descripcion**: Almacena los datos de los clientes que realizan compras.


| **Campo** | **Tipo**     | **Descripcion**                |
| :-------- | :------- | :------------------------- |
| RUT | PK | Identificador unico del Cliente. |
| ID_DIRECCION | FK | Referencia a la tabla DIRECCION. |
| NOMBRE_CLIENTE| VARCHAR2 | Nombre completo del Cliente. |
| GENERO | VARCHAR2 | Genero del Cliente. |
| EDAD | VARCHAR2 | Edad del Cliente. |

#### Entidad: **PRODUCTO**

**Descripcion**: Registro de los productos disponibles para su venta.

| **Campo** | **Tipo**     | **Descripcion**                |
| :-------- | :------- | :------------------------- |
| ID_PRODUCTO | PK | Identificador unico del Producto |
| NOMBRE_PRODUCTO | VARCHAR2 | Nombre comercial del Producto |
| CATEGORIA| VARCHAR2 | Categoría o tipo de Producto (por ejemplo: electrónica, alimentos, ropa, etc.). |
| MARCA | VARCHAR2 | Marca o fabricante del Producto. |
| PRECIO | NUMERIC | Precio unitario de venta del Producto. |


#### Entidad: **PROMOCION**

**Descripcion**: Registra las promociones o descuentos aplicables a las ventas.

| **Campo** | **Tipo**     | **Descripcion**                |
| :-------- | :------- | :------------------------- |
| ID_PROMOCION | PK | Identificador unico del Producto |
| DESCRIPCION | VARCHAR2 | Detalle o nombre de la promoción. |
| TIPO_PROMOCION| VARCHAR2 | Clasificación de la promoción (por ejemplo: porcentaje, descuento fijo, 2x1, etc.). |
| FECHA_INICIO | DATE | Fecha de inicio de la promoción. |
| FECHA_FIN | DATE | Fecha de término de la promoción. |


#### Entidad: **VENTAS**

**Descripcion**: Registra las transacciones de venta, vinculando clientes, productos, tiendas,
proveedores y promociones.

| **Campo** | **Tipo**     | **Descripcion**                |
| :-------- | :------- | :------------------------- |
| ID_VENTAS | PK | Identificador único de la venta. |
| ID_CLIENTE | FK | Cliente asociado a la venta. |
| ID_PROPDUCTO | FK | Producto vendido. |
| ID_TIENDA | FK | Tienda donde se realizó la venta. |
| ID_PROVEEDOR | FK | Proveedor del producto vendido. |
| ID_PROMOCION | FK | Promoción aplicada (puede ser nula). |
| ID_FECHA | FK | Fecha de la venta. |
| CANTIDAD | INTEGER | Número de unidades vendidas. |
| TOTAL_VENTA | DECIMAL | Monto total de la venta. |



#### Entidad: **VENTAS**

**Descripcion**: Registra las transacciones de venta, vinculando clientes, productos, tiendas,
proveedores y promociones.

| **Relacion** | **Entidades**     | **Tipo**     | **Descripcion**                |
| :-------- | :------- | :------- | :------------------------- |
| CLIENTE - DIRECCION | CLIENTE (N) – DIRECCION (1) | Muchos a uno. | Cada cliente está asociado a una única dirección. |
| TIENDA – DIRECCION | TIENDA (N) – DIRECCION (1) | Muchos a uno. | Cada tienda se encuentra en una única dirección. |
| VENTAS – CLIENTE | VENTAS (N) – CLIENTE (1) | Muchos a uno. | Cada venta pertenece a un cliente específico. |
| VENTAS – PRODUCTO | VENTAS (N) – PRODUCTO (1) | Muchos a uno. | Cada venta incluye un producto determinado. |
| VENTAS – PROVEEDOR | VENTAS (N) – PROVEEDOR (1) | Muchos a uno. | Cada producto vendido proviene de un proveedor. |
| VENTAS – FECHA | VENTAS (N) – FECHA (1) | Muchos a uno. | Cada producto vendido proviene de un proveedor. |
| VENTAS – PROMOCION | VENTAS (N) – PROMOCION (1) | Muchos a uno. | Identifica si la venta está asociada a una promoción. |

