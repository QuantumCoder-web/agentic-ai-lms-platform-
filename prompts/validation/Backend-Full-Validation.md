Act as a Principal QA Architect, Integration Tester, and Microservices Reviewer.

Perform a complete end-to-end validation of the Agentic AI LMS backend.

Do not generate new features.

Goal:

Validate all existing services and identify gaps before continuing development.

Current Services:

- Eureka Server
- API Gateway
- Auth Service
- User Service
- Course Service

Validation Scope:

==================================================
1. Build Validation
==================================================

For each service:

- Run mvn clean test
- Run mvn clean package

Verify:

✅ Build Success
✅ Test Success
✅ No Compilation Errors
✅ No Dependency Conflicts

Services:

- eureka-server
- api-gateway
- auth-service
- user-service
- course-service

==================================================
2. Runtime Validation
==================================================

Start all services.

Verify:

Eureka Server:
http://localhost:8761

API Gateway:
http://localhost:8080

Auth Service:
http://localhost:8081

User Service:
http://localhost:8082

Course Service:
http://localhost:8083

Check startup logs.

Identify:

✅ Successful startup
⚠ Warnings
❌ Errors

==================================================
3. Eureka Validation
==================================================

Verify Eureka contains:

- API-GATEWAY
- AUTH-SERVICE
- USER-SERVICE
- COURSE-SERVICE

Status should be:

UP

==================================================
4. Actuator Validation
==================================================

Verify:

/actuator/health

/actuator/info

/actuator/metrics

for:

- API Gateway
- Auth Service
- User Service
- Course Service

Expected:

{
  "status": "UP"
}

==================================================
5. Swagger Validation
==================================================

Verify:

Auth Service

- /swagger-ui/index.html
- /v3/api-docs

User Service

- /swagger-ui/index.html
- /v3/api-docs

Course Service

- /swagger-ui/index.html
- /v3/api-docs

Confirm controllers are visible.

==================================================
6. API Gateway Validation
==================================================

Verify routing through Gateway.

Test:

Auth

http://localhost:8080/api/auth/**

User

http://localhost:8080/api/users/**

Course

http://localhost:8080/api/courses/**

Verify:

✅ Routing works
✅ Security works
✅ Expected responses returned

==================================================
7. Auth Service Validation
==================================================

Verify:

POST /api/auth/register/student

POST /api/auth/register/instructor

POST /api/auth/login

POST /api/auth/logout

POST /api/auth/refresh-token

POST /api/auth/forgot-password

POST /api/auth/reset-password

POST /api/auth/mfa/enable

POST /api/auth/mfa/verify

Validate:

✅ Request DTOs
✅ Response DTOs
✅ JWT generation
✅ Refresh token generation

Decode generated JWT.

Verify claims:

- subject/email
- role

==================================================
8. User Service Validation
==================================================

Verify:

GET /api/users/profile

PUT /api/users/profile

POST /api/users/profile/image

GET /api/instructors/pending

GET /api/instructors/{id}

PUT /api/instructors/{id}/approve

PUT /api/instructors/{id}/reject

GET /api/admin/users

GET /api/admin/instructors

GET /api/admin/dashboard

Verify:

✅ Security
✅ Validation
✅ OpenAPI contracts

==================================================
9. Course Service Validation
==================================================

Verify:

POST /api/courses

GET /api/courses

GET /api/courses/{id}

PUT /api/courses/{id}

DELETE /api/courses/{id}

POST /api/courses/{courseId}/modules

GET /api/courses/{courseId}/modules

POST /api/modules/{moduleId}/lessons

GET /api/modules/{moduleId}/lessons

POST /api/courses/{courseId}/enroll

GET /api/users/{userId}/enrollments

POST /api/progress/complete

GET /api/progress/{userId}/{courseId}

POST /api/courses/{courseId}/reviews

GET /api/courses/{courseId}/reviews

Verify:

✅ CRUD
✅ Security
✅ DTO validation

==================================================
10. Security Validation
==================================================

Verify:

JWT validation filters

Role extraction

@PreAuthorize usage

Protected endpoints require token.

Public endpoints remain public.

Verify:

ADMIN

INSTRUCTOR

STUDENT

authorization logic.

==================================================
11. Database Validation
==================================================

Verify:

AUTH_DB

USER_DB

COURSE_DB

Check:

✅ Tables created
✅ Entity mappings
✅ Foreign key relationships
✅ Hibernate startup

==================================================
12. Architecture Review
==================================================

Review:

- Layered architecture
- DTO usage
- Records usage
- No Lombok rule
- Java 25 compatibility
- RabbitMQ optional implementation
- Feign integrations
- JWT strategy

==================================================
13. Final Output
==================================================

Generate a report:

✅ Passed

⚠ Improvement Needed

❌ Critical

For every finding include:

- Service Name
- Issue
- Severity
- Recommended Fix

At the end provide:

Backend Readiness Score /100

and answer:

"Is the backend safe to freeze for frontend development?"
