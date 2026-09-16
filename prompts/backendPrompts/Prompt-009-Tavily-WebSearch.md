# Prompt-009 : Tavily Search Integration

Act as a Principal AI Architect and Spring AI Architect.

The AI Service already contains:

- Gemini Integration
- Provider Failover
- RAG
- Embeddings
- Semantic Search

We now want external web knowledge.

--------------------------------------------------
GOAL
--------------------------------------------------

Integrate Tavily Search API into AI Service.

Purpose:

Allow AI to answer:

- Technology updates
- Industry news
- Research questions
- Questions not present in LMS content

--------------------------------------------------
CONFIGURATION
--------------------------------------------------

Environment Variable:

TAVILY_API_KEY

application.yml

tavily:
  api-key: ${TAVILY_API_KEY}

Do not hardcode credentials.

--------------------------------------------------
NEW COMPONENTS
--------------------------------------------------

TavilySearchService

Responsibilities:

- Execute Tavily search
- Parse results
- Return summarized search context

HybridSearchService

Responsibilities:

- Combine LMS RAG results
- Combine Tavily results
- Build final context

--------------------------------------------------
SEARCH STRATEGY
--------------------------------------------------

Step 1

Search LMS Content.

If confidence is high:

Return LMS answer.

Step 2

If LMS content insufficient:

Query Tavily.

Step 3

Combine:

- LMS Content
- Tavily Results

Step 4

Send contextual prompt to Gemini.

--------------------------------------------------
NEW APIS
--------------------------------------------------

POST /api/ai/web-search

Request

{
  "query": "Latest Spring Boot features"
}

--------------------------------------------------

POST /api/ai/hybrid-chat

Request

{
  "userId": 1,
  "courseId": 1,
  "question": "What are the latest JWT security practices?"
}

--------------------------------------------------
RESPONSE FORMAT
--------------------------------------------------

{
  "answer": "...",

  "sourceType": "LMS | WEB | HYBRID",

  "sources": [
    {
      "title": "...",
      "url": "..."
    }
  ]
}

--------------------------------------------------
AI FEATURES TO ENHANCE
--------------------------------------------------

AI Tutor

Use:

- LMS Content
- Tavily Results

Learning Advisor

Use:

- LMS Progress
- Industry Trends

Recommendations

Use:

- User Interests
- Course Catalog
- Latest Skills from Web

Interview Assistant

Use:

- Tavily Research
- Gemini

--------------------------------------------------
VALIDATION
--------------------------------------------------

Verify:

1. LMS-only query
2. Web-only query
3. Hybrid query
4. Tavily failure handling
5. Gemini failure handling

Generate final validation report.

Do not stop for approvals.

Continue until fully implemented.
