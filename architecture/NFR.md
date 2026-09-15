# Non-Functional Requirements (NFR)

# Project Name

## Agentic AI LMS Platform

---

# 1. Overview

This document defines the Non-Functional Requirements (NFRs) for the **Agentic AI LMS Platform**.

These requirements ensure that the platform remains:

- Secure
- Scalable
- Reliable
- Observable
- Maintainable
- Extensible
- High Performing

while supporting:

- Agentic AI Workflows
- Tool Calling
- Retrieval-Augmented Generation (RAG)
- Microservice-based Architecture
- Event-Driven Communication

---

# 2. Availability

The platform shall provide high availability for all core business services.

## Requirements

1. Services shall be available during business operating hours.
2. Failure of a single microservice shall not impact the overall platform.
3. Temporary AI provider outages shall not affect authentication or course-related functionalities.
4. Core LMS capabilities shall remain operational even when AI services are degraded.
5. Critical business services shall support graceful degradation.
6. Health endpoints shall be available for service monitoring.

---

# 3. Scalability

The platform shall support future horizontal scaling requirements.

## Requirements

1. Services shall be independently deployable.
2. Services shall be independently scalable.
3. AI workloads shall be isolated from business workloads.
4. RabbitMQ shall support asynchronous workload processing.
5. Database ownership shall remain isolated per service.
6. AI processing shall scale independently from LMS operations.

## Future Scalability Considerations

- Kubernetes Deployment
- Horizontal Pod Autoscaling (HPA)
- Cloud-Native Deployments
- Auto Scaling Groups
- Distributed Caching
- Multi-Region Deployment Support

---

# 4. Performance

## 4.1 Authentication Performance

| Operation | Maximum Response Time |
|------------|----------------------|
| Login | ≤ 2 Seconds |
| JWT Validation | ≤ 500 ms |
| Token Refresh | ≤ 1 Second |
| Logout | ≤ 1 Second |

---

## 4.2 Course Operations Performance

| Operation | Maximum Response Time |
|------------|----------------------|
| Course Retrieval | ≤ 1 Second |
| Course Search | ≤ 2 Seconds |
| Enrollment Creation | ≤ 2 Seconds |
| Progress Update | ≤ 2 Seconds |

---

## 4.3 AI Operations Performance

| Operation | Maximum Response Time |
|------------|----------------------|
| AI Tutor Response | ≤ 10 Seconds |
| RAG Retrieval | ≤ 3 Seconds |
| Quiz Generation | ≤ 15 Seconds |
| Summary Generation | ≤ 10 Seconds |
| Learning Recommendations | ≤ 8 Seconds |
| Interview Feedback | ≤ 15 Seconds |

---

## 4.4 Notification Performance

| Operation | Maximum Response Time |
|------------|----------------------|
| Event Delivery | ≤ 5 Seconds |
| Bell Notification Availability | ≤ 2 Seconds |
| Email Notification Dispatch | ≤ 10 Seconds |

---

# 5. Reliability

The platform shall handle failures gracefully.

## Requirements

1. Retry mechanisms shall be implemented for RabbitMQ consumers.
2. Message delivery reliability shall be ensured using the Outbox Pattern.
3. Circuit Breakers shall be implemented for inter-service communication.
4. Service failures shall be isolated.
5. Dead Letter Queues (DLQ) shall be supported for failed events.
6. Automatic recovery mechanisms shall be implemented where appropriate.

## Reliability Patterns

- Retry Pattern
- Circuit Breaker Pattern
- Outbox Pattern
- Dead Letter Queue (DLQ)
- Bulkhead Isolation
- Graceful Degradation

---

# 6. Security

The platform shall implement enterprise-grade security standards.

---

## 6.1 Authentication Security

The platform shall support:

1. JWT-Based Authentication
2. Refresh Token Support
3. BCrypt Password Encryption
4. Multi-Factor Authentication (MFA)
5. Session Expiration Enforcement
6. Token Revocation Support
7. Password Reset Workflows

---

## 6.2 Authorization Security

The platform shall implement Role-Based Access Control (RBAC).

### Supported Roles

- ADMIN
- INSTRUCTOR
- STUDENT

### Authorization Enforcement

Authorization shall be enforced at:

1. API Gateway Layer
2. Service Layer
3. Method Security Layer

---

## 6.3 Data Protection

The platform shall ensure:

1. Sensitive data is never logged.
2. Passwords are never stored in plaintext.
3. JWT and refresh tokens are protected.
4. Personal user information is secured.
5. API communications occur over HTTPS in production environments.
6. Database credentials are securely managed.
7. Input validation is enforced across all services.

---

# 7. Maintainability

The platform shall remain maintainable and extensible.

## Requirements

1. Domain-driven service ownership.
2. Loose coupling between services.
3. Event-driven communication patterns.
4. Documentation-first development.
5. Reusable AI workflows.
6. Standardized API contracts.
7. Centralized configuration management.
8. Consistent exception handling.

## Design Principles

- Clean Architecture
- SOLID Principles
- Domain-Driven Design (DDD)
- API-First Development
- Event-Driven Architecture

---

# 8. Observability

The platform shall provide complete operational visibility.

---

## 8.1 Distributed Tracing

### Technology

**Zipkin**

### Capabilities

1. End-to-end request tracing
2. Service dependency tracking
3. Distributed request correlation
4. AI workflow tracing
5. Cross-service latency monitoring

---

## 8.2 Metrics Collection

### Technology

**Prometheus**

### Collected Metrics

1. Request Count
2. Response Time
3. Error Rates
4. Queue Depth
5. Active Connections
6. Resource Utilization
7. AI Processing Metrics
8. LLM Usage Metrics

---

## 8.3 Monitoring Dashboards

### Technology

**Grafana**

### Dashboard Categories

1. Service Health Dashboard
2. API Performance Dashboard
3. AI Usage Dashboard
4. RabbitMQ Monitoring Dashboard
5. Infrastructure Dashboard
6. Database Dashboard
7. Security Dashboard

---

# 9. Auditability

The platform shall maintain comprehensive audit records.

---

## 9.1 User Audit

The following activities shall be stored:

- Login History
- Profile Updates
- Enrollment Activities
- Password Reset Events
- MFA Changes

---

## 9.2 AI Audit

The following AI records shall be maintained:

- User Prompts
- Agent Decisions
- Tool Invocations
- Retrieved RAG Context
- AI Responses
- Response Generation Time
- LLM Provider Information
- Token Usage Details

---

## 9.3 Administrative Audit

The following administrative activities shall be recorded:

- Instructor Approvals
- Instructor Rejections
- User Management Actions
- Course Lifecycle Operations
- Configuration Changes

---

# 10. Messaging Requirements

The platform shall use RabbitMQ for asynchronous communication.

## Requirements

1. Event-Driven Integration
2. Decoupled Service Communication
3. Reliable Event Delivery
4. Async AI Processing
5. Event Retry Support
6. Dead Letter Queue Support

---

## Supported Events

### UserRegisteredEvent

Triggered after successful user registration.

### InstructorApprovedEvent

Triggered when an instructor is approved.

### CoursePublishedEvent

Triggered when a course is published.

### EnrollmentCreatedEvent

Triggered when a learner enrolls in a course.

### ContentUploadedEvent

Triggered when new learning content is uploaded.

### NotificationCreatedEvent

Triggered when a new notification needs to be delivered.

---

# 11. AI Requirements

The AI platform shall support:

1. Agentic Workflows
2. Tool Calling
3. Retrieval-Augmented Generation (RAG)
4. Tavily-Powered Internet Search
5. Multi-LLM Integration
6. AI Workflow Auditing
7. Explainable AI Interactions

---

## AI Provider Flexibility

The architecture shall allow switching between providers with minimal code changes.

### Supported Providers

- Ollama
- Azure OpenAI
- OpenAI
- Enterprise LLM
- Future AI Providers

### Design Goal

Provider changes should require configuration updates rather than significant code modifications.

---

# 12. Data Storage Requirements

Each microservice shall maintain independent database ownership.

---

## Auth Service

### Database

`AUTH_DB`

### Purpose

- User Credentials
- Tokens
- MFA Configuration
- Authentication Logs

---

## User Service

### Database

`USER_DB`

### Purpose

- User Profiles
- Instructor Profiles
- Contact Information

---

## Course Service

### Database

`COURSE_DB`

### Purpose

- Courses
- Lessons
- Articles
- Learning Content

---

## Enrollment Service

### Database

`ENROLLMENT_DB`

### Purpose

- Enrollments
- Learning Progress
- Course Completion Records

---

## Notification Service

### Database

`NOTIFICATION_DB`

### Purpose

- User Notifications
- Notification History
- Delivery Status

---

## AI Service

### Database

`AI_DB`

### Purpose

- AI Conversations
- AI Audit Logs
- Tool Call History
- Agent Execution Records

---

## Vector Storage

### Technology

**PGVector**

### Purpose

1. Embedding Storage
2. Semantic Search
3. Vector Similarity Search
4. RAG Retrieval Operations

---

# 13. Deployment Requirements

The platform shall support local development and future cloud deployment.

---

## Current Environment

### Local Development

Components:

- PostgreSQL
- RabbitMQ
- Ollama
- Zipkin
- Prometheus
- Grafana

---

## Future Environment

### Cloud Deployment

Potential Targets:

- Microsoft Azure
- Amazon Web Services (AWS)
- Google Cloud Platform (GCP)

### Future Deployment Capabilities

- Docker
- Kubernetes
- Managed PostgreSQL
- Managed RabbitMQ
- CI/CD Pipelines

---

# 14. Disaster Recovery

The platform shall support recovery from operational failures.

## Requirements

1. Database backup mechanisms.
2. Audit log retention.
3. Event recovery through the Outbox Pattern.
4. Message replay capability.
5. Service restoration procedures.
6. Backup validation processes.

## Recovery Objectives

| Objective | Target |
|------------|---------|
| Recovery Point Objective (RPO) | ≤ 24 Hours |
| Recovery Time Objective (RTO) | ≤ 4 Hours |

---

# 15. Extensibility

The platform shall support future enhancements without major architectural changes.

## Potential Future Features

1. Mobile Applications
2. OAuth2 Integration
3. Single Sign-On (SSO)
4. Passwordless Authentication
5. Multi-Agent AI Systems
6. Certificate Generation
7. Live Classes
8. Webinar Integration
9. Kubernetes Deployment
10. Enterprise Tenant Support
11. Multi-Language Support
12. AI Voice Tutor
13. Video Transcription
14. AI Content Moderation

---

# 16. Compliance and Standards

The platform should align with the following engineering practices:

- RESTful API Standards
- OpenAPI / Swagger Documentation
- Secure Coding Practices
- OWASP Security Recommendations
- Centralized Logging Standards
- Enterprise Audit Requirements

---

# 17. Success Criteria

The platform shall be considered compliant with this NFR document when:

- Performance targets are consistently met.
- Service failures do not impact unrelated domains.
- AI workloads remain isolated from LMS workloads.
- Full observability is available through Grafana, Prometheus, and Zipkin.
- Security controls are enforced across all layers.
- Audit records are available for business and AI operations.
- Future scalability can be achieved without major architectural changes.
