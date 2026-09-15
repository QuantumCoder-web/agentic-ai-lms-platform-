Act as a Senior Spring Boot Architect and API Reviewer.

Review and validate the generated Auth Service against the project architecture and API contracts.

Project:
Agentic AI LMS Platform

Service:
AUTH-SERVICE

Validation Checklist:

1. Swagger Validation

Verify Swagger UI is accessible.

Expected URLs:

http://localhost:8081/swagger-ui/index.html

or

http://localhost:8081/swagger-ui.html

Validate all endpoints appear in Swagger.

---

2. OpenAPI Validation

Verify:

http://localhost:8081/v3/api-docs

returns valid OpenAPI JSON.

---

3. Endpoint Validation

Verify existence of:

POST /api/auth/register/student

POST /api/auth/register/instructor

POST /api/auth/login

POST /api/auth/logout

POST /api/auth/refresh-token

POST /api/auth/forgot-password

POST /api/auth/reset-password

POST /api/auth/mfa/enable

POST /api/auth/mfa/verify

---

4. Request DTO Validation

Review request payloads.

Check whether they align with enterprise API design.

Recommendations:

Use Request Body instead of Query Parameters for:

Forgot Password

Current:
POST /forgot-password?email=test@test.com

Preferred:
{
  "email": "test@test.com"
}

MFA Verify

Current:
POST /mfa/verify?code=123456

Preferred:
{
  "code": "123456"
}

---

5. Response Contract Validation

Verify Login Response returns:

{
  "accessToken": "",
  "refreshToken": "",
  "role": ""
}

Verify consistent response structure across all APIs.

---

6. Validation Annotations

Verify:

- @NotBlank
- @Email
- @NotNull
- @Size

are present where applicable.

Generate test requests that should fail validation.

---

7. Security Validation

Verify:

- Public endpoints
- Protected endpoints
- JWT filter configuration
- SecurityConfig

Check for security gaps.

---

8. Actuator Validation

Verify:

http://localhost:8081/actuator

http://localhost:8081/actuator/health

http://localhost:8081/actuator/info

http://localhost:8081/actuator/metrics

---

9. Eureka Validation

Verify Auth Service is registered in Eureka.

Expected:

AUTH-SERVICE -> UP

---

10. Code Review

Review:

- Controller layer
- DTO layer
- Service layer
- Security layer
- Exception handling

Check alignment with:

- HLD
- LLD
- API-CONTRACTS.md

---

11. Output

Generate a review report:

✅ Correct

⚠ Needs Improvement

❌ Critical Issue

Provide exact fixes for every issue found.

Do not generate new features.

Only validate, review and identify gaps.
