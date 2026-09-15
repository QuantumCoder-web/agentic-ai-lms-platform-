# Functional Requirements Document (FRD)

# Project Name

## Agentic AI LMS Platform

---

# 1. Project Overview

The Agentic AI LMS Platform is an enterprise-grade Learning Management System (LMS) that combines traditional learning management capabilities with advanced AI technologies.

The platform leverages:

- Agentic AI
- Tool Calling
- Retrieval-Augmented Generation (RAG)
- Tavily Search Integration
- AI-Assisted Learning Workflows

The system enables:

## Students

- Learn through courses, lessons, articles, and videos
- Interact with AI-powered learning assistants
- Track learning progress
- Receive personalized recommendations

## Instructors

- Create and manage learning content
- Generate educational material using AI
- Monitor learner engagement
- View course analytics

## Administrators

- Manage users and instructors
- Monitor platform operations
- Oversee AI usage and system metrics

---

# 2. User Roles

## 2.1 Student

A Student shall be able to:

1. Register an account
2. Login to the platform
3. Manage profile information
4. Enroll in courses
5. View lessons
6. Read learning articles
7. Watch educational videos
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
3. Await administrator approval
4. Create courses
5. Update courses
6. Publish courses
7. Create lessons
8. Upload learning content
9. Add YouTube learning resources
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

## Registration

The platform shall support:

- Student Registration
- Instructor Registration

---

## Authentication

The platform shall support:

- Login
- Logout
- JWT Authentication
- Refresh Tokens

---

## Security

The platform shall support:

- BCrypt Password Encryption
- Forgot Password
- Password Reset
- Multi-Factor Authentication (MFA)

---

## Authorization

Role-Based Access Control (RBAC) shall be implemented for:

- STUDENT
- INSTRUCTOR
- ADMIN

---

# 4. User Profile Management

Users shall be able to:

1. View Profile
2. Update Profile
3. Upload Profile Photo
4. Maintain Contact Information
5. Update Biography

## Instructor Additional Information

Instructors shall maintain:

- Skills
- Experience
- LinkedIn Profile
- Approval Status

---

# 5. Course Management

## Course Operations

Instructors shall be able to:

1. Create Course
2. Update Course
3. Publish Course
4. Archive Course

---

## Lesson Operations

Instructors shall be able to:

1. Create Lesson
2. Update Lesson
3. Publish Lesson

---

## Supported Content Types

The platform shall support:

- Articles
- Rich Text Content
- Video Content
- YouTube Learning Links

---

# 6. Enrollment Management

Students shall be able to:

1. Search Courses
2. Enroll In Courses
3. View Enrolled Courses

## System Responsibilities

The system shall:

- Track Enrollment Status
- Track Learning Progress
- Track Course Completion

---

# 7. Notification Management

## Bell Notifications

The platform shall support:

- Enrollment Notifications
- Instructor Approval Notifications
- Course Publication Notifications
- AI Activity Notifications

---

## Email Notifications

The platform shall support:

- Account Notifications
- Instructor Approval Notifications
- Enrollment Confirmations

---

# 8. AI Features

## 8.1 AI Tutor

Students shall be able to:

1. Ask course-related questions
2. Receive contextual answers
3. Learn using retrieved course content

Capabilities:

- RAG-powered responses
- Context-aware explanations
- Personalized assistance

---

## 8.2 AI Quiz Generator

The AI system shall:

1. Generate quizzes from lessons
2. Generate MCQs
3. Generate answer explanations

---

## 8.3 Lesson Summarizer

The AI system shall:

1. Summarize lessons
2. Summarize complete courses
3. Generate revision notes

---

## 8.4 Interview Coach

The AI system shall:

1. Conduct mock interviews
2. Ask technical questions
3. Evaluate answers
4. Generate feedback reports

---

## 8.5 Learning Advisor

The AI system shall:

1. Analyze student progress
2. Recommend learning paths
3. Suggest next learning activities

---

## 8.6 AI Course Builder

The AI system shall assist instructors in:

1. Generating course outlines
2. Creating lesson structures
3. Creating learning objectives

---

## 8.7 Career & Skill Advisor

The AI system shall:

1. Analyze learner skills
2. Identify skill gaps
3. Recommend career roadmaps
4. Suggest learning resources
5. Recommend technologies to learn

Examples:

- Become Java Backend Developer
- Become Full Stack Developer
- Become AI Engineer

---

## 8.8 AI Content Generator

The AI system shall assist instructors in:

1. Generating lesson content
2. Generating assignments
3. Creating coding exercises
4. Creating interview questions
5. Creating learning objectives

---

# 9. Retrieval Augmented Generation (RAG)

The platform shall support:

1. Content Chunking
2. Embedding Generation
3. Vector Storage
4. Similarity Search
5. Context-Aware Response Generation

## Knowledge Sources

- Articles
- Lessons
- Course Content

---

# 10. External Knowledge Search

The platform shall use Tavily for internet-assisted research.

Capabilities:

1. Current Information Retrieval
2. Industry Trend Analysis
3. Learning Resource Discovery
4. Technology Recommendations
5. Career Research

---

# 11. AI Agent Capabilities

The AI Agent shall:

1. Understand user intent
2. Select relevant tools
3. Execute tools
4. Combine retrieved information
5. Generate final responses

Capabilities:

- Multi-Step Reasoning
- Tool Orchestration
- RAG Retrieval
- Tavily Search
- Personalized Recommendations

---

# 12. Tool Calling Requirements

The AI Agent shall support:

## SearchCourseTool

Search available courses.

## GetLessonTool

Retrieve lesson content.

## EnrollCourseTool

Enroll a student in a course.

## KnowledgeRetrievalTool

Retrieve relevant RAG content.

## SummaryTool

Generate summaries.

## QuizTool

Generate quizzes.

## ProgressAnalyzerTool

Analyze learner progress.

## InternetSearchTool

Perform Tavily Search.

## CareerAdvisorTool

Generate career recommendations.

## ContentGeneratorTool

Generate educational content.

---

# 13. AI Audit & Traceability

The platform shall maintain:

1. User Prompts
2. AI Responses
3. Tool Invocations
4. Retrieved Context
5. Execution Duration
6. LLM Usage Statistics
7. Token Usage
8. AI Interaction History

Objectives:

- Explainability
- Compliance
- Monitoring
- Traceability

---

# 14. Event-Driven Architecture Requirements

The platform shall use RabbitMQ.

## Supported Events

### UserRegisteredEvent

Created after successful registration.

### InstructorApprovedEvent

Created after instructor approval.

### CoursePublishedEvent

Created after course publication.

### EnrollmentCreatedEvent

Created after enrollment.

### ContentUploadedEvent

Created after lesson/content upload.

---

# 15. Observability Requirements

The platform shall provide:

1. Distributed Tracing
2. Application Metrics
3. Queue Metrics
4. Service Health Monitoring
5. AI Performance Monitoring

## Zipkin

- Tracing
- Request Flow Tracking

## Prometheus

- Metrics Collection
- Monitoring

## Grafana

- Dashboards
- Visualization
- Alerting

---

# 16. High-Level Microservices Scope

## Auth Service

Responsibilities:

- Authentication
- Authorization
- JWT
- Refresh Tokens
- MFA
- Password Management

---

## User Service

Responsibilities:

- Student Profiles
- Instructor Profiles
- Admin Profiles
- Instructor Approval
- User Preferences

---

## Course Service

Responsibilities:

- Course Management
- Lesson Management
- Content Management
- Student Enrollment
- Learning Progress Tracking
- Course Completion Tracking
- Course Analytics
- Razorpay Test Integration

---

## AI Service

Responsibilities:

- AI Tutor
- Quiz Generator
- Summarizer
- Interview Coach
- Learning Advisor
- Career Advisor
- Content Generator
- Tool Calling
- Tavily Integration
- RAG Orchestration

---

## Notification Service

Responsibilities:

- Bell Notifications
- Email 
