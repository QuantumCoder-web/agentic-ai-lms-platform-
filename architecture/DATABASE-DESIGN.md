# Database Design

## Project

**Agentic AI LMS Platform**

---

# Database Strategy

Each microservice owns its database.

No service is allowed to directly access another service database.

Communication occurs through:

- REST APIs
- OpenFeign
- RabbitMQ Events

---

# AUTH_DB

### Purpose

Authentication and Authorization

---

## Table: credentials

### Columns

- id (PK)
- email (Unique)
- password_hash
- role
- enabled
- account_non_locked
- created_at
- updated_at

### Role Values

- ADMIN
- INSTRUCTOR
- STUDENT

---

## Table: refresh_tokens

### Columns

- id (PK)
- user_id
- token
- expiry_date
- created_at

---

## Table: password_reset_tokens

### Columns

- id (PK)
- user_id
- token
- expiry_date
- used

---

## Table: mfa_settings

### Columns

- id (PK)
- user_id
- enabled
- secret_key
- created_at

---

# USER_DB

### Purpose

Profile Management

---

## Table: users

### Columns

- id (PK)
- auth_user_id
- role
- status
- created_at

### Status Values

#### Instructor

- PENDING_APPROVAL
- APPROVED
- REJECTED

#### Student

- ACTIVE

#### Admin

- ACTIVE

---

## Table: profiles

### Columns

- id (PK)
- user_id
- full_name
- email
- phone
- bio
- profile_image_url
- created_at
- updated_at

---

## Table: instructor_profiles

### Columns

- id (PK)
- user_id
- skills
- experience
- linkedin_url
- approval_notes

---

# COURSE_DB

### Purpose

Learning Domain

---

## Table: courses

### Columns

- id (PK)
- title
- description
- instructor_id
- status
- created_at
- updated_at

### Status Values

- DRAFT
- PUBLISHED
- ARCHIVED

---

## Table: lessons

### Columns

- id (PK)
- course_id
- title
- article_content
- youtube_url
- lesson_order
- created_at

---

## Table: enrollments

### Columns

- id (PK)
- student_id
- course_id
- enrollment_status
- enrolled_at

### Status Values

- ACTIVE
- COMPLETED
- CANCELLED

---

## Table: progress

### Columns

- id (PK)
- student_id
- course_id
- completion_percentage
- last_accessed
- updated_at

---

## Table: payments

### Purpose

Dummy Razorpay Test Tracking

### Columns

- id (PK)
- student_id
- course_id
- razorpay_order_id
- razorpay_payment_id
- amount
- status
- created_at

### Status Values

- PENDING
- SUCCESS
- FAILED

---

# AI_DB

### Purpose

Agentic AI Operations

---

## Table: chat_history

### Columns

- id (PK)
- user_id
- session_id
- message_type
- content
- created_at

### Message Types

- USER
- ASSISTANT

---

## Table: agent_execution_history

### Columns

- id (PK)
- user_id
- question
- tools_used
- execution_time
- response
- created_at

---

## Table: tool_execution_audit

### Columns

- id (PK)
- tool_name
- status
- execution_time
- created_at

### Status Values

- SUCCESS
- FAILED

---

## Table: rag_query_audit

### Columns

- id (PK)
- user_id
- query
- retrieved_chunks
- response
- created_at

---

# PGVECTOR

### Purpose

- Semantic Search
- RAG
- Embeddings

---

## Table: document_chunks

### Columns

- id (PK)
- course_id
- lesson_id
- chunk_text
- created_at

---

## Table: document_embeddings

### Columns

- id (PK)
- chunk_id
- embedding_vector

---

# NOTIFICATION_DB

### Purpose

Notification Management

---

## Table: notifications

### Columns

- id (PK)
- user_id
- title
- message
- status
- notification_type
- created_at

### Status Values

- READ
- UNREAD

### Notification Types

- ENROLLMENT
- COURSE
- APPROVAL
- SYSTEM
- AI

---

# Relationships

## Auth Service

```text
credentials
    |
    |
    v
users
    |
    |
    v
profiles
```

---

## Course Service

```text
courses
   |
   |
   v
lessons

courses
   |
   |
   v
enrollments

enrollments
   |
   |
   v
progress
```

---

## AI Service

```text
document_chunks
        |
        |
        v
document_embeddings
```

---

# Database Principles

- Service-Owned Databases
- No Cross-Service Database Access
- Asynchronous Event Integration
- Auditability
- Traceability
- AI Explainability
