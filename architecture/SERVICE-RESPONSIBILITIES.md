# Service Responsibility Matrix

## Project

**Agentic AI LMS Platform**

---

# Purpose

This document defines ownership boundaries for each microservice.

### Primary Goals

- Clear Domain Ownership
- Loose Coupling
- Independent Scalability
- Independent Deployment
- Database Isolation
- Event-Driven Communication

---

# Auth Service

## Owns

Authentication and Authorization

## Responsibilities

- Student Registration
- Instructor Registration
- Login
- Logout
- JWT Generation
- Refresh Token Management
- Password Reset
- Forgot Password
- MFA Configuration
- Role Management

## Roles

- ADMIN
- INSTRUCTOR
- STUDENT

## Database

`AUTH_DB`

## Tables

- credentials
- refresh_tokens
- password_reset_tokens
- mfa_settings

## Events Published

- UserRegisteredEvent

## Events Consumed

- None

---

# User Service

## Owns

User Profiles and Instructor Verification

## Responsibilities

- Student Profile Management
- Instructor Profile Management
- Admin Profile Management
- Instructor Verification
- Instructor Approval
- Profile Image Management
- Skills Management
- Experience Information
- User Preferences Management

## Database

`USER_DB`

## Tables

- users
- profiles
- instructor_profiles
- user_preferences

## Events Published

- InstructorApprovedEvent

## Events Consumed

- UserRegisteredEvent

---

# Course Service

## Owns

Learning Content Domain

## Responsibilities

- Course Creation
- Course Publishing
- Course Updates
- Course Archival
- Lesson Creation
- Lesson Management
- Article Management
- Video Content Management
- Student Enrollment
- Learning Progress Tracking
- Course Completion Tracking
- Course Analytics
- Razorpay Test Payment Tracking

## Database

`COURSE_DB`

## Tables

- courses
- lessons
- enrollments
- progress
- payments

## Events Published

- ContentUploadedEvent
- CoursePublishedEvent
- EnrollmentCreatedEvent

## Events Consumed

- None

---

# AI Service

## Owns

Agentic AI Platform

## Responsibilities

- AI Tutor
- Quiz Generation
- Summary Generation
- Interview Coach
- Learning Advisor
- Course Builder
- Tool Calling
- RAG Processing
- Tavily Integration
- AI Audit Trail
- Prompt Tracking
- LLM Usage Tracking

## Database

`AI_DB`

## Tables

- chat_history
- agent_execution_history
- tool_execution_audit
- rag_query_audit
- ai_usage_metrics

## Vector Store

`PGVector`

### Vector Tables

- vector_documents

## Events Published

Future Events:

- QuizGeneratedEvent
- RecommendationGeneratedEvent
- InterviewCompletedEvent

## Events Consumed

- ContentUploadedEvent

---

# Notification Service

## Owns

Notification Delivery

## Responsibilities

- Bell Notifications
- Email Notifications
- Notification History
- Read / Unread Tracking
- Notification Preferences

## Database

`NOTIFICATION_DB`

## Tables

- notifications
- email_notifications

## Events Published

Future Events:

- NotificationDeliveredEvent

## Events Consumed

- InstructorApprovedEvent
- EnrollmentCreatedEvent
- CoursePublishedEvent

---

# Service Communication Rules

## Auth Service

### May Communicate With

```text
User Service
```

### Purpose

- Profile Creation
- User Validation

---

## User Service

### May Communicate With

```text
Auth Service
```

### Purpose

- Identity Verification

---

## Course Service

### May Communicate With

```text
User Service
```

### Purpose

- Instructor Validation
- Student Validation
- Profile Retrieval

---

## AI Service

### May Communicate With

```text
Course Service
User Service
```

### Purpose

- Retrieve Course Content
- Retrieve Learning Progress
- Retrieve User Information
- Build Learning Recommendations

---

## Notification Service

### Communication Strategy

```text
RabbitMQ Events Preferred
```

### Purpose

- Event Consumption
- Notification Generation

---

# Event Ownership Matrix

| Event | Producer | Consumer |
|---------|----------|----------|
| UserRegisteredEvent | Auth Service | User Service |
| InstructorApprovedEvent | User Service | Notification Service |
| ContentUploadedEvent | Course Service | AI Service |
| CoursePublishedEvent | Course Service | Notification Service |
| EnrollmentCreatedEvent | Course Service | Notification Service |

---

# Database Ownership Rules

## Allowed

- REST APIs
- OpenFeign Clients
- RabbitMQ Events

## Forbidden

- Shared Databases
- Cross-Service Table Access
- Direct Database Queries Between Services

Every service owns its data exclusively.

---

# Dependency Direction

```text
Frontend
    │
    ▼

API Gateway
    │
    ▼

Auth Service
User Service
Course Service
AI Service
Notification Service

    │
    ▼

RabbitMQ

    │
    ▼

PostgreSQL
PGVector
```

---

# Architectural Principles

- Database Per Service
- Event-Driven Architecture
- Loose Coupling
- High Cohesion
- Independent Deployability
- Independent Scalability
- AI-First Design
- RAG-Based Knowledge Retrieval
- Tool Calling Architecture
- Observability by Default
- Auditability by Design
- Security First
