```java
public class Usuario {
    private String idUsuario;
    private String nombre;
    private String correoElectronico;
    private String contrasenaHash;
    private List<Direccion> direccionEnvio;  //Esto es un objeto anidado
    private Direccion direccionFacturacion;
    private List<String> historialPedidos;
    private List<Pedido> pedido;
    private String numeroTelefono;
    private boolean activo;
    private boolean deleted;

    // Getters and Setters
}

public class Direccion {
    private String calle;
    private String ciudad;
    private String estado;
    private String codigoPostal;
    private String pais;
    private boolean deleted;

    // Getters and Setters
}

public class Producto {
    private String idProducto;
    private String nombre;
    private String descripcion;
    private double precio;
    private int cantidadStock;
    private List<String> categorias;
    private List<String> subCategorias;
    private List<String> etiquetas;
    private String marca;
    private List<Resena> resenas;
    private boolean deleted;

    // Getters and Setters
}

public class Resena {
    private String idResena;
    private String idUsuario;
    private String idProducto;
    private int calificacion;
    private String comentario;
    private Date fechaCreacion;
    private boolean deleted;

    // Getters and Setters
}

public class Pedido {
    private String idPedido;
    private List<ItemPedido> items;  //Esto es un objeto anidado
    private double montoTotal;
    private Date fechaPedido;
    private Pago detallesPago;
    private Envio detallesEnvio;
    private boolean deleted;

    // Getters and Setters
}

public class ItemPedido {
    private String idItemProducto;
    private Producto producto;
    private int cantidad;
    private double precioUnitario;
    private boolean deleted;

    // Getters and Setters
}

public class Pago {
    private String idPago;
    private String metodo; // ej., "tarjeta_credito", "paypal"
    private String idTransaccion;
    private Date fechaPago;
    private double monto;
    private String estado; // ej., "completado", "fallido"
    private boolean deleted;

    // Getters and Setters
}

public class Envio {
    private String transportista;
    private Date fechaEntregaEstimada;
    private Date fechaEnviado;
    private Direccion direccionEntrega;
    private boolean deleted;

    // Getters and Setters
}


public class Promocion {
    private String idPromocion;
    private ItemPedido ItemPedido;
    private String codigo;
    private String descripcion;
    private double valorDescuento;
    private String tipoDescuento; // ej., "porcentaje", "fijo"
    private Date validoDesde;
    private Date validoHasta;
    private boolean activa;
    private boolean deleted;

    // Getters and Setters
}


public class Transportista{
    private String idTrasnportista;
    private List<Envio> envio;
    private String nombre;
    private String correo; 
    private String telefono; 
    private String direccion;
    private String wbe;
    private String contacto;
}
public class Provehedor{
    private String idProvehedor;
    private String nombre;
    private String contacto;
    private String correo;
    private String telefono;
    private String web;
    private List<Producto>productos;

}


```


### **1. Clase `Usuario`**
- **Propósito**: Representa a los usuarios del sistema, ya sean clientes o administradores.
- **Razón**: Es fundamental tener una entidad que almacene información sobre los usuarios, ya que son el núcleo de cualquier tienda en línea. Los atributos incluyen datos personales (nombre, correo electrónico, número de teléfono), roles (cliente/administrador) y direcciones (envío/facturación). Además, se incluye un historial de pedidos para facilitar el seguimiento de compras previas.

---

### **2. Clase `Direccion`**
- **Propósito**: Almacena información de direcciones asociadas a los usuarios.
- **Razón**: Las direcciones son esenciales para el envío y la facturación. Separar esta información en una clase independiente permite reutilizarla tanto para direcciones de envío como de facturación, evitando redundancia.
En este caso la direccion es un documento anidado dentro del documento del usuario

---

### **3. Clase `Producto`**
- **Propósito**: Representa los productos disponibles en la tienda.
- **Razón**: Esta clase incluye todos los detalles necesarios para describir un producto: nombre, descripción, precio, stock, categorías, etiquetas, URL de imagen y marca. Además, se incluyen reseñas para capturar la retroalimentación de los clientes, lo cual es crucial para el equipo de marketing. La inclusión de categorías y subcategorías permite organizar los productos de manera jerárquica, facilitando la navegación y búsqueda.

---

### **4. Clase `Resena`**
- **Propósito**: Almacena las reseñas y calificaciones de los productos realizadas por los usuarios.
- **Razón**: Las reseñas son una herramienta poderosa para influir en las decisiones de compra de otros clientes. Incluir la calificación, comentario y fecha de creación permite analizar tendencias y mejorar la experiencia del usuario.

---

### **5. Clase `Pedido`**
- **Propósito**: Representa un pedido realizado por un usuario.
- **Razón**: Un pedido es una transacción clave en una tienda en línea. Incluye detalles como el usuario que lo realizó, los productos comprados, el monto total, el estado del pedido y los detalles de pago y envío. Esto permite un seguimiento completo del ciclo de vida del pedido.

---

### **6. Clase `ItemPedido`**
- **Propósito**: Representa un producto dentro de un pedido.
- **Razón**: Un pedido puede contener múltiples productos, y esta clase permite almacenar detalles específicos de cada uno (nombre, cantidad, precio unitario). Esto facilita el cálculo del monto total y el seguimiento de inventario.

En este caso la los items son documentos anidados dentro del documento del pedido

---

### **7. Clase `Pago`**
- **Propósito**: Almacena información sobre los pagos realizados por los usuarios.
- **Razón**: El pago es una parte crítica de cualquier transacción. Incluir detalles como el método de pago, la fecha, el monto y el estado permite gestionar correctamente las finanzas y resolver disputas si es necesario.

---

### **8. Clase `Envio`**
- **Propósito**: Representa la información relacionada con el envío de un pedido.
- **Razón**: El envío es una actividad clave en una tienda en línea. Incluir el número de seguimiento, el transportista, las fechas estimadas y la dirección de entrega permite un seguimiento eficiente y mejora la experiencia del cliente.

---

### **9. Clase `Promocion`**
- **Propósito**: Representa las promociones o descuentos disponibles en la tienda.
- **Razón**: Las promociones son una herramienta esencial para el equipo de marketing, ya que incentivan las compras y aumentan las ventas. Incluir atributos como el código, el tipo de descuento y las fechas de validez permite gestionar campañas de manera efectiva.

