Act as a Principal Spring Boot Architect and Integration Architect.

We already have:

✅ Auth Service
✅ User Service
✅ Course Service
✅ Notification Service
✅ AI Service
✅ RAG
✅ Tavily
✅ Gemini
✅ MFA
✅ Forgot Password

We also have a working CloudAMQP (RabbitMQ) instance.

IMPORTANT:

Do NOT redesign the application.

Do NOT modify existing business logic.

Do NOT refactor existing APIs.

Do NOT change controller contracts.

Do NOT modify frontend contracts.

Do NOT remove existing synchronous behavior.

Do NOT create new architecture.

Goal:

Add RabbitMQ event publishing and consumption only.

RabbitMQ must be an enhancement, not a rewrite.

==================================================
CLOUDAMQP
==================================================

Use the existing CloudAMQP instance.

Before implementation, inspect what information is required:

- Host
- Port
- Username
- Password
- Virtual Host
- Connection URI

If additional values are needed, explicitly request them.

==================================================
USE CASES
==================================================

Publish events AFTER successful execution only.

1. User Registered

Event:

UserRegisteredEvent

2. User Logged In

Event:

UserLoginEvent

3. MFA OTP Generated

Event:

MfaOtpEvent

4. Forgot Password Requested

Event:

ForgotPasswordEvent

5. Course Enrollment Successful

Event:

CourseEnrollmentEvent

==================================================
NOTIFICATION SERVICE
==================================================

Notification Service becomes the RabbitMQ consumer.

Consumer responsibilities:

- Receive events
- Generate notification records
- Send Gmail email notifications

==================================================
EMAILS
==================================================

Support:

1. Welcome Email

2. Login Notification Email

Example:

"Your account was accessed successfully."

3. MFA OTP Email

4. Password Reset Email

5. Course Enrollment Email

==================================================
EMAIL PROVIDER
==================================================

Use Gmail SMTP.

Do not hardcode credentials.

Use environment variables.

If any values are needed, request:

MAIL_HOST
MAIL_PORT
MAIL_USERNAME
MAIL_PASSWORD

Use Gmail App Password only.

==================================================
IMPLEMENTATION RULES
==================================================

1. Existing APIs must continue working.

2. Existing tests must continue passing.

3. Existing AI functionality must remain untouched.

4. Existing RAG functionality must remain untouched.

5. Existing Tavily integration must remain untouched.

6. Existing frontend contracts must remain untouched.

7. RabbitMQ should only enhance notification delivery.

==================================================
VALIDATION
==================================================

After implementation:

Verify:

✅ Registration event published

✅ Login event published

✅ MFA event published

✅ Forgot password event published

✅ Enrollment event published

✅ Notification Service receives events

✅ Email successfully sent

✅ Existing tests pass

✅ Existing functionality unchanged

Generate validation output only.

No architecture redesign.
No unnecessary refactoring.
