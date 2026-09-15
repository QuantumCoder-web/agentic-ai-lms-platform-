# Low Level Design (LLD)

## Project Name

Agentic AI LMS Platform

---

# 1. Service Breakdown

## Business Services

- Auth Service
- User Service
- Course Service
- AI Service
- Notification Service

## Infrastructure Services

- API Gateway
- Eureka Server

---

# 2. Auth Service

## Purpose

Handles Authentication and Authorization.

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

### Registration

```http
POST /api/auth/register/student
POST /api/auth/register/instructor
```

### Authentication

```http
POST /api/auth/login
POST /api/auth/logout
POST /api/auth/refresh-token
```

### Password Management

```http
POST /api/auth/forgot-password
POST /api/auth/reset-password
```

### MFA

```http
POST /api/auth/mfa/enable
POST /api/auth/mfa/verify
```

---

## Events Published

```text
UserRegisteredEvent
```

---

## Events Consumed

None

---

# 3. User Service

## Purpose

Profile Management & Instructor Approval.

---

## Database

USER_DB

---

## Tables

### users

- id
- auth_user_id
- role
- status
- created_at

### profiles

- id
- user_id
- full_name
- email
- phone
- bio
- profile_image_url

### instructor_profiles

- id
- user_id
- skills
- experience
- linkedin_url
- approval_status

### user_preferences

- id
- user_id
- notifications_enabled
- email_enabled
- theme
- updated_at

---

## APIs

### Profile APIs

```http
GET  /api/users/profile
PUT  /api/users/profile
POST /api/users/profile/image
```

### Instructor APIs

```http
GET  /api/instructors/pending
GET  /api/instructors/{id}

PUT  /api/instructors/{id}/approve
PUT  /api/instructors/{id}/reject
```

### Admin APIs

```http
GET /api/admin/users
GET /api/admin/instructors
GET /api/admin/dashboard
```

---

## Events Consumed

```text
UserRegisteredEvent
```

---

## Events Published

```text
InstructorApprovedEvent
```

---

# 4. Course Service

## Purpose

Course, Lesson, Enrollment and Progress Management.

---

## Database

COURSE_DB

---

## Tables

### courses

- id
- title
- description
- instructor_id
- category
- level
- status
- created_at

### lessons

- id
- course_id
- title
- content
- content_type
- youtube_url
- lesson_order

### enrollments

- id
- student_id
- course_id
- enrollment_status
- enrolled_at

### progress

- id
- student_id
- course_id
- completion_percentage
- last_accessed
- updated_at

### payments

- id
- student_id
- course_id
- razorpay_order_id
- razorpay_payment_id
- amount
- status
- created_at

---

## Course APIs

```http
POST   /api/courses
PUT    /api/courses/{id}
GET    /api/courses
GET    /api/courses/{id}

PUT    /api/courses/{id}/publish
PUT    /api/courses/{id}/archive
```

---

## Lesson APIs

```http
POST /api/lessons
PUT  /api/lessons/{id}
GET  /api/lessons/{id}
```

---

## Enrollment APIs

```http
POST /api/enrollments

GET /api/enrollments/my-courses

GET /api/enrollments/{courseId}
```

---

## Progress APIs

```http
PUT /api/progress/lesson

GET /api/progress/{courseId}
```

---

## Search APIs

```http
GET /api/courses/search
```

---

## Events Published

```text
ContentUploadedEvent

CoursePublishedEvent

EnrollmentCreatedEvent
```

---

## Events Consumed

None

---

# 5. AI Service

## Purpose

Agentic AI Orchestration Layer.

---

## Database

AI_DB

---

## Tables

### chat_history

- id
- user_id
- session_id
- message_type
- content
- created_at

### agent_execution_history

- id
- user_id
- question
- tools_used
- execution_time
- response
- created_at

### tool_execution_audit

- id
- tool_name
- status
- execution_time
- created_at

### rag_query_audit

- id
- user_id
- query
- retrieved_chunks
- response
- created_at

### ai_usage_metrics

- id
- user_id
- llm_provider
- model_name
- prompt_tokens
- completion_tokens
- total_tokens
- execution_time
- created_at

---

## Vector Store

PGVector

### vector_documents

- id
- course_id
- lesson_id
- chunk_text
- embedding_vector
- created_at

---

## APIs

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

### Career Advisor

```http
POST /api/ai/career-advisor
```

### Content Generator

```http
POST /api/ai/content-generator
```

### Course Builder

```http
POST /api/ai/course-builder
```

---

# Agent Tools

### SearchCourseTool

Search courses.

### GetLessonTool

Fetch lesson content.

### EnrollCourseTool

Enroll student.

### KnowledgeRetrievalTool

Perform RAG retrieval.

### SummaryTool

Generate summaries.

### QuizTool

Generate quizzes.

### ProgressAnalyzerTool

Analyze learner progress.

### InternetSearchTool

Perform Tavily Search.

### CareerAdvisorTool

Generate career recommendations.

### ContentGeneratorTool

Generate educational content.

---

## Events Consumed

```text
ContentUploadedEvent
EnrollmentCreatedEvent
```

---

# 6. Notification Service

## Purpose

Notification Delivery & Tracking.

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
- status
- type
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

```http
GET /api/notifications

PUT /api/notifications/{id}/read
```

---

## Events Consumed

```text
InstructorApprovedEvent

CoursePublishedEvent

EnrollmentCreatedEvent
```

---

# 7. RabbitMQ Design

## Exchange

```text
lms.events.exchange
```

---

## Queues

### user.registered.queue

Consumes:

```text
UserRegisteredEvent
```

### instructor.approved.queue

Consumes:

```text
InstructorApprovedEvent
```

### course.published.queue

Consumes:

```text
CoursePublishedEvent
```

### enrollment.created.queue

Consumes:

```text
EnrollmentCreatedEvent
```

### content.uploaded.queue

Consumes:

```text
ContentUploadedEvent
```

---

# 8. API Gateway

## Responsibilities

- Request Routing
- JWT Validation
- Request Filtering
- Correlation ID Injection
- Security Enforcement

---

## Routes

```text
/auth/**          -> Auth Service

/users/**         -> User Service

/courses/**       -> Course Service

/ai/**            -> AI Service

/notifications/** -> Notification Service
```

---

# 9. Eureka Server

## Responsibilities

- Service Registration
- Service Discovery
- Dynamic Endpoint Resolution

---

## Registered Services

- API Gateway
- Auth Service
- User Service
- Course Service
- AI Service
- Notification Service

---

# 10. Security Design

## Authentication

- JWT Access Token
- Refresh Token
- MFA
- BCrypt

## Authorization

Roles:

- ADMIN
- INSTRUCTOR
- STUDENT

## Enforcement

### Gateway Layer

- JWT Validation

### Service Layer

- Method-Level Security
- Resource Ownership Validation

---

# 11. Observability

## Zipkin

- Distributed Tracing

## Prometheus

- Metrics Collection

## Grafana

Dashboards:

- Service Health
- AI Usage
- RabbitMQ Monitoring
- Database Monitoring
- API Performance

---

# 12. Design Patterns

- Microservices Architecture
- Event Driven Architecture
- Outbox Pattern
- Circuit Breaker
- Retry Pattern
- Tool Calling Pattern
- RAG Pattern
- API Gateway Pattern
- Service Discovery Pattern

---

# 13. Future Enhancements

- OAuth2 / SSO
- Passwordless Login
- Mobile App
- Live Classes
- Certificate Generation
- Multi-Agent AI
- Kubernetes Deployment
- Multi-Tenant LMS
