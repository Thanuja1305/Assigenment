Library Management System
A robust Spring Boot MVC application designed to manage a library's catalog by maintaining authors and their associated books. The project demonstrates a full CRUD implementation using Spring Data JPA, JSP for the frontend, and a One-to-Many relational database design.  

## Features
Author Management: Register, list, and edit author details (Name, Email, Country).  

Book Catalog: Manage a collection of books linked to specific authors.  

Relational Mapping: Implements a One-to-Many relationship (one author to many books) with cascade operations.  

Performance Optimization: Utilizes custom JOIN FETCH queries to eliminate N+1 select performance issues when retrieving book data.  

Data Validation: Server-side validation using Jakarta Bean Validation for emails, mandatory fields, and price constraints.  

## Tech Stack
Backend: Spring Boot 3.2.3, Java 17.  

Persistence: Spring Data JPA with Hibernate.  

Database: MySQL.  

Frontend: JSP (JavaServer Pages), JSTL, and CSS.  

Testing: JUnit 5, Mockito, and @DataJpaTest.  

## Project Structure
Plaintext
src/main/java/com/university/library/
├── controller/  # Web Request Handlers (Home, Author, Book)
├── model/       # JPA Entities (Author, Book)
├── repository/  # Data Access Layers
└── service/     # Business Logic Layers

src/main/resources/
├── static/css/  # UI Styling
├── data.sql     # Initial Database Seeds
└── webapp/      # JSP Views and Layouts
## Configuration & Setup
### Prerequisites
JDK 17 or higher.  

MySQL Server.  

Maven.  

### Database Configuration
Update the src/main/resources/application.properties file with your MySQL credentials:

Properties
spring.datasource.url=jdbc:mysql://localhost:3306/library_db?createDatabaseIfNotExist=true
spring.datasource.username=your_username
spring.datasource.password=your_password
The application is configured to automatically create the schema and seed data from data.sql upon startup.  

## Running the Application
Clone the repository.

Navigate to the project root and run:

Bash
mvn spring-boot:run
Access the application at http://localhost:8080[cite: 1].

## Testing
The project includes both unit and integration tests[cite: 1]:

AuthorServiceTest: Mocks the repository layer to verify business logic[cite: 1].

BookRepositoryTest: Tests data persistence and the custom INNER JOIN logic using an in-memory database context[cite: 1].

To run tests:

Bash
mvn test
## Challenges & Solutions
JSP Integration: Spring Boot does not natively support JSPs in executable JARs. This was resolved by including tomcat-embed-jasper and configuring a custom InternalResourceViewResolver in the properties file[cite: 1].

Navigation Logic: Implemented a modular UI where the landing page remains clean and focused, while administrative pages include full sidebar/navigation suites[cite: 1]
