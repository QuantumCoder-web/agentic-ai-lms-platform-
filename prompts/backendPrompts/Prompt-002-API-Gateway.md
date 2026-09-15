# Prompt-002 : API Gateway

## Objective

Generate the API Gateway for the Agentic AI LMS Platform.

## Prompt

```text
Act as a Principal Java Microservices Architect.

Generate a production-ready Spring Cloud API Gateway.

Project Name:
Agentic AI LMS Platform

Generate the complete application inside:

backend/api-gateway

Technology Stack:

- Java 25
- Maven
- Spring Boot 3.x
- Spring Cloud Gateway
- Spring Cloud Netflix Eureka Client
- Spring Boot Actuator

Architecture Context:

Service Registry:
- Eureka Server (Port 8761)

Gateway Responsibilities:

- Centralized Routing
- Service Discovery
- JWT Validation (placeholder for future implementation)
- Request Logging
- Correlation ID Propagation
- Security Boundary
- Entry Point for all Microservices

Business Services:

- Auth Service
- User Service
- Course Service
- AI Service
- Notification Service

Requirements:

1. Generate a standalone Spring Cloud Gateway project.

2. Register with Eureka Server.

3. Generate:

   - pom.xml
   - application.yml
   - main application class
   - README.md

4. Configure Port:

   8080

5. Configure Eureka Client:

   Eureka URL:
   http://localhost:8761/eureka

6. Add Route Definitions:

   Auth Service

   Route:
   /auth/**

   Service:
   lb://AUTH-SERVICE

   -----------------------

   User Service

   Route:
   /users/**

   Service:
   lb://USER-SERVICE

   -----------------------

   Course Service

   Route:
   /courses/**

   Service:
   lb://COURSE-SERVICE

   -----------------------

   AI Service

   Route:
   /ai/**

   Service:
   lb://AI-SERVICE

   -----------------------

   Notification Service

   Route:
   /notifications/**

   Service:
   lb://NOTIFICATION-SERVICE

7. Generate a Global Logging Filter.

Purpose:

- Log Request URI
- Log HTTP Method
- Log Request Time

8. Generate a Correlation ID Filter.

Requirements:

- Generate UUID if header missing
- Forward Correlation ID downstream
- Add Correlation ID to logs

Header Name:

X-Correlation-Id

9. Generate a JWT Authentication Filter Skeleton.

Requirements:

- Placeholder implementation only
- Skip validation for auth endpoints
- Ready for future integration

10. Configure Spring Actuator.

Expose:

- health
- info
- metrics

11. Use package structure:

com.agenticailms.gateway

12. Follow enterprise coding standards.

13. Explain every generated file and why it exists.

Expected Output Structure:

backend/
└── api-gateway/
    ├── src/main/java
    ├── src/main/resources
    ├── pom.xml
    └── README.md

Generate complete source code.
```
