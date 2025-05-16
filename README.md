# Unidad3_Desafio1
#Automatización de Búsqueda y Compra en Amazon

Este proyecto automatiza un flujo funcional de compra en Amazon.com utilizando Java, Selenium WebDriver, Cucumber (BDD) y el patrón Page Object Model (POM). El escenario incluye búsqueda, navegación entre páginas de resultados, selección de producto y agregado al carrito.

Tecnologías utilizadas
Herramienta	Versión	Descripción
Java	17+	Lenguaje principal
Gradle	8.0.2	Gestor de dependencias y ejecución
Selenium WebDriver	4.15.0	Control del navegador
WebDriverManager	5.6.2	Descarga automática del driver
Cucumber (BDD)	7.14.1	Framework para pruebas en lenguaje natural
JUnit	5.9.1	Framework de pruebas
TestNG (opcional)	7.8.0	Alternativa para pruebas
Estructura del Proyecto
├── features/ │ └── AmazonSearch.feature # Escenario en lenguaje Gherkin ├── steps/ │ └── AmazonSearchSteps.java # Definición de pasos de Cucumber ├── pages/ │ ├── BasePage.java # Funciones reutilizables y setup de WebDriver │ └── AmazonSearchPage.java # Funciones específicas de Amazon ├── build.gradle # Configuración del proyecto (dependencias) └── README.md # Este documento

Escenario Automatizado
```gherkin Scenario: As a Customer, I want to search for Alexa and verify the third result on page 2 can be added to the cart Given the user navigates to www.amazon.com And searches for Alexa And navigates to the page number 2 And selects the third item Then the user is able to add it to the cart

Ejecución del Proyecto
Requisitos
Java 17 o superior
Gradle instalado (o usar el wrapper ./gradlew en sistemas Unix o gradlew.bat en Windows)
Ejecutar pruebas
```bash gradle test

Cambios importantes frente al código base
Mejora	Descripción
Cantidad de producto	Se agregó setQuantityToTwo() para agregar dos productos al carrito.
Idioma	Se fuerza el idioma inglés en Amazon usando cookies (lc-main=en_US).
Refactorización	Separación del código en Page Objects (BasePage y AmazonSearchPage).
Correcciones	URL corregida, localizadores más estables y comentarios explicativos.
Reutilización	Parámetro quantityDropdown centralizado para evitar valores hardcoded.
Escenario Outline	Se dejó lista una versión comentada para ejecutar con múltiples productos.
Comentarios clave
Archivo	Línea de Código
AmazonSearchSteps.java	amazon.setQuantityToTwo(); // Nuevo paso antes de agregar al carrito
AmazonSearchPage.java	private String quantityDropdown = "quantity"; // Localizador reutilizado
BasePage.java	driver.get("https://www.amazon.com/-/es");
driver.manage().addCookie(new Cookie("lc-main", "en_US"));
driver.navigate().refresh();
