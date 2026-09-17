CRITICAL

Do NOT assume features exist.

Do NOT assume features are missing.

VERIFY FIRST.

Only implement functionality that is genuinely missing.

Avoid cascading changes.

Avoid large refactors.

Avoid breaking authentication, approvals, notifications, AI services, RAG, RabbitMQ, existing APIs, or seeded courses.

==================================================
PHASE 1 - FEATURE AUDIT
==================================================

Perform a complete audit.

For every feature below report:

✅ Fully Working

🟡 Partially Working

❌ Missing

Do NOT implement before verification.

==================================================
COURSE CREATION FLOW
==================================================

Verify Instructor functionality.

Can Instructor:

✅ Create Course

✅ Add Thumbnail

✅ Add Description

✅ Add Modules

✅ Add Lessons

✅ Add Resource Links

✅ Add GitHub Links

✅ Add YouTube Links

✅ Publish Course

✅ Edit Course

✅ Delete Course

✅ Index Course for AI

Report exactly what works and what does not.

==================================================
COURSE DISCOVERY
==================================================

Verify Student experience.

Can Student:

✅ View Courses

✅ Search Courses

✅ Filter Courses

✅ Open Course Details

✅ View Modules

✅ View Lessons

✅ Access Free Course

==================================================
ENROLLMENT / PURCHASE FLOW
==================================================

Verify current implementation.

Can Student:

✅ Enroll in Course

✅ Purchase Premium Course

✅ Access Purchased Content

✅ View My Courses

If purchase system does not exist:

Report as missing.

Do not fabricate.

==================================================
INSTRUCTOR ANALYTICS
==================================================

Verify:

Can Instructor see:

✅ Total Students

✅ Course Enrollments

✅ Students Per Course

✅ Learning Progress

✅ Active Learners

Only use real database data.

No mock analytics.

==================================================
QUIZ SYSTEM
==================================================

Verify first.

Can Student:

✅ Generate Quiz

✅ Take Quiz

✅ Submit Quiz

✅ See Results

✅ Store Results

Can AI generate quiz from course content?

Verify using actual runtime flow.

==================================================
SUMMARY SYSTEM
==================================================

Verify:

✅ AI Summary Generation

✅ Lesson Summary

✅ Module Summary

✅ Course Summary

Verify these use actual lesson content.

==================================================
RAG SYSTEM
==================================================

Verify actual implementation.

Flow:

Course
↓
Lesson
↓
Chunking
↓
Embeddings
↓
pgvector
↓
Retrieval
↓
Gemini
↓
Answer

Validate:

✅ Embeddings generated

✅ Stored in vector database

✅ Retrieval works

✅ AI uses retrieved content

✅ Citations included

Provide evidence.

==================================================
AI TUTOR
==================================================

Verify whether AI Tutor exists.

Requirements:

✅ Course-aware answers

✅ Uses RAG

✅ Context retained during session

✅ Chat history maintained

✅ Session persistence

✅ Source citations

==================================================
CHATBOT EXPERIENCE
==================================================

Current requirement:

Do not lock AI to a page.

Implement only if missing.

Desired UX:

Floating chatbot

Bottom-right corner

Available across:

✅ Student

✅ Instructor

✅ Admin

Features:

✅ Minimize

✅ Expand

✅ Persistent Conversation

✅ Session Memory

✅ Clear Chat

✅ New Chat

✅ Context Awareness

Do not make it a decorative widget.

==================================================
VOICE MODE
==================================================

Verify first.

If missing:

Implement lightweight Voice Mode.

Requirements:

✅ Voice Input

✅ Speech-to-Text

✅ Sends transcription to chatbot

✅ Works for Student

✅ Works for Instructor

✅ Works for Admin

Voice output is optional.

Voice input is the priority.

==================================================
ROLE-AWARE AI
==================================================

AI should behave differently.

Student:

✅ Learning help

✅ Course questions

✅ Quiz help

✅ Summaries

Instructor:

✅ Course creation help

✅ Module suggestions

✅ Lesson improvement

✅ Quiz creation

✅ Analytics insights

Admin:

✅ Platform metrics

✅ Instructor approvals

✅ User statistics

✅ Operational insights

Example:

Admin asks:
"How many instructors are pending approval?"

AI should answer using platform data.

==================================================
STRICT VALIDATION
==================================================

Before claiming completion:

Verify:

✅ API Exists

✅ Backend Works

✅ Database Stores Data

✅ Frontend Displays Data

✅ Security Enforced

✅ Runtime Tested

No assumptions.

No fake completions.

==================================================
DO NOT BREAK
==================================================

Do not break:

✅ Authentication

✅ Instructor Approval

✅ Notifications

✅ Existing AI

✅ Existing Courses

✅ Seeded Courses

✅ RAG Architecture

✅ RabbitMQ

✅ Email System

==================================================
OUTPUT
==================================================

Return:

1. Fully Working Features

2. Partially Working Features

3. Missing Features

4. Files Modified

5. APIs Added

6. Database Changes

7. Runtime Validation Evidence

8. Remaining Blockers

IMPORTANT:

Verification takes priority over implementation.

Never build what already exists.

Never remove working functionality.

Goal:

Deliver a production-ready AI LMS with verified instructor workflows, course creation, enrollment, quizzes, summaries, RAG, chatbot, and voice capabilities without introducing cascading failures.
