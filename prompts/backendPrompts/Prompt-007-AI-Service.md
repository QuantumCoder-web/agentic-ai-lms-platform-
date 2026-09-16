# Prompt-007 : AI Service

## Prompt

```text
Act as a Principal AI Architect, Spring AI Architect, and Microservices Architect.

Generate a production-ready AI Service for the Agentic AI LMS Platform.

Project Name:

Agentic AI LMS Platform

Generate project inside:

backend/ai-service

Technology Stack:

- Java 25
- Spring Boot 3.x
- Maven
- Spring AI
- Ollama
- OpenFeign
- PostgreSQL
- Eureka Client
- Spring Boot Actuator
- Validation
- OpenAPI / Swagger

Important MVP Rules

1. Do NOT use RabbitMQ.
2. Do NOT use AMQP.
3. Do NOT use MCP.
4. Do NOT build autonomous agents.
5. Use OpenFeign for inter-service communication.
6. Use Java Records for DTOs.
7. Do NOT use Lombok.
8. Java 25 compatible.
9. Swagger enabled.
10. Eureka enabled.

Current Platform Services

- Eureka Server
- API Gateway
- Auth Service
- User Service
- Course Service
- Notification Service
- AI Service (Current)

Service Name

AI-SERVICE

Port

8085

Database

AI_DB

Package

com.agenticailms.ai

Mission

Provide AI capabilities for LMS users.

MVP Features

1. AI Tutor

Answer learner questions.

2. Quiz Generator

Generate quizzes from course content.

3. Course Summary Generator

Generate summaries from lessons and course content.

4. Learning Advisor

Provide recommendations and learning guidance.

5. Course Recommendation Engine

Recommend courses based on user interests and enrollments.

LLM Provider

Ollama

Embedding Model

nomic-embed-text

Chat Model

gemma3:4b

Make model configurable through application.yml.

Example:

ai:
  chat-model: gemma3:4b
  embedding-model: nomic-embed-text

Inter-Service Communication

Create OpenFeign clients for:

User Service

Course Service

Notification Service

Requirements

AI Service must be able to:

- Retrieve user profile
- Retrieve enrolled courses
- Retrieve course details
- Retrieve lessons
- Send notification

through OpenFeign.

Do not use direct database access to other services.

Layered Architecture

Generate:

- controller
- service
- repository
- entity
- dto
- config
- client
- exception
- mapper

Database Tables

ai_conversations

- id
- user_id
- prompt
- response
- created_at

quiz_history

- id
- user_id
- course_id
- generated_quiz
- created_at

summary_history

- id
- user_id
- course_id
- generated_summary
- created_at

APIs

AI Chat

POST /api/ai/chat

Request

{
  "userId": 1,
  "prompt": "Explain Spring Security JWT Authentication"
}

Response

{
  "response": "..."
}

Quiz Generator

POST /api/ai/quiz

Request

{
  "userId": 1,
  "courseId": 101
}

Response

{
  "quiz": "..."
}

Summary Generator

POST /api/ai/summary

Request

{
  "userId": 1,
  "courseId": 101
}

Response

{
  "summary": "..."
}

Learning Advisor

POST /api/ai/advisor

Request

{
  "userId": 1,
  "question": "What should I learn next?"
}

Response

{
  "advice": "..."
}

Course Recommendations

GET /api/ai/recommendations/{userId}

Response

{
  "recommendations": []
}

Prompt Engineering

Create dedicated prompt templates.

Examples:

TutorPromptTemplate

QuizPromptTemplate

SummaryPromptTemplate

AdvisorPromptTemplate

RecommendationPromptTemplate

Store templates in separate classes.

Security

Use same JWT strategy as:

- Auth Service
- User Service
- Course Service
- Notification Service

Implement:

- JwtTokenProvider
- JwtAuthenticationFilter
- SecurityConfig

Roles

ADMIN
INSTRUCTOR
STUDENT

Swagger

URLs

http://localhost:8085/swagger-ui/index.html

http://localhost:8085/v3/api-docs

Actuator

Expose:

- health
- info
- metrics

Testing

Generate:

- AiChatServiceTest
- QuizGeneratorServiceTest
- SummaryServiceTest
- RecommendationServiceTest
- AiControllerTest

Use:

- JUnit 5
- Mockito
- Spring Boot Test

Coverage Goal

80%+

Quality Rules

- SOLID Principles
- Clean Architecture
- SonarQube Ready
- JaCoCo Ready
- Environment-Based Configuration

Validation Phase

After generation:

1. Run mvn clean test.
2. Fix all compilation errors.
3. Start application.
4. Verify Eureka registration.
5. Verify Swagger.
6. Verify OpenAPI.
7. Verify Actuator.
8. Verify Feign clients.
9. Generate final validation report.
10. Generate architecture review.

Do not stop for approval requests.

Continue until AI Service is fully generated and validated.
```
