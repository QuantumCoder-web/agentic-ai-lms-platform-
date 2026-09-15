# High Level Design (HLD)

# Project Name

## Agentic AI LMS Platform

---

# 1. Purpose

The Agentic AI LMS Platform is an enterprise-grade Learning Management System (LMS) built using a microservices architecture. The platform combines traditional LMS functionality with modern AI capabilities such as Agentic AI, Tool Calling, Retrieval-Augmented Generation (RAG), and external knowledge retrieval.

The system enables:

- Students to learn through courses and AI assistance.
- Instructors to create and manage learning content.
- Administrators to govern platform operations.
- AI agents to perform intelligent learning workflows.

---

# 2. Architecture Goals

The architecture is designed to achieve:

- Scalability
- High Availability
- Service Isolation
- Event-Driven Communication
- AI Extensibility
- Observability
- Security
- Future Cloud Readiness

---

# 3. System Architecture Overview

## Infrastructure Layer

- Eureka Server
- API Gateway

## Business Services

- Auth Service
- User Service
- Course Service
- AI Service
- Notification Service

## Messaging Layer

- RabbitMQ

## Data Layer

- PostgreSQL
- PGVector

## AI Layer

- Spring AI
- Tool Calling
- RAG Engine
- Tavily Search
- Ollama / Enterprise LLM

## Observability Layer

- Zipkin
- Prometheus
- Grafana

---

# 4. High Level Architecture Diagram

```
+--------------------------------------------------+
|                  React Frontend                  |
+-------------------------+------------------------+
                          |
                          v
+--------------------------------------------------+
|                  API Gateway                     |
+--------------------------------------------------+
                          |
                          v
+--------------------------------------------------+
|                 Eureka Server                    |
+--------------------------------------------------+

        |            |            |           |
        v            v            v           v

+-----------+ +-----------+ +-----------+ +-----------+
|   Auth    | |   User    | |  Course   | |    AI     |
|  Service  | |  Service  | |  Service  | |  Service  |
+-----------+ +-----------+ +-----------+ +-----------+
      |             |            |             |
      +-------------+------------+-------------+
                            |
                            v
                     +-------------+
                     | RabbitMQ    |
                     +-------------+
                            |
                            v
                  +----------------------+
                  | Notification Service |
                  +----------------------+

----------------------------------------------------
                     PostgreSQL
----------------------------------------------------

AUTH_DB
USER_DB
COURSE_DB
NOTIFICATION_DB
AI_DB

----------------------------------------------------
                     PGVector
----------------------------------------------------

Embeddings
Similarity Search
RAG Context Retrieval

----------------------------------------------------
                  Observability
----------------------------------------------------

Zipkin
Prometheus
Grafana
```

---

# 5. Service Responsibilities

## Auth Service

### Purpose

Authentication and Authorization

### Responsibilities

- User Registration
- User Login
- JWT Generation
- Refresh Tokens
- MFA Support
- Forgot Password
- Password Reset
- Role Management

### Database

`AUTH_DB`

---

## User Service

### Purpose

Profile Management

### Responsibilities

- Student Profiles
- Instructor Profiles
- Admin Profiles
- Profile Updates
- Instructor Approval Workflow
- Skills Management
- Experience Management

### Database

`USER_DB`

---

## Course Service

### Purpose

Learning Content Management

### Responsibilities

- Course CRUD
- Lesson CRUD
- Article Management
- YouTube Content Management
- Enrollment Management
- Progress Tracking
- Razorpay Test Integration

### Database

`COURSE_DB`

---

## AI Service

### Purpose

Agentic AI Orchestration

### Responsibilities

- AI Tutor
- Quiz Generation
- Lesson Summarization
- Interview Coach
- Learning Advisor
- AI Course Builder
- Tool Calling
- RAG Retrieval
- Tavily Search Integration
- AI Auditing

### Database

`AI_DB`

### Vector Storage

`PGVector`

---

## Notification Service

### Purpose

Notification Delivery

### Responsibilities

- Bell Notifications
- Email Notifications
- Notification History
- Event Processing

### Database

`NOTIFICATION_DB`

---

# 6. Database Ownership

| Service | Database |
|----------|-----------|
| Auth Service | AUTH_DB |
| User Service | USER_DB |
| Course Service | COURSE_DB |
| AI Service | AI_DB |
| Notification Service | NOTIFICATION_DB |

### Principle

Each service owns its database.

No cross-service table access is allowed.

Communication must happen via:

- REST APIs
- RabbitMQ Events

---

# 7. Communication Architecture

## Synchronous Communication

Technology:

- OpenFeign

### Examples

Course Service → User Service

AI Service → Course Service

AI Service → User Service

Auth Service → User Service

---

## Asynchronous Communication

Technology:

- RabbitMQ

### Benefits

- Loose Coupling
- Event Processing
- Reliability
- Scalability

---

# 8. RabbitMQ Event Architecture

## Published Events

### UserRegisteredEvent

Producer:

- Auth Service

Consumers:

- User Service
- Notification Service

---

### InstructorApprovedEvent

Producer:

- User Service

Consumers:

- Notification Service

---

### CoursePublishedEvent

Producer:

- Course Service

Consumers:

- Notification Service

---

### EnrollmentCreatedEvent

Producer:

- Course Service

Consumers:

- Notification Service
- AI Service

---

### ContentUploadedEvent

Producer:

- Course Service

Consumers:

- AI Service

---

# 9. Authentication Flow

```
User
 │
 ▼
API Gateway
 │
 ▼
Auth Service
 │
 ▼
JWT Generated
 │
 ▼
JWT Returned
 │
 ▼
Subsequent Requests
 │
 ▼
Gateway Validation
 │
 ▼
Business Services
```

---

# 10. Instructor Approval Workflow

```
Instructor Registration
        │
        ▼
Auth Service
        │
        ▼
UserRegisteredEvent
        │
        ▼
User Service
        │
        ▼
Status = PENDING
        │
        ▼
Admin Approval
        │
        ▼
InstructorApprovedEvent
        │
        ▼
Notification Service
```

---

# 11. Content Ingestion & RAG Pipeline

```
Course Content Upload
          │
          ▼
Course Service
          │
          ▼
ContentUploadedEvent
          │
          ▼
AI Service
          │
          ▼
Chunking
          │
          ▼
Embedding Generation
          │
          ▼
PGVector Storage
```

---

# 12. RAG Architecture

```
User Question
       │
       ▼
Embedding Generation
       │
       ▼
PGVector Similarity Search
       │
       ▼
Top Matching Chunks
       │
       ▼
Prompt Construction
       │
       ▼
LLM
       │
       ▼
Response
```

---

# 13. Tool Calling Architecture

```
User Prompt
      │
      ▼
Agent
      │
      ▼
Intent Detection
      │
      ▼
Tool Selection
      │
      ▼
Tool Execution
      │
      ▼
Final Response
```

### Supported Tools

- SearchCourseTool
- GetLessonTool
- EnrollCourseTool
- KnowledgeRetrievalTool
- SummaryTool
- QuizTool
- ProgressAnalyzerTool
- InternetSearchTool

---

# 14. Tavily Integration

### Use Cases

- Current Technology Trends
- Industry Research
- Career Guidance
- Learning Roadmaps
- Interview Preparation

### Flow

```
Question
   │
   ▼
AI Agent
   │
   ▼
InternetSearchTool
   │
   ▼
Tavily
   │
   ▼
Results
   │
   ▼
LLM
   │
   ▼
Final Response
```

---

# 15. Security Architecture

### Authentication

- JWT Authentication
- Refresh Tokens
- BCrypt Password Hashing
- MFA

### Authorization

RBAC:

- ADMIN
- INSTRUCTOR
- STUDENT

### Enforcement

- Gateway
- Service Layer

---

# 16. AI Audit Architecture

Store:

- User Prompts
- Agent Decisions
- Tool Invocations
- Retrieved Context
- Tavily Results
- Generated Responses
- Response Time
- Token Consumption

### Goals

- Explainability
- Traceability
- Compliance
- Monitoring

---

# 17. Observability Architecture

## Zipkin

- Distributed Tracing
- Request Correlation

## Prometheus

- Metrics Collection
- Application Monitoring

## Grafana

- Dashboards
- AI Monitoring
- Queue Monitoring
- Service Monitoring

---

# 18. Deployment Architecture

### Local Development

- Spring Boot Services
- PostgreSQL
- RabbitMQ
- Ollama
- Zipkin
- Prometheus
- Grafana

### Future Deployment

- Docker
- Kubernetes
- Azure
- AWS
- GCP

---

# 19. Key Architectural Benefits

- Microservices Architecture
- Agentic AI Support
- Tool Calling
- RAG-Based Learning
- Event-Driven Design
- Independent Scalability
- High Observability
- AI Traceability
- Cloud Readiness
- Future Multi-Agent Support
