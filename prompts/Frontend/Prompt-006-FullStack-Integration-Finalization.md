# Prompt-010 : Full Stack Integration Finalization

Act as a Principal Software Architect, Principal Frontend Architect, Principal Spring Boot Architect, and Principal QA Engineer.

You have full access to both:

- frontend/
- backend/

Do NOT generate reports.

Do NOT generate architecture reviews.

Do NOT generate documentation.

Directly inspect the code and implement missing integrations.

==================================================
OBJECTIVE
==================================================

The backend architecture is considered complete.

Current backend includes:

✅ Authentication
✅ User Management
✅ Course Management
✅ Notification Service
✅ Gemini Integration
✅ Gemini Failover Chain
✅ Company LLM Fallback
✅ Embeddings
✅ pgvector
✅ RAG
✅ Semantic Search
✅ Tavily Search
✅ Hybrid Search
✅ Quiz Generation
✅ Summary Generation
✅ Recommendations

The remaining work is frontend integration and end-to-end LMS workflow completion.

==================================================
IMPLEMENTATION MODE
==================================================

Stop proposing.

Stop redesigning.

Stop generating reports.

Directly implement missing integrations.

==================================================
PHASE 1
FRONTEND API LAYER
==================================================

Create:

frontend/src/services/aiService.ts

Implement:

1. askHybridQuestion()

POST /api/ai/hybrid-chat

2. generateSummary()

POST /api/ai/summary

3. generateQuiz()

POST /api/ai/quiz

4. getRecommendations()

GET /api/ai/recommendations/{userId}

5. indexCourse()

POST /api/ai/rag/index/course/{courseId}

6. semanticSearch()

POST /api/ai/rag/search

7. webSearch()

POST /api/ai/web-search

Implement full typing.

Create request DTOs.

Create response DTOs.

Use existing API patterns.

==================================================
PHASE 2
FIX ALL API MISMATCHES
==================================================

Inspect frontend and backend contracts.

Fix:

✅ Route mismatches

✅ DTO mismatches

✅ Request body mismatches

✅ Response mapping mismatches

✅ Progress APIs

✅ Instructor Approval APIs

Do not leave known mismatches unresolved.

==================================================
PHASE 3
INSTRUCTOR WORKFLOW
==================================================

Implement end-to-end instructor flow:

Instructor Login
        ↓
Create Course
        ↓
Add Lesson
        ↓
Manage Lessons
        ↓
Index Course
        ↓
Success Status

Required Pages:

CreateCoursePage

ManageCoursesPage

LessonManagementPage

CourseIndexPage

All pages must use real backend APIs.

No mocked data.

No placeholders.

==================================================
PHASE 4
STUDENT WORKFLOW
==================================================

Implement:

Student Dashboard

My Courses

Course Details

Lesson View

Course Progress

Enrollments

Use real backend APIs.

Remove placeholders.

==================================================
PHASE 5
AI TUTOR
==================================================

Implement AiTutorPage.

Connect:

POST /api/ai/hybrid-chat

Features:

✅ Chat History

✅ Markdown Rendering

✅ Loading State

✅ Error State

✅ Source Citations

✅ LMS / WEB / HYBRID Badge

Response Sources Section

Example:

Sources:
- Course 1 Lesson 3
- Tavily Source

==================================================
PHASE 6
SUMMARY GENERATOR
==================================================

Implement:

CourseSummaryPage

Connect:

POST /api/ai/summary

Features:

✅ Markdown Summary

✅ Loading State

✅ Copy Button

✅ Regenerate Button

==================================================
PHASE 7
QUIZ GENERATOR
==================================================

Implement:

QuizGeneratorPage

Connect:

POST /api/ai/quiz

Features:

✅ Question Cards

✅ Option Selection

✅ Submit

✅ Score Calculation

✅ Correct Answer Display

==================================================
PHASE 8
RECOMMENDATIONS
==================================================

Create:

RecommendationPage

Connect:

GET /api/ai/recommendations/{userId}

Features:

✅ Recommended Courses

✅ Reason Display

✅ Course Cards

✅ Navigation

==================================================
PHASE 9
COURSE INDEXING UX
==================================================

When Instructor clicks:

Index Course

Call:

POST /api/ai/rag/index/course/{courseId}

Show:

✅ Progress Spinner

✅ Success Toast

✅ Failure Toast

✅ Indexed Status Badge

==================================================
PHASE 10
END-TO-END VALIDATION
==================================================

Validate complete workflow:

Register
↓
Login
↓
Create Course
↓
Add Lesson
↓
Index Course
↓
Create Embeddings
↓
Student Enrolls
↓
Student Opens Course
↓
Student Uses AI Tutor
↓
Summary Generated
↓
Quiz Generated
↓
Recommendations Loaded

==================================================
RESTRICTIONS
==================================================

Do NOT:

- Create new AI features
- Add MCP
- Add Agent Frameworks
- Add new Architectures
- Create extra reports

Focus only on:

- Missing integrations
- Missing pages
- API wiring
- End-to-end functionality

==================================================
SUCCESS CRITERIA
==================================================

A user can:

1. Register

2. Login

3. Create Course

4. Add Lesson

5. Index Course

6. Ask AI Questions

7. Receive LMS-grounded RAG answers

8. Generate Summaries

9. Generate Quizzes

10. View Recommendations

without any mocked data.

Proceed immediately.
