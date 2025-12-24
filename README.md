# 🏥 Sistema de Gestión Hospitalaria - Proyecto DAW I

[![Java](https://img.shields.io/badge/Java-17-orange)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen)](https://spring.io/projects/spring-boot)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-blue)](https://www.mysql.com/)

Este sistema es una solución integral para la gestión de un centro médico, permitiendo el control de pacientes, médicos, citas, especialidades y comprobantes de pago. Desarrollado como parte del curso de Desarrollo de Aplicaciones Web I.

## Descripción General
El sistema permite automatizar el flujo hospitalario,
* **Gestión de Usuarios:** Roles de Administrador, Recepcionista, Cajero y Médico.
* **Citas médicas:** Registro, cancelación y seguimiento de estados (Pendiente, Pagado, Atendido, etc.).
* **Historial médico:** Regsitro detallado de diagnósticos y tratamientos por cita.
* **Facturación:** Generación de comprobantes de pago con diferentes métodos (Efectivo, Tarjeta, Transferencia).
* **Disponibilidad:** Generación automática de slots de horarios para los médicos.
   
## Requisitos Técnicos
* **Java Development Kit (JDK):** Versión 17.
* **Gestor de Dependencias:** Maven.
* **Base de Datos:** MySQL Server.
* **IDE Recomendado:** Spring Tool Suite (STS).

## Configuración del Archivo application.properties
El archivo se encuentra en src/main/resources/application.properties. Debes configurarlo con tus credenciales locales de MySQL:

### Puerto en el que correrá la API (por defecto 8080)
server.port=8080

### CONFIGURACIÓN DE BASE DE DATOS (MySQL)
#### URL de conexión: reemplaza 'localhost:3306' si usas otro puerto
spring.datasource.url=jdbc:mysql://localhost:3306/DB_Hospital?useSSL=false&serverTimezone=UTC

#### Credenciales de tu base de datos
spring.datasource.username=root
spring.datasource.password=tu_contraseña_aqui

#### Driver de conexión
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

### CONFIGURACIÓN DE JPA / HIBERNATE
#### 'update' permite que Hibernate cree las tablas si no existen 
#### (aunque se recomienda usar los scripts SQL adjuntos)
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect

#### Variables Clave:
* server.port: Define el puerto donde escuchará la aplicación. Si el 8080 está ocupado, cámbialo aquí.

* spring.datasource.url: El nombre de la base de datos debe coincidir con el del script SQL (DB_Hospital).

* spring.jpa.hibernate.ddl-auto: Configurado en update para sincronizar las entidades de Java con las tablas de MySQL.

## Instalación y Ejecución
Para ejecutar este proyecto localmente, sigue estos pasos:

**1. Preparar la Base de Datos:**
Ejecuta los scripts SQL proporcionados en el siguiente orden para evitar errores de llaves foráneas:
* DB_Hospital_Create.sql (Crea tablas y estructura).
* DB_Hospital_Insert.sql (Carga datos maestros: especialidades y usuarios iniciales).
* DB_Hospital_Logic.sql (Procedimientos y eventos para slots de horarios).

**2. Clonar y Compilar:**
Abre una terminal y ejecuta:
git clone [https://github.com/ivangonzalespurizaca/SistemaDeGestionDeCitasMedicas.git]
cd proyecto-hospital
mvn clean install

**3. Ejecutar la Aplicación:**
Puedes iniciar el sistema con el siguiente comando:
mvn spring-boot:run
La API estará disponible en: http://localhost:8080/api/
