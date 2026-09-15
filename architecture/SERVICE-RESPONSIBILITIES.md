# Service Responsibility Matrix

## Project

Agentic AI LMS Platform

---

# Purpose

This document defines ownership boundaries for each microservice.

The primary goals are:

- Clear Domain Ownership
- Loose Coupling
- Independent Scalability
- Independent Deployment
- Database Isolation

---

# Auth Service

## Owns

Authentication and Authorization

### Responsibilities

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

### Roles

- ADMIN
- INSTRUCTOR
- STUDENT

### Database

`AUTH_DB`

### Tables

- credentials
- refresh_tokens
- password_reset_tokens
- mfa_settings

### Publishes Events

- UserRegisteredEvent

### Consumes Events

None

---

# User Service

## Owns

User Profiles and Instructor Verification

### Responsibilities

- Student Profile Management
- Instructor Profile Management
- Admin Profile Management
- Instructor Verification
- Instructor Approval
- Profile Image Management
- Skills Management
- Experience Information

### Database

`USER_DB`

### Tables

- users
- profiles
- instructor_profiles

### Publishes Events

- InstructorApprovedEvent

### Consumes Events

- UserRegisteredEvent

---

# Course Service

## Owns

Learning Content Domain

### Responsibilities

- Course Creation
- Course Publishing
- Course Updates
- Course Archival
- Lesson Creation
- Lesson Management
- Article Management
- YouTube Content Management
- Course Analytics
- Razorpay Test Payment Tracking

### Database

`COURSE_DB`

### Tables

- courses
- lessons
- articles
- youtube_links
- payments

### Publishes Events

- ContentUploadedEvent
- CoursePublishedEvent

### Consumes Events

None

---

# Enrollment Service

## Owns

Enrollment and Learning Progress

### Responsibilities

- Student Enrollment
- Course Enrollment Tracking
- Learning Progress Tracking
- Course Completion Tracking
- Progress Analytics

### Database

`ENROLLMENT_DB`

### Tables

- enrollments
- lesson_progress
- course_progress

### Publishes Events

- EnrollmentCreatedEvent
- CourseCompletedEvent

### Consumes Events

None

---

# AI Service

## Owns

Agentic AI Operations

### Responsibilities

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

### Database

`AI_DB`

### Tables

- chat_history
- ai_conversations
- tool_execution_audit
- agent_execution_history
- ai_audit_logs

### Vector Storage

`PGVector`

### Publishes Events

Future:

- QuizGeneratedEvent
- RecommendationGeneratedEvent
- InterviewCompletedEvent

### Consumes Events

- ContentUploadedEvent

---

# Notification Service

## Owns

Notification Delivery

### Responsibilities

- Bell Notifications
- Email Notifications
- Notification History
- Read / Unread Tracking
- Notification Preferences

### Database

`NOTIFICATION_DB`

### Tables

- notifications
- email_notifications

### Publishes Events

Future:

- NotificationDeliveredEvent

### Consumes Events

- InstructorApprovedEvent
- EnrollmentCreatedEvent
- 
