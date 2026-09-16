Architecture Correction

Implement Gemini failover, NOT key rotation.

Current Providers:

1. Gemini Key 1
2. Gemini Key 2
3. Gemini Key 3
4. Gemini Key 4
5. Gemini Key 5
6. Company LLM

Requirements:

Do NOT implement round-robin rotation.

Do NOT switch keys per request.

Do NOT load balance requests.

Implement failover chain only.

Execution Flow:

Gemini Key 1
    ↓ exception/quota/rate limit

Gemini Key 2
    ↓ exception/quota/rate limit

Gemini Key 3
    ↓ exception/quota/rate limit

Gemini Key 4
    ↓ exception/quota/rate limit

Gemini Key 5
    ↓ exception/quota/rate limit

Company LLM
    ↓ exception

Return safe fallback response.

Environment Variables:

GEMINI_API_KEY_1
GEMINI_API_KEY_2
GEMINI_API_KEY_3
GEMINI_API_KEY_4
GEMINI_API_KEY_5

COMPANY_LLM_API_KEY

Configuration must not store actual keys.

Keys must come only from environment variables.

Generate logs indicating:

Active Provider
Failover Provider
Failure Reason

Goal:

Keep Gemini as the primary AI source.

Use Company LLM only as the final AI fallback before graceful degradation.
