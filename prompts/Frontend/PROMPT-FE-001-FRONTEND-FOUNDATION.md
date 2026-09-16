# PROMPT-FE-001 : LMS Frontend Foundation

Act as a Senior React Architect and Frontend Lead.

Project:
Agentic AI Learning Management System (LMS)

Backend already exists.

DO NOT generate backend code.

--------------------------------------------------
TECH STACK
--------------------------------------------------

React 19
TypeScript
Vite
Tailwind CSS
React Router
Axios
TanStack Query
React Hook Form
Zod
JWT Authentication

--------------------------------------------------
BACKEND
--------------------------------------------------

All APIs must connect through API Gateway.

Gateway:

http://localhost:8080

Auth APIs:

/api/auth/register/student
/api/auth/register/instructor
/api/auth/login
/api/auth/logout
/api/auth/refresh-token
/api/auth/forgot-password
/api/auth/reset-password

User APIs:

/api/users/profile
/api/admin/users
/api/admin/instructors
/api/admin/dashboard
/api/instructors/pending

Course APIs:

/api/courses
/api/courses/{id}
/api/courses/{courseId}/enroll
/api/users/{userId}/enrollments
/api/progress/{userId}/{courseId}

--------------------------------------------------
GOAL
--------------------------------------------------

Generate the entire frontend architecture.

Create:

1. Folder structure
2. Routing architecture
3. Authentication architecture
4. State management architecture
5. Axios configuration
6. JWT token storage strategy
7. Refresh token strategy
8. Protected routes
9. Role-based routes
10. Responsive layout architecture

--------------------------------------------------
ROLES
--------------------------------------------------

ROLE_ADMIN

ROLE_INSTRUCTOR

ROLE_STUDENT

--------------------------------------------------
PAGES
--------------------------------------------------

Authentication

- Login
- Register Student
- Register Instructor
- Forgot Password

Student

- Dashboard
- Course Catalog
- My Courses
- Course Details
- Course Progress
- Profile

Instructor

- Dashboard
- Create Course
- Manage Courses
- Students

Admin

- Dashboard
- User Management
- Instructor Approvals

AI

- AI Tutor
- Quiz Generator
- Course Summary

--------------------------------------------------
OUTPUT REQUIRED
--------------------------------------------------

Phase 1:

1. Complete project folder structure

2. Dependency list

3. Route structure

4. Context structure

5. Services structure

6. React Query setup

7. Axios interceptor setup

8. Environment configuration

9. Layout architecture

10. Navigation architecture

Generate code in implementation order.

Do not skip files.

Use enterprise-grade folder organization.
