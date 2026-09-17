FINAL PHASE

NO NEW FEATURES.

NO NEW SERVICES.

NO NEW ARCHITECTURE.

NO REFACTORING.

NO ASSUMPTIONS.

This is a runtime verification and bug sweep phase.

The system should now be functionally complete.

Your task is to identify hidden bugs, broken flows, runtime issues, authorization issues, API issues, database issues, and UX dead ends.

==================================================
RULES
==================================================

Do NOT report compilation success.

Do NOT report type-check success.

Do NOT report code review findings.

Report only:

✅ Runtime verified

🟡 Partial

❌ Broken

==================================================
PHASE 1
AUTHENTICATION
==================================================

Verify:

✅ Student Registration

✅ Student Login

✅ Instructor Registration

✅ Admin Login

✅ Forgot Password

✅ Password Reset

✅ MFA Enable

✅ MFA Verify

✅ Logout

Verify redirect flows.

Verify token refresh.

Verify unauthorized access handling.

==================================================
PHASE 2
INSTRUCTOR APPROVAL
==================================================

Verify:

Instructor Registers
↓
Pending
↓
Admin Sees Request
↓
Approve
↓
Email Sent
↓
Account Activated
↓
Instructor Login Works

Verify rejection path.

Verify notifications.

Verify dashboard refresh.

==================================================
PHASE 3
DASHBOARDS
==================================================

Student Dashboard

✅ Loads

✅ Real data only

✅ Progress shown

✅ Continue Learning

✅ Recommendations

Instructor Dashboard

✅ Loads

✅ Course metrics

✅ Student counts

✅ Analytics

Admin Dashboard

✅ Loads

✅ Real analytics

✅ No fake users

✅ No placeholder statistics

==================================================
PHASE 4
PROFILES
==================================================

Student Profile

Instructor Profile

Admin Profile

Verify:

✅ No UUID shown

✅ No ROLE_* shown

✅ Full Name

✅ Email

✅ Phone

✅ MFA Status

✅ Edit Profile

✅ Save Profile

==================================================
PHASE 5
COURSES
==================================================

Verify Instructor can:

✅ Create Course

✅ Upload Image

✅ Add Module

✅ Add Lesson

✅ Add YouTube Link

✅ Add Resources

✅ Publish Course

✅ Edit Course

✅ Delete Course

Verify Student can:

✅ View Course

✅ Enroll

✅ Continue Learning

==================================================
PHASE 6
PREMIUM COURSE / RAZORPAY
==================================================

Verify:

✅ Premium Course Visible

✅ Buy Now Visible

✅ Razorpay Test Mode Opens

✅ Payment Success

✅ Enrollment Created

✅ Purchase History Created

✅ Instructor Revenue Updated

✅ Admin Visibility

==================================================
PHASE 7
PROGRESS TRACKING
==================================================

Verify:

✅ Lesson Complete

✅ Module Progress

✅ Course Progress %

✅ Continue Learning

✅ Resume Learning

✅ Completion Status

==================================================
PHASE 8
CERTIFICATES
==================================================

Verify:

✅ Course Completed

✅ Certificate Generated

✅ Certificate Download

✅ PDF Valid

✅ Certificate ID Present

==================================================
PHASE 9
AI CHATBOT
==================================================

Verify:

✅ Global Chatbot Visible

✅ Bottom Right

✅ Open

✅ Close

✅ Minimize

✅ New Chat

✅ Clear Chat

✅ Chat Persists

✅ Navigation Does Not Lose Context

==================================================
PHASE 10
VOICE MODE
==================================================

Verify:

✅ Voice Input

✅ Speech To Text

✅ Text Appears

✅ Message Sent

✅ Response Generated

==================================================
PHASE 11
RAG
==================================================

Verify runtime.

Not code.

Course
↓
Lesson
↓
Chunking
↓
Embedding
↓
pgvector
↓
Retrieval
↓
Gemini
↓
Answer

Test Questions:

"What is Eureka Service Discovery?"

"What is RAG?"

Expected:

✅ Course-specific answer

✅ Retrieved context used

✅ No generic answer

==================================================
PHASE 12
QUIZ
==================================================

Verify:

✅ Generate Quiz

✅ Questions from Course

✅ Submit Quiz

✅ Save Results

✅ View Results

==================================================
PHASE 13
SUMMARY
==================================================

Verify:

✅ Lesson Summary

✅ Module Summary

✅ Course Summary

✅ Uses course content

==================================================
PHASE 14
NOTIFICATIONS
==================================================

Admin

✅ New Instructor Request

✅ Approval Events

Instructor

✅ Approval

✅ Enrollment

✅ Course Events

Student

✅ Enrollment

✅ Completion

✅ Quiz Results

Bell must:

✅ Open

✅ Show Count

✅ Mark Read

✅ Mark All Read

✅ Persist

==================================================
PHASE 15
AUDIT LOGS
==================================================

Verify:

✅ Login Audit

✅ Registration Audit

✅ Approval Audit

✅ Payment Audit

✅ Course Creation Audit

✅ Admin Action Audit

==================================================
PHASE 16
ERROR SWEEP
==================================================

Search entire application for:

❌ Console Errors

❌ React Errors

❌ 401 Errors

❌ 403 Errors

❌ 404 Errors

❌ 500 Errors

❌ Failed API Calls

❌ Broken Navigation

❌ Dead Buttons

❌ Loading Loops

❌ Unauthorized Pages

❌ Empty States Without Message

==================================================
FINAL OUTPUT
==================================================

Return a report.

Section 1:
✅ Fully Working

Section 2:
🟡 Partial

Section 3:
❌ Broken

For every broken item provide:

1. Root Cause

2. File Responsible

3. API Responsible

4. Fix Required

5. Impact Level

Tag:

P0 = Demo blocker

P1 = Significant issue

P2 = Minor issue

Goal:

Identify every remaining bug and demo blocker before final demo preparation.
