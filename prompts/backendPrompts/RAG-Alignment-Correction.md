Architecture Alignment Correction

Do not ask architectural questions.

Proceed with the implementation based on the following decisions.

--------------------------------------------------
DECISION 1
--------------------------------------------------

Use PostgreSQL pgvector.

Create vector extension automatically.

Create startup initialization script.

Do not require manual DBA work.

Application must work from a fresh setup.

--------------------------------------------------
DECISION 2
--------------------------------------------------

Course content is the source of truth.

Instructor uploads:

- Course Details
- Lessons
- Lesson Content
- PDFs
- Notes
- Resources

AI Service must index ALL available course content.

Use Course Service through OpenFeign.

Do NOT access Course database directly.

--------------------------------------------------
DECISION 3
--------------------------------------------------

RAG IS THE PRIMARY AI ARCHITECTURE.

Current AI capabilities:

- AI Tutor
- Quiz Generator
- Summary Generator
- Learning Advisor
- Recommendations

All of them must use retrieved LMS context.

No feature should rely only on Gemini prompts.

--------------------------------------------------
DECISION 4
--------------------------------------------------

Recommendation Strategy

Recommendations should work globally.

Do NOT restrict to a single courseId.

Use:

- User profile
- Enrollments
- Learning history
- Semantic similarity

Search across all indexed course embeddings.

--------------------------------------------------
DECISION 5
--------------------------------------------------

Required RAG Flow

Instructor Uploads Content
        ↓

Course Service Stores Content
        ↓

AI Service Indexes Content
        ↓

Chunking
        ↓

Embeddings
        ↓

pgvector
        ↓

Semantic Search
        ↓

Gemini
        ↓

Grounded Answer

--------------------------------------------------
DECISION 6
--------------------------------------------------

MCP is NOT required.

Tool Framework is NOT required.

Implement standard RAG architecture.

Use:

- OpenFeign
- Gemini Embeddings
- pgvector
- Semantic Search

Only.

--------------------------------------------------
DECISION 7
--------------------------------------------------

Tavily is NOT part of this implementation.

Finish LMS-grounded RAG first.

After RAG validation is complete,
we will implement Tavily as a separate enhancement.

--------------------------------------------------
DECISION 8
--------------------------------------------------

Every RAG response must return:

- Answer
- Source Chunks
- Source Course
- Source Lesson

to demonstrate answer grounding.

--------------------------------------------------
GOAL
--------------------------------------------------

The objective is:

Instructor uploads content
        ↓
Content gets indexed
        ↓
Student asks question
        ↓
AI answers from uploaded LMS content

This is the primary success criterion.

Proceed with implementation and validation.

Do not request additional architecture decisions.
