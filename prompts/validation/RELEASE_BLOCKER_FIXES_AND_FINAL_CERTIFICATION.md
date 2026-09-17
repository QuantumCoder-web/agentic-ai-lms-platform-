RELEASE BLOCKER PHASE

STOP ALL NEW FEATURE DEVELOPMENT.

STOP UI REFINEMENTS.

STOP NEW ARCHITECTURE.

STOP NEW MICROSERVICES.

The objective is now:

Fix all P0/P1 issues identified during runtime verification and achieve release readiness.

No assumptions.

No compilation claims.

No implementation summaries.

Only runtime validation counts.

==================================================
P0 BLOCKERS
==================================================

These issues prevent production readiness.

Fix them first.

--------------------------------------------------
P0-1 MFA IS BYPASSED
--------------------------------------------------

Current:

MFA enabled users still receive JWT directly.

MFA verification is never enforced.

Root Cause:

AuthServiceImpl.login()

returns JWT before MFA validation logic executes.

Required:

User Login
↓
MFA Enabled?
↓
YES
↓
Return MFA_REQUIRED response
↓
OTP Verification
↓
JWT issued

Validate:

✅ MFA enabled account

✅ Login blocked until OTP

✅ OTP verification succeeds

✅ JWT issued only after verification

This is mandatory.

==================================================
P0-2 INSTRUCTOR APPROVAL FAILED
==================================================

Current:

Approval returns HTTP 200

But account remains disabled.

Root Cause:

user-service sends user.id

instead of authUserId

to auth-service enable endpoint.

Required:

Use:

user.getAuthUserId()

instead of

instructorProfile.getUserId()

Validate:

✅ Approve instructor

✅ Auth account enabled

✅ Instructor login works

✅ Email notification sent

✅ In-app notification generated

==================================================
P0-3 AI SERVICE STARTUP FAILURE
==================================================

Current:

Repository type mismatch.

Long vs String.

AI Service can fail to start.

Required:

Audit ALL AI repositories.

Audit:

QuizHistoryRepository

SummaryHistoryRepository

ConversationRepository

Embedding repositories

Validate:

✅ AI service starts

✅ No startup exceptions

✅ No JPA semantic errors

==================================================
P1 HIGH PRIORITY
==================================================

--------------------------------------------------
P1-1 AI ASSISTANT REDIRECT
--------------------------------------------------

Current:

Login flow loses intended destination.

Required:

Public User
↓
Click AI Assistant
↓
Redirect Login
↓
Successful Login
↓
Return To AI Assistant

Validate.

--------------------------------------------------
P1-2 PAYMENT SECURITY
--------------------------------------------------

Current:

Payment API accepts userId from request body.

This is insecure.

Required:

Extract user identity from JWT.

Never trust request body userId.

Validate:

✅ Correct user ownership

✅ No ID spoofing

✅ Enrollment tied to authenticated user

==================================================
FULL LMS VALIDATION
==================================================

After fixes:

Verify end-to-end.

==================================================
STUDENT JOURNEY
==================================================

✅ Register

✅ Login

✅ MFA

✅ Browse Courses

✅ Enroll

✅ Buy Premium Course

✅ Razorpay Test Payment

✅ Progress Tracking

✅ Mark Lesson Complete

✅ Complete Course

✅ Certificate Download

✅ Notifications

✅ AI Tutor

✅ Quiz

✅ Summary

✅ Voice Input

==================================================
INSTRUCTOR JOURNEY
==================================================

✅ Apply

✅ Pending

✅ Admin Approval

✅ Login After Approval

✅ Create Course

✅ Add Modules

✅ Add Lessons

✅ Add YouTube Links

✅ Add Resources

✅ Publish Course

✅ Index Course

✅ View Analytics

✅ View Students

==================================================
ADMIN JOURNEY
==================================================

✅ Login

✅ MFA

✅ View Users

✅ View Instructors

✅ Approve Instructor

✅ Reject Instructor

✅ Notifications

✅ Audit Logs

✅ Platform Analytics

==================================================
RAG VALIDATION
==================================================

Do NOT claim verified.

Prove verified.

Test:

Question:
"What is Eureka Service Discovery?"

Question:
"What is RAG?"

Question:
"How do embeddings work?"

Verify:

✅ Retrieval executed

✅ pgvector query executed

✅ Relevant chunks retrieved

✅ Gemini used retrieved context

✅ Response grounded in course data

==================================================
AI FEATURES
==================================================

Verify:

✅ Global Chatbot

✅ Chat History

✅ Persistent Sessions

✅ Voice Input

✅ Quiz Generation

✅ Summary Generation

✅ Recommendations

✅ Role-Aware Responses

==================================================
NOTIFICATIONS
==================================================

Verify actual events.

Student:

✅ Enrollment

✅ Completion

✅ Quiz Results

Instructor:

✅ Approval

✅ Enrollment

✅ Course Events

Admin:

✅ Instructor Requests

✅ Approvals

✅ Rejections

==================================================
AUDIT LOGS
==================================================

Verify:

✅ Login

✅ Registration

✅ Approval

✅ Payment

✅ Course Creation

✅ Completion

Stored and visible.

==================================================
ERROR SWEEP
==================================================

Search entire stack for:

✅ 401

✅ 403

✅ 404

✅ 500

✅ React Runtime Errors

✅ Failed API Calls

✅ Dead Buttons

✅ Navigation Loops

✅ Broken Redirects

✅ Empty States

==================================================
FINAL OUTPUT
==================================================

Section A

✅ RELEASE READY

Section B

🟡 NEEDS ATTENTION

Section C

❌ RELEASE BLOCKERS

For every blocker provide:

1. Root Cause

2. File

3. Endpoint

4. Fix

5. Validation Evidence

6. Severity

Use:

P0 = Demo Blocker

P1 = High

P2 = Medium

Goal:

Reach a state where a complete Student → Instructor → Admin → AI → Payment → Certificate → Notification workflow can be demonstrated without runtime failures.
