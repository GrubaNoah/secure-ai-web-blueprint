# Context Glossary — Secure AI-Built Web Blueprint

A shared glossary for this project. Definitions only — no implementation details.
Updated as terms are resolved during design.

---

## Blueprint
The single public GitHub deliverable. A reusable guide + reference patterns for
building secure web apps (especially AI-generated ones), **plus** a worked
case-study showing the patterns applied for real. One pinned repo. (Decision: option C.)

## Case-study
The real-world proof inside the Blueprint: the before/after security hardening of
the wedding website (Supabase + Next.js + Vercel). Sanitized — contains no secrets
and no guest PII. Screenshots illustrate it.

## Wedding site
The live production app being hardened (a private wedding RSVP site). Source of the
case-study. Never made public itself (holds guest PII + secret history).

## Safe AI-built website
A web app that closes the **specific security gaps AI code generators routinely
ship**, verified against a checklist — not merely "an app that runs." Defined by
coverage of the Control Domains below.

## Control Domains
The checklist areas the Blueprint covers. (Decision: full set adopted.)
1. **Identity & access** — auth, MFA, RBAC, least privilege
2. **Data authorization** — row-level rules (RLS), per-row ownership
3. **Secrets management** — server-side only, no hardcoding, rotation
4. **Input validation & abuse control** — validation, rate limiting, bot guard
5. **Auditability** — record of who did what, when
6. **Supply chain** — pinned deps, advisory scanning
7. **Deploy hygiene** — preview vs prod separation, security headers
8. **Verification loop** — security advisors/linters, AI-assisted review
9. **Monitoring & Detection (SIEM)** — ship logs, dashboard, alert on suspicious events

## Monitoring & Detection (SIEM)
Collecting events from the app, auth provider, and host into one place, watching
them on a dashboard, and alerting on suspicious patterns (e.g. failed admin
logins). Distinct from Auditability: audit = write it down; monitoring = watch it.

## Axiom
The cloud log platform used in the case-study (free tier). Ingests Vercel request
logs + Supabase auth/Postgres logs + the app audit log -> dashboard + alerts.
Blueprint also points to Wazuh as the self-hosted alternative.

## Principle callout
A short note attached to each concrete (Supabase/Next/Vercel) pattern stating the
transferable security principle behind it, so the Blueprint teaches the concept,
not just the copy-paste. (Decision: Blueprint style = Hybrid.)

## Guest PII
The crown-jewel asset: guest names, emails, home addresses, dietary/health notes.
Protecting its **confidentiality** is the #1 goal (integrity #2, availability #3).

## Opportunistic remote attacker
The primary adversary for this design: probes public endpoints, reads the client
bundle, tries weak/default admin auth, brute-forces. (Out of scope *for this
design only*: nation-state, physical, large DDoS, cloud-provider insider.)

## Site gate (vs Admin access) — two distinct layers
- **Site gate**: an optional shared `SITE_PASSWORD` cookie that hides the *whole
  public site* from non-guests. Built but inactive. Guest-facing. Weak by design
  (plaintext-password cookie). NOT the focus of the security migration.
- **Admin access**: the privileged path to read/edit/delete RSVPs (currently
  `ADMIN_PASSWORD` + RPC secrets). THIS is what the RBAC migration replaces with
  real auth + roles. The crown-jewel control.

Keeping these separate prevents "the password" ambiguity.

## Wedding repo visibility
The wedding-site repo is **private**. Lowers exposure risk, but the Blueprint repo
is **public**, so PII/secret sanitization is still mandatory for anything copied over.

<!-- terms below resolved as the grill continues -->

