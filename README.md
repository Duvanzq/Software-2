☕ Café & Co. — Sistema de Gestión de Cafetería
Café & Co. es una aplicación de escritorio desarrollada en Java Swing para apoyar la gestión de una cafetería. Permite administrar productos, personalizar pedidos, configurar promociones, hacer seguimiento a los estados de preparación y consultar resúmenes diarios de ventas.

Proyecto académico de Ingeniería de Software II — Universidad Libre, Bogotá (2026).
Tecnologías
- Java 8 o superior (recomendado: JDK 17 o 21).
- Java Swing para las interfaces gráficas.
- Apache NetBeans como entorno de desarrollo.
- Maven para la compilación y gestión de dependencias.
- JUnit 4 para pruebas unitarias.
- Figma como referencia visual del rediseño.
Los datos se almacenan en memoria: no se requiere instalar ni configurar una base de datos.

Funcionalidades
Módulo	Funciones disponibles
Inicio	Panel de resumen, indicadores y pedidos recientes.
Productos	Registrar, consultar, buscar, filtrar, editar y eliminar productos.
Nuevo pedido	Elegir productos y cantidades, agregar complementos y calcular subtotales y descuentos.
Pedidos	Consultar pedidos, ver detalles y avanzar su estado de preparación.
Promociones	Registrar descuentos porcentuales o fijos, establecer días y horarios, activar/desactivar y eliminar promociones.
Cierre de caja	Consultar por fecha las ventas brutas, descuentos y ventas netas de los pedidos entregados.


Reglas principales
- Estados del pedido: PENDIENTE → EN_PREPARACION → LISTO → ENTREGADO, sin saltos ni retrocesos.
- Personalización: los complementos se agregan sin modificar el producto original. La interfaz incluye leche adicional, crema y queso.
- Descuentos: cuando varias promociones están vigentes, se aplica solo la que representa el mayor ahorro.
- Valores históricos: el pedido conserva el precio y descuento calculados al registrarse, aunque después cambien los productos o las promociones.
- Cierre diario: se contabilizan únicamente los pedidos entregados en la fecha seleccionada.
Patrones de diseño
El proyecto emplea tres patrones:
Patrón	Clases principales	Aplicación
Decorator	ItemMenu, Producto, Complemento	Agrega complementos al producto y recalcula su descripción y precio sin modificar la clase base.
Strategy	PoliticaDescuento, DescuentoPorcentaje, DescuentoFijo, Promocion	Permite intercambiar algoritmos de descuento manteniendo un contrato común.
Facade (fachada de acceso)	ContextoCafeteria y los cuatro servicios	Centraliza la creación y el acceso a los servicios compartidos por las interfaces.


Nota sobre Facade: ContextoCafeteria ofrece acceso a los servicios mediante getters; las interfaces invocan después las operaciones del servicio correspondiente. No oculta todas las operaciones de negocio detrás de métodos propios.
Estructura del proyecto
Cafeteria_Java_Figma_NetBeans/
├── pom.xml
├── docs/
│   ├── vista_inicio_prueba.png
│   └── vista_nuevo_pedido_prueba.png
└── src/
    ├── main/java/co/edu/unilibre/cafeteria/
    │   ├── grafica/       # CafeteriaFigma y AplicacionGrafica
    │   ├── consola/       # AplicacionConsola
    │   ├── modelo/        # Productos, pedidos, promociones y datos
    │   ├── servicio/      # Lógica de negocio y ContextoCafeteria
    │   └── promocion/     # Políticas de descuento (Strategy)
    └── test/java/co/edu/unilibre/cafeteria/
        ├── modelo/
        ├── servicio/
        └── pruebas/
Cómo ejecutar el proyecto
Opción 1: Apache NetBeans
1. Instala JDK 8 o superior y Apache NetBeans con soporte para Maven.
2. Abre NetBeans y selecciona File → Open Project.
3. Selecciona la carpeta raíz del proyecto, donde se encuentra pom.xml.
4. Ejecuta el proyecto con Run Project, o abre CafeteriaFigma.java y usa Run File.
La clase principal configurada en pom.xml es:
co.edu.unilibre.cafeteria.grafica.CafeteriaFigma
Opción 2: Terminal con Maven
Desde la carpeta que contiene pom.xml:
mvn clean package
java -jar target/cafeteria-1.0-SNAPSHOT.jar
También puedes iniciar la interfaz principal con:
mvn exec:java
Otras interfaces disponibles: AplicacionGrafica (Swing básica) y AplicacionConsola (menú en terminal). Se pueden ejecutar por separado desde NetBeans. Cada ejecución puede crear su propio contexto y conjunto de datos temporales.
Pruebas
Para ejecutar las pruebas unitarias JUnit incluidas:
mvn test
El repositorio contiene pruebas de productos, pedidos, promociones, complementos y caja, además de una clase de verificación integrada (VerificacionIntegrada).
Capturas de pantalla
Panel de inicio

Registro de pedidos

Las capturas corresponden a una ejecución de prueba con datos temporales, no a registros precargados.
Limitaciones actuales
- Sin base de datos ni persistencia: los datos se pierden al cerrar la aplicación.
- No hay autenticación de usuarios ni permisos por roles.
- No se implementan gestión de inventario, facturación electrónica ni medios de pago diferenciados.
- Los combos y las notificaciones internas no están incluidos en el alcance actual.
- La interfaz de Swing está construida mediante código Java; no incluye formularios .form del diseñador visual de NetBeans.
Equipo de desarrollo
- Duvan Andres Alarcon Mora
- Andres Ardila Neira
- Miguel Angel Velosa Soler
Universidad Libre — Ingeniería de Software II — 2026
Diseño de referencia
Prototipo de Café & Co. en Figma
