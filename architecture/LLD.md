# Low Level Design (LLD)

## Project Name

Agentic AI LMS Platform

---

# 1. Service Breakdown

## Business Services

- Auth Service
- User Service
- Course Service
- Enrollment Service
- AI Service
- Notification Service

## Infrastructure Services

- Eureka Server
- API Gateway

---

# 2. Auth Service

## Purpose

Handles authentication and authorization.

---

## Database

AUTH_DB

---

## Tables

### credentials

- id
- email
- password_hash
- role
- enabled
- created_at
- updated_at

### refresh_tokens

- id
- user_id
- token
- expiry_date

### password_reset_tokens

- id
- user_id
- token
- expiry_date

### mfa_settings

- id
- user_id
- enabled
- secret

---

## APIs

### Authentication APIs

```http
POST /api/auth/register/student
POST /api/auth/register/instructor
POST /api/auth/login
POST /api/auth/logout
POST /api/auth/refresh-token
POST /api/auth/forgot-password
POST /api/auth/reset-password
POST /api/auth/mfa/enable
POST /api/auth/mfa/verify
```

### Response Objects

```json
{
  "accessToken": "jwt-token",
  "refreshToken": "refresh-token",
  "role": "STUDENT"
}
```

---

# 3. User Service

## Purpose

Profile and user management.

---

## Database

USER_DB

---

## Tables

### users

- id
- auth_user_id
- first_name
- last_name
- email
- phone
- profile_image_url
- bio
- created_at

### instructor_profiles

- id
- user_id
- skills
- experience
- linkedin_url
- approval_status
- approved_by
- approved_at

### admin_profiles

- id
- user_id

---

## APIs

### User APIs

```http
GET    /api/users/profile
PUT    /api/users/profile
POST   /api/users/profile/image
```

### Instructor APIs

```http
GET    /api/instructors/pending
PUT    /api/instructors/{id}/approve
PUT    /api/instructors/{id}/reject
GET    /api/instructors/{id}
```

### Admin APIs

```http
GET /api/admin/users
GET /api/admin/metrics
```

---

# 4. Course Service

## Purpose

Course and content management.

---

## Database

COURSE_DB

---

## Tables

### courses

- id
- title
- description
- category
- level
- instructor_id
- status
- created_at

### lessons

- id
- course_id
- title
- content
- lesson_order
- status

### articles

- id
- course_id
- title
- content

### youtube_links

- id
- course_id
- title
- youtube_url

---

## APIs

### Course APIs

```http
POST   /api/courses
PUT    /api/courses/{id}
GET    /api/courses
GET    /api/courses/{id}
DELETE /api/courses/{id}
PUT    /api/courses/{id}/publish
```

### Lesson APIs

```http
POST   /api/lessons
PUT    /api/lessons/{id}
GET    /api/lessons/{id}
PUT    /api/lessons/{id}/publish
```

### Search APIs

```http
GET /api/courses/search
```

---

# 5. Enrollment Service

## Purpose

Enrollment and progress tracking.

---

## Database

ENROLLMENT_DB

---

## Tables

### enrollments

- id
- student_id
- course_id
- enrolled_at
- status

### lesson_progress

- id
- enrollment_id
- lesson_id
- completed
- completed_at

### course_progress

- id
- enrollment_id
- completion_percentage
- last_accessed

---

## APIs

### Enrollment APIs

```http
POST /api/enrollments
GET  /api/enrollments/my-courses
GET  /api/enrollments/{courseId}
```

### Progress APIs

```http
PUT /api/progress/lesson
GET /api/progress/{courseId}
```

---

# 6. AI Service

## Purpose

Agentic AI orchestration and execution.

---

## Database

AI_DB

---

## Vector Database

PGVector

---

## Tables

### ai_conversations

- id
- user_id
- session_id
- prompt
- response
- created_at

### ai_tool_execution

- id
- conversation_id
- tool_name
- execution_time
- status

### ai_audit_logs

- id
- prompt
- response
- retrieved_context
- token_usage
- duration

### embeddings_metadata

- id
- content_type
- content_id
- vector_reference
- created_at

---

## Supported Features

### AI Tutor

```http
POST /api/ai/tutor
```

### Quiz Generator

```http
POST /api/ai/quiz
```

### Summary Generator

```http
POST /api/ai/summary
```

### Interview Coach

```http
POST /api/ai/interview
```

### Learning Advisor

```http
POST /api/ai/advisor
```

### Course Builder

```http
POST /api/ai/course-builder
```

---

## Tool Registry

### SearchCourseTool

Purpose:

Search available courses.

---

### GetLessonTool

Purpose:

Fetch lesson content.

---

### EnrollCourseTool

Purpose:

Enroll student into course.

---

### KnowledgeRetrievalTool

Purpose:

Retrieve relevant RAG chunks.

---

### SummaryTool

Purpose:

Generate lesson summary.

---

### QuizTool

Purpose:

Generate quizzes.

---

### ProgressAnalyzerTool

Purpose:

Analyze learning progress.

---

### InternetSearchTool

Purpose:

Perform Tavily search.

---

# 7. Notification Service

## Purpose

Notification management and delivery.

---

## Database

NOTIFICATION_DB

---

## Tables

### notifications

- id
- user_id
- title
- message
- type
- read_status
- created_at

### email_notifications

- id
- user_id
- email
- subject
- status
- sent_at

---

## APIs

### Notification APIs

```http
GET /api/notifications
PUT /api/notifications/{id}/read
```

---

# 8. RabbitMQ Design

## Exchanges

### lms.events.exchange

Purpose:

Main event exchange.

---

## Queues

### user.registered.queue

Consumes:

- UserRegisteredEvent

### instructor.approved.queue

Consumes:

- InstructorApprovedEvent

### course.published.queue

Consumes:

- CoursePublishedEvent

### enrollment.created.queue

Consumes:

- EnrollmentCreatedEvent

### content.uploaded.queue

Consumes:

- ContentUploadedEvent

---

# 9. Event Contracts

## UserRegisteredEvent

```json
{
  "userId": 1,
  "email": "user@email.com",
  "role": "STUDENT"
}
```

---

## InstructorApprovedEvent

```json
{
  "userId": 10,
  "approvedAt": "timestamp"
}
```

---

## CoursePublishedEvent

```json
{
  "courseId": 100,
  "courseName": "Spring Boot"
}
```

---

# 10. Security Design

## Authentication

- JWT Access Tokens
- Refresh Tokens
- MFA Support
- BCrypt Password Hashing

## Authorization

Roles:

- ADMIN
- INSTRUCTOR
- STUDENT

## Security Enforcement

### Gateway

- JWT Validation
- Request Filtering

### Service Layer

- Method-Level Authorization
- Resource Ownership Checks

---

# 11. API Gateway Design

## Responsibilities

- Request Routing
- JWT Validation
- Rate Limiting
- Correlation ID Injection
- Centralized Logging

### Routes

```text
/auth/**           -> Auth Service
/users/**          -> User Service
/courses/**        -> Course Service
/enrollments/**    -> Enrollment Service
/ai/**             -> AI Service
/notifications/**  -> Notification Service
```

---

# 12. Eureka Service Discovery

## Responsibilities

- Service Registration
- Service Discovery
- Load Balancing Support
- Dynamic Endpoint Resolution

---

# 13. Observability Design

## Zipkin

Tracks:

- Request Traces
- Service Dependencies
- Latency Analysis

## Prometheus

Collects:

- API Metrics
- JVM Metrics
- RabbitMQ Metrics
- AI Metrics

## Grafana

Dashboards:

- Service Health
- API Monitoring
- AI Usage
- Queue Monitoring
- Database Monitoring

---

# 14. Sequence Flows

## Student Enrollment Flow

```text
Student
  ↓
Frontend
  ↓
Gateway
  ↓
Enrollment Service
  ↓
EnrollmentCreatedEvent
  ↓
RabbitMQ
  ↓
Notification Service
```

---

## AI Tutor Flow

```text
Student Question
      ↓
AI Service
      ↓
KnowledgeRetrievalTool
      ↓
PGVector
      ↓
Relevant Chunks
      ↓
LLM
      ↓
Response
      ↓
Audit Storage
```

---

# 15. Design Patterns Used

## Microservices

- Independent deployment
- Independent scaling

## CQRS (Lightweight)

- Read APIs
- Write APIs

## Outbox Pattern

- Reliable event publishing

## Circuit Breaker

- Service failure handling

## Retry Pattern

- RabbitMQ consumer retries

## RAG Pattern

- Context-aware AI responses

## Tool Calling Pattern

- Agentic workflow execution

---

# 16. Future Enhancements

- OAuth2 / SSO
- Certificate Generation
- Mobile Application
- Live Classes
- Multi-Agent AI
- Kubernetes Deployment
- Multi-Tenant LMS
- Voice-Based AI Tutor
