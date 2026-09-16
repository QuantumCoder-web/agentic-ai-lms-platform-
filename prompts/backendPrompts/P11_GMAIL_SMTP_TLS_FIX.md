STRICT RUNTIME BUG FIX

DO NOT ADD FEATURES.

DO NOT MODIFY BUSINESS LOGIC.

DO NOT MODIFY RABBITMQ.

ONLY FIX EMAIL DELIVERY.

==================================================
PROVEN FACTS
==================================================

✅ Notification Service Starts

✅ RabbitMQ Connects

✅ CloudAMQP Connects

✅ Event Listener Receives Messages

✅ UserLoginEvent Consumed

❌ Email Sending Fails

==================================================
ACTUAL ERROR
==================================================

javax.net.ssl.SSLException:

Unsupported or unrecognized SSL message

smtp.gmail.com
port 587

==================================================
INVESTIGATION REQUIRED
==================================================

Inspect:

application.yml

application-dev.yml

MailConfig

JavaMailSender configuration

.env loading

run_with_env.ps1

Verify:

spring.mail.host

spring.mail.port

spring.mail.username

spring.mail.password

spring.mail.properties.*

==================================================
VALID SMTP CONFIG
==================================================

If using Gmail Port 587:

Use:

mail.smtp.auth=true

mail.smtp.starttls.enable=true

mail.smtp.starttls.required=true

mail.smtp.ssl.enable=false

Do NOT use SSL socket mode.

==================================================
ALTERNATIVE
==================================================

If using Gmail SSL:

Port = 465

mail.smtp.ssl.enable=true

mail.smtp.starttls.enable=false

==================================================
VERIFY
==================================================

After fix:

Send:

✅ Welcome Email

✅ Login Email

✅ MFA OTP Email

✅ Forgot Password Email

✅ Enrollment Email

Provide actual success logs.

==================================================
OUTPUT
==================================================

Return:

1. Root cause

2. Exact file modified

3. Exact property changed

4. Runtime proof of successful email delivery

Do not stop until emails are actually sent.
