# Pizzeria
La pizzería “Sabor Italiano” lleva 11 años ofreciendo pizzas artesanales y un servicio de calidad. Con el crecimiento del negocio, sus dueños decidieron implementar un sistema automatizado para mejorar la gestión de ventas, inventarios y atención al cliente. Esta decisión busca optimizar los procesos y adaptarse a las nuevas tecnologías sin perder la esencia que los caracteriza.

# Entidades 
Usuarios (id, nombre, apellido, correo, contraseña, rol)      
Clientes (id, nombre, apellido, telefono, direccion)            
Productos (id, nombre, descripcion, precio, stock)         
Ventas (id, fecha, total, id_usuario, id_cliente)       
Detalle_Venta(id, id_venta, id_producto, cantidad, precio_unitario, subtotal)      
Ingredientes (id, nombre, cantidad_disponible, unidad_medida)         
Productos_Ingredientes (id_producto, id_ingrediente, cantidad_usada)       
Proveedores (id, nombre, telefono, correo, direccion)         
Proveedor_ingrediente (id_proveedor, id_ingrediente, precio_unitatio, fecha_ultimo_suministro)    

# Descripcion y Cardinalidad
 1. Usuarios

Descripción: Representa a las personas que utilizan el sistema (administradores, cajeros, etc.).
Relaciones:

    Un usuario puede realizar muchas ventas.

    Cardinalidad: 1:N (Usuario → Ventas)

 2. Clientes

Descripción: Clientes que realizan compras en la pizzería. Pueden ser registrados para llevar un historial de compras.
Relaciones:

    Un cliente puede realizar muchas ventas.

    Cardinalidad: 1:N (Cliente → Ventas)

 3. Productos

Descripción: Pizzas, bebidas u otros productos que ofrece la pizzería.
Relaciones:

    Un producto puede estar en muchos detalles de venta.

    Un producto puede estar compuesto por muchos ingredientes.

    Cardinalidades:

        1:N (Producto → Detalle_Venta)

        M:N (Producto ↔ Ingredientes) mediante Productos_Ingredientes

 4. Ventas

Descripción: Registro de cada venta realizada en el sistema.
Relaciones:

    Una venta es realizada por un usuario y puede pertenecer a un cliente.

    Una venta tiene muchos detalles de venta.

    Cardinalidades:

        N:1 (Venta → Usuario)

        N:1 (Venta → Cliente)

        1:N (Venta → Detalle_Venta)

 5. Detalle_Venta

Descripción: Representa los productos vendidos en cada venta (detalle línea por línea).
Relaciones:

    Un detalle de venta pertenece a una venta y está asociado a un producto.

    Cardinalidades:

        N:1 (Detalle_Venta → Venta)

        N:1 (Detalle_Venta → Producto)

 6. Ingredientes

Descripción: Insumos necesarios para preparar los productos (como masa, queso, salsa, etc.).
Relaciones:

    Un ingrediente puede estar en muchos productos.

    Un ingrediente puede ser provisto por muchos proveedores.

    Cardinalidades:

        M:N (Ingrediente ↔ Productos) mediante Productos_Ingredientes

        M:N (Ingrediente ↔ Proveedores) mediante Proveedor_Ingrediente

 7. Proveedores

Descripción: Empresas o personas que suministran ingredientes a la pizzería.
Relaciones:

    Un proveedor puede suministrar muchos ingredientes.

    Cardinalidad: 1:N (Proveedor → Proveedor_Ingrediente)

 8. Productos_Ingredientes

Descripción: Tabla intermedia que define qué ingredientes componen un producto y en qué cantidad.
Relaciones:

    Pertenece a un producto y a un ingrediente.

    Cardinalidad: N:1 (respecto a Producto e Ingrediente)

 9. Proveedor_Ingrediente

Descripción: Tabla intermedia que registra qué proveedor suministra qué ingrediente y a qué precio.
Relaciones:

    Pertenece a un proveedor y a un ingrediente.

    Cardinalidad: N:1 (respecto a Proveedor e Ingrediente)

    