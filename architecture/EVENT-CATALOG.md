# Event Catalog

## Project

Agentic AI LMS Platform

---

# Overview

The platform uses RabbitMQ for asynchronous communication between microservices.

Goals:

- Loose Coupling
- Scalability
- Reliability
- Event-Driven Design

---

# Event: UserRegisteredEvent

## Description

Triggered when a new user successfully registers.

---

## Producer

Auth Service

---

## Consumers

- User Service

---

## Payload

```json
{
  "userId": 1,
  "email": "user@example.com",
  "role": "STUDENT",
  "createdAt": "2026-09-15T10:00:00"
}
```

---

## Purpose

- Create profile
- Initialize user preferences

---

# Event: InstructorApprovedEvent

## Description

Triggered when an administrator approves an instructor.

---

## Producer

User Service

---

## Consumers

- Notification Service

---

## Payload

```json
{
  "userId": 100,
  "approvedBy": 1,
  "approvedAt": "2026-09-15T10:30:00"
}
```

---

## Purpose

- Notify instructor
- Update UI notifications

---

# Event: EnrollmentCreatedEvent

## Description

Triggered when a student enrolls in a course.

---

## Producer

Course Service

---

## Consumers

- Notification Service
- AI Service

---

## Payload

```json
{
  "studentId": 10,
  "courseId": 101,
  "enrolledAt": "2026-09-15T11:00:00"
}
```

---

## Purpose

- Generate notifications
- Initialize learning recommendations

---

# Event: CoursePublishedEvent

## Description

Triggered when an instructor publishes a course.

---

## Producer

Course Service

---

## Consumers

- Notification Service

---

## Payload

```json
{
  "courseId": 101,
  "courseName": "Spring Boot Masterclass",
  "publishedAt": "2026-09-15T11:15:00"
}
```

---

## Purpose

- Notify enrolled students
- Notify followers/subscribers

---

# Event: ContentUploadedEvent

## Description

Triggered when content is uploaded to a course.

---

## Producer

Course Service

---

## Consumers

- AI Service

---

## Payload

```json
{
  "courseId": 101,
  "lessonId": 15,
  "contentType": "ARTICLE",
  "uploadedAt": "2026-09-15T11:30:00"
}
```

---

## Purpose

- Trigger chunking
- Generate embeddings
- Update vector store

---

# RabbitMQ Exchange

```text
lms.events.exchange
```

---

# Queues

```text
user.registered.queue

instructor.approved.queue

enrollment.created.queue

course.published.queue

content.uploaded.queue
```

---

# Event Design Principles

- Immutable Events
- Idempotent Consumers
- Loose Coupling
- Schema Versioning
- Retry Support
- Dead Letter Queue Ready
