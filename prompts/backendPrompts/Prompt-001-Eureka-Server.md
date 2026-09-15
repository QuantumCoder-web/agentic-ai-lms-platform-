# Prompt-001 : Eureka Discovery Server

## Objective

Generate the Service Discovery layer for the Agentic AI LMS Platform.

## Prompt

```text
Act as a Principal Java Microservices Architect.

Generate a production-ready Eureka Discovery Server for an enterprise-grade microservices project.

Project Name:
Agentic AI LMS Platform

Generate the application inside:

backend/eureka-server

Technology Stack:

- Java 21
- Maven
- Spring Boot 3.x
- Spring Cloud Netflix Eureka Server
- Spring Boot Actuator

Architecture Context:

This Eureka Server will act as the service registry for:

Infrastructure Services:
- API Gateway

Business Services:
- Auth Service
- User Service
- Course Service
- AI Service
- Notification Service

Requirements:

1. Create a standalone Spring Boot Eureka Server application.

2. Generate complete project structure.

3. Generate:
   - pom.xml
   - application.yml
   - main application class
   - README.md

4. Configure Eureka:

   Port:
   8761

   Host:
   localhost

5. Disable:

   - self registration
   - registry fetching

6. Enable Eureka Dashboard.

7. Configure Spring Boot Actuator.

8. Expose health endpoints.

9. Use enterprise-level package naming:

com.agenticailms.discovery

10. Follow Java and Spring Boot best practices.

11. Add meaningful comments where required.

12. Provide a clear explanation of every generated file.

Expected Output Structure:

backend/
└── eureka-server/
    ├── src/main/java
    ├── src/main/resources
    ├── pom.xml
    └── README.md

Generate complete source code for all files.
```
