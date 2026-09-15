# API Contracts

## Project

Agentic AI LMS Platform

---

# API Standards

## Base URL

```text
/api
```

## Response Format

### Success

```json
{
  "success": true,
  "message": "Operation completed successfully",
  "data": {}
}
```

### Error

```json
{
  "success": false,
  "message": "Validation failed",
  "errorCode": "VALIDATION_ERROR"
}
```

---

# Auth Service APIs

## Register Student

```http
POST /api/auth/register/student
```

### Request

```json
{
  "email": "student@mail.com",
  "password": "Password@123",
  "fullName": "John Doe"
}
```

---

## Register Instructor

```http
POST /api/auth/register/instructor
```

### Request

```json
{
  "email": "instructor@mail.com",
  "password": "Password@123",
  "fullName": "Jane Doe"
}
```

---

## Login

```http
POST /api/auth/login
```

### Request

```json
{
  "email": "student@mail.com",
  "password": "Password@123"
}
```

### Response

```json
{
  "accessToken": "jwt-token",
  "refreshToken": "refresh-token",
  "role": "STUDENT"
}
```

---

## Refresh Token

```http
POST /api/auth/refresh-token
```

---

## Forgot Password

```http
POST /api/auth/forgot-password
```

---

## Reset Password

```http
POST /api/auth/reset-password
```

---

# User Service APIs

## Get Profile

```http
GET /api/users/profile
```

---

## Update Profile

```http
PUT /api/users/profile
```

### Request

```json
{
  "fullName": "John Doe",
  "phone": "9876543210",
  "bio": "Java Developer"
}
```

---

## Upload Profile Image

```http
POST /api/users/profile/image
```

---

## Get Pending Instructors

```http
GET /api/instructors/pending
```

---

## Approve Instructor

```http
PUT /api/instructors/{id}/approve
```

---

## Reject Instructor

```http
PUT /api/instructors/{id}/reject
```

---

# Course Service APIs

## Create Course

```http
POST /api/courses
```

### Request

```json
{
  "title": "Spring Boot Masterclass",
  "description": "Complete Spring Boot Learning Path",
  "category": "Backend Development",
  "level": "Intermediate"
}
```

---

## Update Course

```http
PUT /api/courses/{courseId}
```

---

## Get All Courses

```http
GET /api/courses
```

---

## Get Course By Id

```http
GET /api/courses/{courseId}
```

---

## Publish Course

```http
PUT /api/courses/{courseId}/publish
```

---

## Archive Course

```http
PUT /api/courses/{courseId}/archive
```

---

## Create Lesson

```http
POST /api/lessons
```

### Request

```json
{
  "courseId": 1,
  "title": "Dependency Injection",
  "content": "Lesson Content",
  "contentType": "ARTICLE"
}
```

---

## Update Lesson

```http
PUT /api/lessons/{lessonId}
```

---

## Get Lesson

```http
GET /api/lessons/{lessonId}
```

---

## Enroll Course

```http
POST /api/enrollments
```

### Request

```json
{
  "courseId": 1
}
```

---

## Get My Courses

```http
GET /api/enrollments/my-courses
```

---

## Update Lesson Progress

```http
PUT /api/progress/lesson
```

### Request

```json
{
  "courseId": 1,
  "lessonId": 3,
  "completed": true
}
```

---

## Get Progress

```http
GET /api/progress/{courseId}
```

---

## Search Courses

```http
GET /api/courses/search?keyword=spring
```

---

# AI Service APIs

## AI Tutor

```http
POST /api/ai/tutor
```

### Request

```json
{
  "question": "Explain Dependency Injection"
}
```

---

## Generate Summary

```http
POST /api/ai/summary
```

### Request

```json
{
  "lessonId": 10
}
```

---

## Generate Quiz

```http
POST /api/ai/quiz
```

### Request

```json
{
  "lessonId": 10,
  "questionCount": 10
}
```

---

## Interview Coach

```http
POST /api/ai/interview
```

### Request

```json
{
  "topic": "Spring Boot"
}
```

---

## Learning Advisor

```http
POST /api/ai/advisor
```

### Request

```json
{
  "userId": 1
}
```

---

## Career Advisor

```http
POST /api/ai/career-advisor
```

### Request

```json
{
  "goal": "Become Java Backend Developer"
}
```

---

## Content Generator

```http
POST /api/ai/content-generator
```

### Request

```json
{
  "topic": "Spring Security",
  "contentType": "ARTICLE"
}
```

---

## Course Builder

```http
POST /api/ai/course-builder
```

### Request

```json
{
  "topic": "Java Microservices"
}
```

---

# Notification Service APIs

## Get Notifications

```http
GET /api/notifications
```

---

## Mark Notification As Read

```http
PUT /api/notifications/{notificationId}/read
```

---

# Security Requirements

All protected endpoints require:

```http
Authorization: Bearer <JWT_TOKEN>
```

---

# Content Types

Supported Values

```text
ARTICLE
VIDEO
MIXED
```

---

# User Roles

Supported Values

```text
ADMIN
INSTRUCTOR
STUDENT
```

---

# Course Status

Supported Values

```text
DRAFT
PUBLISHED
ARCHIVED
```

---

# Enrollment Status

Supported Values

```text
ACTIVE
COMPLETED
CANCELLED
```

---

# Error Codes

```text
VALIDATION_ERROR

UNAUTHORIZED

FORBIDDEN

RESOURCE_NOT_FOUND

COURSE_NOT_FOUND

LESSON_NOT_FOUND

USER_NOT_FOUND

AI_PROCESSING_ERROR

INTERNAL_SERVER_ERROR
```
