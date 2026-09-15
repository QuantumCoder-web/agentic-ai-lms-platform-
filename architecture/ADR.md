# Architecture Decision Records (ADR)

## Project

Agentic AI LMS Platform

---

# ADR-001

## Title

Microservices Architecture

### Decision

Use Microservices instead of Monolith.

### Reason

- Independent deployment
- Independent scaling
- Better separation of concerns
- Easier AI service isolation

---

# ADR-002

## Title

Separate Auth Service and User Service

### Decision

Authentication and Profile Management are separated.

### Reason

Authentication concerns:

- Login
- JWT
- MFA
- Password Reset

User concerns:

- Profiles
- Skills
- Experience
- Instructor Approval

Different business domains.

---

# ADR-003

## Title

RabbitMQ for Event-Driven Communication

### Decision

Use RabbitMQ for asynchronous communication.

### Reason

- Loose Coupling
- Reliability
- Event Processing
- Future Scalability

---

# ADR-004

## Title

PostgreSQL as Primary Database

### Decision

Use PostgreSQL for all service databases.

### Reason

- Open Source
- Reliable
- Production Proven
- Works with PGVector

---

# ADR-005

## Title

PGVector for Vector Search

### Decision

Use PGVector for embeddings and semantic search.

### Reason

- Native PostgreSQL Integration
- Cost Effective
- Supports RAG Workflows
- Simplifies Architecture

---

# ADR-006

## Title

Spring AI for AI Integration

### Decision

Use Spring AI as AI orchestration layer.

### Reason

- Spring Ecosystem Alignment
- Tool Calling Support
- RAG Support
- Multiple LLM Support

---

# ADR-007

## Title

Tavily for Internet Search

### Decision

Use Tavily for real-time external knowledge retrieval.

### Reason

- Current Information
- Career Guidance
- Industry Research
- Interview Preparation

---

# ADR-008

## Title

RAG-Based Learning Assistant

### Decision

Use Retrieval-Augmented Generation for AI Tutor.

### Reason

- Reduces Hallucinations
- Uses Course Content
- Improves Accuracy
- Improves Explainability

---

# ADR-009

## Title

Agentic AI Architecture

### Decision

Implement Tool Calling based AI Agent.

### Reason

Supports:

- Multi-Step Reasoning
- Tool Selection
- Tool Execution
- Personalized Learning

---

# ADR-010

## Title

Observability First

### Decision

Implement monitoring and tracing from the beginning.

### Technologies

- Zipkin
- Prometheus
- Grafana

### Reason

- Faster Debugging
- Operational Visibility
- Service Health Monitoring

---

# ADR-011

## Title

Database Per Service

### Decision

Each service owns its database.

### Reason

- Strong Ownership
- Loose Coupling
- Independent Evolution
- Better Scalability

---

# ADR-012

## Title

Course Service Owns Enrollment

### Decision

Enrollment and Progress Tracking remain inside Course Service.

### Reason

- Simpler Architecture
- Reduced Service Count
- Sufficient for LMS Scope
- Faster Development

Enrollment Service intentionally not created.
