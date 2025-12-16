# 🛂 API REST Sistema de Pasaportes

> API REST para gestión de personas y pasaportes con arquitectura en capas y buenas prácticas

## 📖 Descripción

Sistema de gestión de pasaportes desarrollado con **Spring Boot** que implementa operaciones CRUD para personas y sus pasaportes asociados. Utiliza arquitectura por capas, DTOs, MapStruct para mapeo de objetos y validaciones con Bean Validation.

## ✨ Características

- ✅ CRUD completo de personas y pasaportes
- 📄 Paginación de resultados
- 🔍 DTOs para Request y Response
- 🗺️ Mapeo automático con MapStruct
- ✔️ Validaciones con Bean Validation
- 🚨 Manejo global de excepciones
- 📡 Códigos HTTP estándar
- 🏗️ Arquitectura en capas

## 🛠️ Tecnologías

- ☕ **Java 17**
- 🌱 **Spring Boot 3.x**
- 🗄️ **Spring Data JPA**
- 🐘 **Hibernate**
- 🗃️ **MySQL 8.0**
- 🗺️ **MapStruct** - Mapeo de DTOs
- ✔️ **Bean Validation** - Validaciones
- 🧱 **Maven** - Gestión de dependencias

## 📡 Endpoints

### 📘 Personas

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| `GET` | `/persona` | Listar personas (paginado) |
| `GET` | `/persona/{id}` | Obtener persona por ID |
| `POST` | `/persona` | Crear persona |
| `PUT` | `/persona/{id}` | Editar persona |
| `DELETE` | `/persona/{id}` | Eliminar persona |

#### 📌 Crear Persona

**Request:** `POST /pasaportes/api/v1/persona`

```json
{
  "nombre": "Juan",
  "apellido": "Pérez",
  "documento": "12345678",
  "pasaporte": {
    "numeroPasaporte": "AB123456",
    "fechaEmision": "2024-01-15",
    "fechaExpiracion": "2034-01-15",
    "pais_emision": "Colombia"
  }
}
```

**Response:** `201 Created`

```json
{
  "id": 1,
  "nombre": "Juan",
  "apellido": "Pérez",
  "documento": "12345678",
  "pasaporte": {
    "id": 1,
    "numeroPasaporte": "AB123456",
    "fechaEmision": "2024-01-15",
    "fechaExpiracion": "2034-01-15",
    "pais_emision": "Colombia"
  }
}
```

#### 📌 Listar Personas (Paginado)

**Request:** `GET /pasaportes/api/v1/persona?page=0&size=10`

```json
{
  "content": [
    {
      "id": 1,
      "nombre": "Juan",
      "apellido": "Pérez",
      "documento": "12345678",
      "pasaporte": {...}
    }
  ],
  "pageable": {
    "pageNumber": 0,
    "pageSize": 10
  },
  "totalElements": 25,
  "totalPages": 3
}
```

## ⚙️ Instalación

### 1️⃣ Clonar repositorio

```bash
git clone https://github.com/Nicko699/Api-Gestion-pasaportes.git
cd Api-Gestion-pasaportes
```

### 2️⃣ Configurar base de datos

Crear la base de datos en MySQL:

```sql
CREATE DATABASE pasaportes;
```

Editar `src/main/resources/application.properties`:

```properties
spring.application.name=Sistema pasaportes
server.servlet.context-path=/pasaportes/api/v1

# Base de datos
spring.datasource.url=jdbc:mysql://localhost:3306/pasaportes?serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=tu_password
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=update
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect
```

### 3️⃣ Compilar y ejecutar

```bash
mvn clean install
mvn spring-boot:run
```

La API estará en: `http://localhost:8080/pasaportes/api/v1`

## 🚨 Manejo de Errores

El sistema maneja las siguientes excepciones:

| Excepción | Código HTTP | Descripción |
|-----------|-------------|-------------|
| `NotFoundException` | 404 | Recurso no encontrado |
| `MethodArgumentNotValidException` | 400 | Error de validación |

### Ejemplo de error

```json
{
  "status": "NOT_FOUND",
  "message": "Persona con ID 999 no encontrada"
}
```

### Error de validación

```json
{
  "nombre": "El nombre no puede estar vacío",
  "documento": "El documento debe tener entre 8 y 10 caracteres"
}
```

## 📋 Códigos HTTP

| Código | Significado |
|--------|-------------|
| `200 OK` | Solicitud exitosa |
| `201 Created` | Recurso creado |
| `204 No Content` | Eliminación/actualización exitosa |
| `400 Bad Request` | Error de validación |
| `404 Not Found` | Recurso no encontrado |
| `500 Internal Server Error` | Error del servidor |

## 🧪 Probar con Postman

### Ejemplos de pruebas

1. **Crear persona con pasaporte**
   - `POST /pasaportes/api/v1/persona`

2. **Listar personas**
   - `GET /pasaportes/api/v1/persona?page=0&size=5`

3. **Obtener persona**
   - `GET /pasaportes/api/v1/persona/1`

4. **Actualizar persona**
   - `PUT /pasaportes/api/v1/persona/1`

5. **Eliminar persona**
   - `DELETE /pasaportes/api/v1/persona/1`

## 👤 Autor

**Nicko699**
- GitHub: [@Nicko699](https://github.com/Nicko699)

---

⭐ **Si te sirvió el proyecto, dale una estrella en GitHub**
