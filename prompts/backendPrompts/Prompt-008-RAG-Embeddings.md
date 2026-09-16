# Prompt-008 : RAG + Embeddings + Semantic Search

Act as a Principal Generative AI Architect, RAG Architect, and Spring AI Architect.

The current AI Service already supports:

- AI Chat
- Quiz Generation
- Summary Generation
- Learning Advisor
- Course Recommendations

However, the platform currently lacks:

- RAG
- Embeddings
- Vector Search
- Semantic Retrieval

These are mandatory features for the Agentic AI LMS.

Goal:

Transform the AI Service from a generic LLM wrapper into a Retrieval-Augmented Generation (RAG) platform.

-------------------------------------------------------
CURRENT STACK
-------------------------------------------------------

Backend:

- Java 25
- Spring Boot 3.x
- PostgreSQL
- OpenFeign
- Eureka
- API Gateway
- Gemini API
- Notification Service
- AI Service

-------------------------------------------------------
RAG REQUIREMENTS
-------------------------------------------------------

Implement:

1. Document Ingestion

2. Text Chunking

3. Embedding Generation

4. Vector Storage

5. Similarity Search

6. RAG Chat

-------------------------------------------------------
VECTOR DATABASE
-------------------------------------------------------

Use PostgreSQL pgvector.

Do NOT introduce:

- Pinecone
- Weaviate
- Chroma
- Milvus

Use PostgreSQL only.

Add migration scripts.

-------------------------------------------------------
NEW TABLES
-------------------------------------------------------

course_embeddings

- id
- course_id
- lesson_id
- chunk_text
- embedding_vector
- created_at

ai_context_history

- id
- user_id
- course_id
- retrieved_chunks
- prompt
- response
- created_at

-------------------------------------------------------
EMBEDDING MODEL
-------------------------------------------------------

Use Gemini Embedding API.

Configuration:

gemini:
  embedding-model: text-embedding-004

Use API Key authentication.

Do NOT use:

- Vertex AI
- Service Accounts
- GCP Credentials

-------------------------------------------------------
DOCUMENT CHUNKING
-------------------------------------------------------

Implement chunking service.

Chunk Size:

1000 characters

Chunk Overlap:

200 characters

Components:

TextChunkingService

Features:

- lesson content chunking
- course content chunking
- PDF extracted text chunking

-------------------------------------------------------
NEW SERVICES
-------------------------------------------------------

EmbeddingService

Responsibilities:

- generate embeddings
- store vectors

SimilaritySearchService

Responsibilities:

- semantic search
- nearest neighbor retrieval

RagChatService

Responsibilities:

- retrieve context
- augment prompt
- send to Gemini

-------------------------------------------------------
RAG PIPELINE
-------------------------------------------------------

User Question

↓

Generate Question Embedding

↓

Vector Search

↓

Top 5 Relevant Chunks

↓

Build Context

↓

Gemini

↓

Answer grounded in LMS content

-------------------------------------------------------
NEW APIs
-------------------------------------------------------

1. Index Course

POST /api/ai/rag/index/course/{courseId}

Purpose:

Generate embeddings for entire course.

-------------------------------------------------------

2. Semantic Search

POST /api/ai/rag/search

Request:

{
  "courseId": 1,
  "query": "Explain Spring Security JWT"
}

Response:

{
  "results": [...]
}

-------------------------------------------------------

3. RAG Chat

POST /api/ai/rag/chat

Request:

{
  "userId": 1,
  "courseId": 1,
  "question": "What is JWT Authentication?"
}

Response:

{
  "answer": "...",
  "sources": [...]
}

-------------------------------------------------------

4. Reindex Course

POST /api/ai/rag/reindex/{courseId}

-------------------------------------------------------
PROMPT SAFETY
-------------------------------------------------------

System Prompt:

Answer ONLY using retrieved LMS context.

If answer is unavailable in the retrieved content:

Respond:

"The requested information was not found in the indexed LMS materials."

Prevent hallucinations.

-------------------------------------------------------
AI FEATURES TO UPGRADE
-------------------------------------------------------

Quiz Generator

Use retrieved course chunks.

Summary Generator

Use retrieved course content.

Learning Advisor

Use enrolled course history.

Recommendations

Use semantic similarity and user profile.

-------------------------------------------------------
OPENFEIGN INTEGRATION
-------------------------------------------------------

AI Service must retrieve:

- Courses
- Lessons
- Content
- Metadata

from Course Service.

Do not access Course DB directly.

-------------------------------------------------------
TESTING
-------------------------------------------------------

Generate:

EmbeddingServiceTest

SimilaritySearchServiceTest

RagChatServiceTest

RagControllerTest

-------------------------------------------------------
VALIDATION
-------------------------------------------------------

After implementation:

1. Generate embeddings.
2. Index course content.
3. Execute semantic search.
4. Execute RAG chat.
5. Verify retrieved chunks are used.
6. Verify source citations returned.
7. Generate RAG validation report.
8. Generate Architecture Review.

Do not stop for approvals.

Continue until RAG implementation is completed and validated.
