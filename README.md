☕ Café & Co.
Café & Co. es una aplicación de escritorio para la gestión de una cafetería, desarrollada como proyecto de Ingeniería de Software II de la Universidad Libre.
Funcionalidades
- Productos: registrar, consultar, buscar, editar y eliminar.
- Pedidos: seleccionar productos, agregar complementos y controlar el estado de preparación.
- Promociones: aplicar descuentos fijos o porcentuales según días y horarios.
- Caja: consultar ventas, descuentos y totales de los pedidos entregados por fecha.
- Inicio: visualizar un resumen de la actividad de la cafetería.
Tecnologías y diseño
- Java 8+, Java Swing, Apache NetBeans y Maven.
- Patrones de diseño: Decorator, Strategy y Facade (fachada de acceso a servicios mediante ContextoCafeteria).
Ejecución
Versión para Windows: el sistema dispone de un ejecutable .exe. Ejecuta el archivo distribuido con el proyecto.

Desde el código fuente: abre el proyecto Maven en NetBeans y ejecuta CafeteriaFigma.java, o usa estos comandos en la carpeta que contiene pom.xml:
mvn clean package
java -jar target/cafeteria-1.0-SNAPSHOT.jar
Para ejecutar las pruebas: mvn test.
Limitaciones
Los datos se guardan temporalmente en memoria: al cerrar la aplicación se pierden. El sistema no incluye base de datos ni autenticación de usuarios.
Equipo
- Duvan Andres Alarcon Mora
- Andres Ardila Neira
- Miguel Angel Velosa Soler
Universidad Libre · Bogotá · 2026
