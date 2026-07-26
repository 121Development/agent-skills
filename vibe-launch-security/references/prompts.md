# 4 AI Security Prompts for Pre-Launch Audits

Copy these directly into Claude Code, Cursor, or any agent environment.

## Prompt 1: Baseline Security Posture

```
Review my app as a security specialist and make sure I have
strong security headers and a solid baseline security posture.
```

Time: ~2 minutes. Fixes obvious gaps. Headers alone are not enough but they are the floor.

## Prompt 2: OWASP Standards Check

```
Review my app against OWASP standards and highlight vulnerabilities.
```

Time: ~2 minutes. Catches SQL injection, XSS, and auth issues.

## Prompt 3: Data Leak Audit

```
Check my app for any credential or sensitive data leaks in
frontend or API routes.
```

Time: ~2 minutes. AI-generated code leaks data in 3 places almost every time:
- .env values ending up in frontend code
- API responses returning too much data
- Secrets showing up in logs

## Prompt 4: API Key Exposure Check

```
Ensure no API keys are exposed in frontend code or network calls.
```

Time: ~2 minutes. If your key is in the browser, assume it has already been taken.

---

## Beyond the Prompts: API Key Rules

- **Public keys** can stay in the frontend: Supabase anon keys, publishable Stripe keys, anything explicitly marked as public. These are designed to be exposed.
- **Secret keys** must stay server-side: service role keys, Stripe secret keys, OpenAI keys, anything without a "publishable" prefix. Store them in Supabase Edge Function Secrets or Vercel environment variables. Never commit them to version control. Never paste them into frontend code.
- **If exposed, regenerate immediately.** Public GitHub repos get scraped for keys within minutes. Do not wait. Do not hope nobody found it.
