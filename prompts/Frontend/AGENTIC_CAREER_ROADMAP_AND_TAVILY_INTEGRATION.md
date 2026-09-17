GOAL

Introduce a simple but effective Agentic AI capability that adds real value to learners.

Do NOT build a complicated multi-agent framework.

Do NOT add CrewAI, AutoGen, or unnecessary orchestration.

Implement a Career Roadmap Agent.

==================================================
CAREER ROADMAP AGENT
==================================================

Student can type:

"I want to become a Backend Engineer"

"I want to become a Full Stack Developer"

"I want to become an AI Engineer"

"I want to become a Cloud Architect"

Agent behavior:

Goal Identified
↓
Analyze Available Courses
↓
Build Learning Roadmap
↓
Present Step-by-Step Path

Example:

Goal:
Backend Engineer

Roadmap:

Step 1
Spring Boot Fundamentals

Step 2
Microservices Architecture

Step 3
API Gateway & Service Discovery

Step 4
Cloud Deployment

Step 5
System Design

Estimated Duration:
8 Weeks

==================================================
ROADMAP UI
==================================================

Display roadmap in professional card layout.

Each step should contain:

✅ Course Name

✅ Short Description

✅ Estimated Duration

✅ Difficulty

✅ CTA Button

Examples:

[Enroll Now]

[View Course]

[Buy Course]

==================================================
COURSE LINKING
==================================================

Agent recommendations must link directly to LMS courses.

Student should be able to:

Roadmap
↓
Click Course
↓
Open Course Details
↓
Enroll or Purchase

No manual searching.

==================================================
PREMIUM COURSE SUPPORT
==================================================

If a roadmap includes premium courses:

Show:

Premium Badge

Price

Buy Now

Proceed through Razorpay flow.

==================================================
ROLE SUPPORT
==================================================

Student:
Career Roadmaps

Instructor:
Suggested Teaching Roadmaps

Admin:
Learning Trend Insights

==================================================
TAVILY INTEGRATION AUDIT
==================================================

Verify actual Tavily usage.

Do NOT assume it is working.

Provide exact runtime flow:

Question
↓
AI Controller
↓
AI Service
↓
pgvector Retrieval
↓
Tavily Search
↓
Prompt Assembly
↓
Gemini
↓
Response

==================================================
TAVILY RUNTIME PROOF
==================================================

Show:

✅ Tavily API key loaded

✅ Tavily request executed

✅ Tavily response received

✅ Prompt includes web results

✅ Gemini receives web context

==================================================
HYBRID RAG
==================================================

Clarify current architecture.

Determine whether:

A.
Course Content
↓
Embeddings
↓
pgvector
↓
Response

B.
Tavily
↓
Web Search
↓
Response

C.
Hybrid
pgvector
+
Tavily
↓
Gemini

Provide actual implementation evidence.

==================================================
OPTIONAL UI IMPROVEMENT
==================================================

In AI Tutor show:

Sources

Course Sources:
- Course Name
- Lesson Name

Web Sources:
- Tavily Results

Collapsible section is sufficient.

==================================================
FINAL USER EXPERIENCE
==================================================

Student

Select Goal:
↓
AI Generates Roadmap
↓
Roadmap Courses Clickable
↓
Enroll / Buy
↓
Learn
↓
Quiz
↓
Improve Skills
↓
Complete Roadmap

Goal:

Make the AI feel like a Learning Coach and Career Guide rather than just another chatbot.
