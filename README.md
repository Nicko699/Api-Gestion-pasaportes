Sistema de Pasaportes
📌 Requisitos previos
Java 17 o superior

Maven 3.8+

Base de datos configurada en application.properties (MySQL, PostgreSQL, etc.)

Haber creado una bd localmente.

IDE recomendado: IntelliJ IDEA o Eclipse

🚀 Ejecución
bash
Copiar
Editar
# Clonar el repositorio
git clone https://github.com/usuario/sistema-pasaportes.git

# Entrar al proyecto
cd sistema-pasaportes

# Ejecutar con Maven
mvn spring-boot:run
El servidor se iniciará en: http://localhost:8080

📂 Estructura del proyecto
Controller/ → Maneja las solicitudes HTTP.

Service/ → Contiene la lógica de negocio.

Repository/ → Acceso a la base de datos con JPA.

Dto/ → Objetos de transferencia de datos.

Model/ → Entidades de base de datos.

Exception/ → Manejo de errores y excepciones.

Mapper/ → Conversión entre entidades y DTOs.
