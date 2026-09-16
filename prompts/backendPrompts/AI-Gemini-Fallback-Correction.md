Architecture Correction

The previous implementation misunderstood the requirement.

Do NOT implement automatic Gemini API key rotation.

Do NOT implement round-robin load balancing.

Do NOT store actual API keys in application.yml.

Requirements:

1. Use a single active Gemini API key through environment variables:

GEMINI_API_KEY

2. Configuration:

gemini:
  api-key: ${GEMINI_API_KEY}
  model: ${GEMINI_MODEL:gemini-2.5-flash}

3. Keep CompanyLlmProvider as a secondary provider.

4. Fallback strategy:

Primary:
GeminiProvider

If Gemini fails:
CompanyLlmProvider

If CompanyLlmProvider fails:
Return a graceful fallback AI message.

5. No automatic key rotation.

6. No multiple-key manager.

7. No load balancing.

8. No API keys hardcoded in source code.

9. No API keys stored in Git.

10. Environment variables only.

Example flow:

AI Request
   ↓
Gemini Provider

If exception:
   ↓
Company LLM Provider

If exception:
   ↓
Fallback response

Example fallback:

"AI service is temporarily unavailable. Please try again in a few moments."

11. Generate a verification report showing:

- Active provider
- Fallback provider
- Configuration locations
- Security review

Goal:

Keep the MVP simple and secure.

Do not add any additional provider complexity unless explicitly requested.
