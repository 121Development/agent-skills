---
name: vibe-launch-security
version: 1.0.0
description: |
  Run a 30-minute pre-launch security checklist for vibe-coded apps. Covers legal protection, database lockdown, auth failure testing, AI security prompts, and infrastructure hardening. Use when the user says they are about to launch, shipping soon, or wants a security checklist for an AI-built MVP.
triggers:
  - "about to launch"
  - "pre-launch security"
  - "vibe coder security"
  - "launch checklist"
  - "security checklist"
  - "shipping tomorrow"
  - "going live"
tools:
  - web_search
mutating: false
---

# Vibe Launch Security

## Contract
- Delivers a complete 5-category pre-launch security checklist tailored to the user's stack
- Surfaces the 4 AI prompts that audit security posture, OWASP compliance, data leaks, and API key exposure
- Flags the failure-case auth tests that catch 80% of live vulnerabilities
- Never lets the user skip a category with "I will fix it later"

## Phases

1. **Confirm the stack.** Ask what they are using: Supabase, Firebase, Vercel, Bolt, Lovable, custom backend, etc. The checklist adapts but the categories do not bend.

2. **Run the 5-category checklist.** Walk through each category in order. Do not let the user jump ahead until the current category is signed off.

   - **Category 1: Protect yourself legally.**
     - Privacy policy generated and linked (Termly or PrivacyPolicies.com)
     - User data locations documented: database region, third-party services touching data
     - No plain-text passwords, no selling data, no exporting to personal email
     - *2026 update:* remind them AI-only code cannot be copyrighted in the US; GPL contamination risk exists; the $1.5B AI copyright settlement is now final

   - **Category 2: Lock down the database.**
     - Row Level Security enabled with policies on every table (Supabase: Auth → Policies must not be empty)
     - Server-side validation on every form (Zod on the client is UX, not security)
     - Error messages are generic to users, detailed only in server-side logs (no stack traces, no table names, no column names)

   - **Category 3: Test auth failure cases.**
     - Wrong password 5 times: does it lock or throttle? Does it confirm the email exists?
     - Password reset for non-existent email: does it reveal whether the email is registered?
     - Click email verification link twice: does it break or handle gracefully?
     - Sign up with already-registered email: does it leak that the user exists?

   - **Category 4: Run the 4 AI prompts.**
     - Load the exact prompts from `references/prompts.md` and feed them into the user's agent (Claude Code, Cursor, etc.)
     - After prompt results, verify: public keys only in frontend, secret keys only in server-side env vars or edge function secrets, nothing committed to version control

   - **Category 5: Protect infrastructure.**
     - Rate limits on every endpoint (Upstash for Supabase Edge Functions: 100 req/min per IP public, 1,000 req/min authenticated)
     - Hard daily caps on paid APIs (OpenAI, Anthropic, Stripe) with alerts at 50%
     - CAPTCHA on every public form (Cloudflare Turnstile is free, 10-minute integration)
     - CORS restrictions on the API: allow-list exact origins, strip credentials from wildcard responses

3. **Produce the go/no-go summary.** List every category as PASS or BLOCK. A single BLOCK means do not launch. Include the exact next action for each BLOCK.

## Output Format
A structured checklist with 5 categories, each containing:
- The specific checks to perform
- The tool or location where to verify (e.g., Supabase Auth → Policies)
- PASS / BLOCK status
- The exact next action if BLOCKED

## Anti-Patterns
- Treating security as a version-2 feature. It is the floor, not a feature.
- Relying on client-side validation as security. Attackers disable JavaScript and use Postman.
- Shipping API keys to the browser. If it is in the frontend, assume it is already stolen.
- Testing only the happy path on auth. Attackers probe the failure cases first.
- Leaving rate limits off because the app is small. A single bot can turn a $20 bill into $200 overnight.

## References
- `references/prompts.md` — the 4 AI prompts to copy into Claude Code, Cursor, or any agent
