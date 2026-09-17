AI Chat UX Improvements

1. Keep role-based suggestion chips.

2. When a user clicks a chip:
✅ Automatically send the prompt
✅ Do not require clicking Send again

3. Improve Voice Mode.

Current:
Mic → Speak → Text appears → User clicks Send

Required:
Mic → Speak → Stop speaking → 1 second silence → Auto-send message

4. Show status indicators:

🎤 Listening...
⏳ Processing...
✅ Response received

5. Keep implementation lightweight.

Do not change AI architecture.
Do not add new services.
Do not introduce breaking changes.

Goal:
Make chatbot feel smooth and modern with one-click prompts and voice auto-send behavior.
