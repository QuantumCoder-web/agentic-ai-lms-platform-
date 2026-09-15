# Prompt-003 : Auth Service

## Prompt

```text
Act as a Principal Java Microservices Architect.

Generate a production-ready Auth Service for an enterprise-grade microservices platform.

Project Name:

Agentic AI LMS Platform

Generate the project inside:

backend/auth-service

Technology Stack:

- Java 21
- Spring Boot 3.x
- Maven
- Spring Security
- Spring Data JPA
- PostgreSQL
- Eureka Client
- OpenFeign
- RabbitMQ
- Spring Boot Actuator
- Validation
- Lombok
- JWT Authentication

Architecture Context:

Infrastructure:

- Eureka Server (Port 8761)
- API Gateway (Port 8080)

Business Services:

- Auth Service (Current)
- User Service
- Course Service
- AI Service
- Notification Service

Database:

AUTH_DB

Responsibilities:

- Student Registration
- Instructor Registration
- Login
- Logout
- JWT Generation
- Refresh Token Management
- Forgot Password
- Password Reset
- MFA Skeleton
- Role Management

Roles:

- ADMIN
- INSTRUCTOR
- STUDENT

Database Tables:

credentials

- id
- email
- password_hash
- role
- enabled
- created_at
- updated_at

refresh_tokens

- id
- user_id
- token
- expiry_date

password_reset_tokens

- id
- user_id
- token
- expiry_date

mfa_settings

- id
- user_id
- enabled
- secret

Event Publishing:

Publish:

UserRegisteredEvent

using RabbitMQ.

Requirements:

1. Generate complete project structure.

2. Create layered architecture:

- controller
- service
- repository
- entity
- dto
- config
- security
- exception
- mapper
- event

3. PostgreSQL configuration.

4. Eureka Client configuration.

5. RabbitMQ producer configuration.

6. JWT implementation.

7. Refresh Token implementation.

8. BCrypt password encryption.

9. Global Exception Handling.

10. Validation annotations.

11. OpenAPI / Swagger configuration.

12. Spring Security configuration.

13. MFA skeleton implementation.

14. Password reset workflow skeleton.

15. Actuator configuration.

Generate APIs:

POST /api/auth/register/student

POST /api/auth/register/instructor

POST /api/auth/login

POST /api/auth/logout

POST /api/auth/refresh-token

POST /api/auth/forgot-password

POST /api/auth/reset-password

POST /api/auth/mfa/enable

POST /api/auth/mfa/verify

Response Example:

{
  "accessToken": "jwt-token",
  "refreshToken": "refresh-token",
  "role": "STUDENT"
}

Testing Requirements:

Generate:

- JUnit 5 Tests
- Mockito Tests
- Spring Boot Tests

Minimum Coverage Target:

80%+

Quality Requirements:

- SonarQube Ready
- Clean Code
- SOLID Principles
- No hardcoded secrets
- Environment-based configuration

Actuator Endpoints:

- health
- info
- metrics

Port:

8081

Service Name:

AUTH-SERVICE

Package Name:

com.agenticailms.auth

Expected Output:

backend/
└── auth-service/

Generate:

- pom.xml
- application.yml
- complete source code
- test cases
- README.md

Explain every generated file and design decision.
```
