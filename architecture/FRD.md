# Functional Requirements Document (FRD)

# Project Name
## Agentic AI LMS Platform

---

# 1. Project Overview

The **Agentic AI LMS Platform** is an enterprise-grade Learning Management System (LMS) that combines traditional learning management capabilities with modern AI technologies, including:

- Agentic AI
- Tool Calling
- Retrieval-Augmented Generation (RAG)
- AI-Assisted Learning Workflows

The platform enables:

### Students
- Learn through courses, articles, and videos
- Interact with AI-powered learning assistants
- Track progress and receive personalized recommendations

### Instructors
- Create and manage learning content
- Generate educational materials using AI
- Monitor learner engagement and analytics

### Administrators
- Manage users and instructors
- Oversee platform operations
- Monitor AI and system usage

### Technology Stack
- Spring Boot
- Spring AI
- RabbitMQ
- PostgreSQL
- PGVector
- Tavily
- Prometheus
- Grafana
- Zipkin

---

# 2. User Roles

## 2.1 Student

A Student shall be able to:

1. Register an account
2. Login to the platform
3. Manage profile information
4. Enroll in courses
5. View lessons
6. Read articles
7. Watch learning videos
8. Interact with AI Tutor
9. Generate lesson summaries
10. Generate quizzes
11. Participate in AI mock interviews
12. View learning progress
13. Receive notifications

---

## 2.2 Instructor

An Instructor shall be able to:

1. Register an account
2. Maintain professional profile
3. Await admin approval
4. Create courses
5. Update courses
6. Publish courses
7. Add lessons
8. Upload articles
9. Add YouTube learning links
10. Generate course content using AI
11. Generate quizzes using AI
12. View enrolled students
13. View course analytics
14. Receive notifications

---

## 2.3 Administrator

An Administrator shall be able to:

1. Manage users
2. Approve instructors
3. Reject instructors
4. View system metrics
5. View AI usage statistics
6. View platform analytics
7. Manage course lifecycle
8. Monitor notifications

---

# 3. Authentication Requirements

## 3.1 Registration

The platform shall support:

- Student Registration
- Instructor Registration

---

## 3.2 Authentication

The platform shall support:

- User Login
- User Logout
- JWT-Based Authentication
- Refresh Token Support

---

## 3.3 Security

The platform shall support:

- Password encryption using BCrypt
- Forgot Password functionality
- Password Reset functionality
- Multi-Factor Authentication (MFA)

---

## 3.4 Authorization

Role-Based Access Control (RBAC) shall be implemented for:

- Student
- Instructor
- Admin

---

# 4. User Profile Management

Users shall be able to:

1. View profile
2. Update profile
3. Upload profile photo
4. Maintain contact information
5. Update biography

## Instructor Additional Information

Instructors shall maintain:

- Skills
- Experience
- LinkedIn Profile
- Approval Status

---

# 5. Course Management

## 5.1 Course Operations

Instructors shall be able to:

1. Create Course
2. Update Course
3. Publish Course
4. Archive Course

---

## 5.2 Lesson Operations

Instructors shall be able to:

1. Create Lesson
2. Update Lesson
3. Publish Lesson

---

## 5.3 Supported Content Types

The platform shall support:

- Articles
- Rich Text Content
- YouTube Learning Links

---

# 6. Enrollment Management

Students shall be able to:

1. Search available courses
2. Enroll in courses
3. View enrolled courses

## System Responsibilities

The system shall:

- Track enrollment status
- Maintain learning progress
- Monitor course completion

---

# 7. Notification Management

## 
