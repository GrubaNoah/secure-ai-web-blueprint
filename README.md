# Secure-by-Default Blueprint for AI-Built Web Apps

A practical checklist + reference patterns for hardening web apps — **especially the ones AI coding tools generate.** AI gets you a working app in an afternoon, but it ships a predictable set of security gaps. This blueprint names those gaps and shows how to close them, backed by a **real production case study**.

> **Worked example:** a live wedding-RSVP site (Next.js + Supabase + Vercel) taken from *shared-password admin + a hardcoded secret* to *identity-based RBAC, MFA, row-level authorization, and an audit trail* — protecting 58 real guests' personal data throughout. See **[case-study/](case-study/)**.

---

## Why this exists

AI-generated apps tend to ship the **same** security holes over and over:
- security toggled **on but not configured** (e.g. RLS enabled with zero policies)
- **secrets in the wrong place** (hardcoded in code or a DB function)
- **shared-password** admin instead of real identity
- no **record** of who changed what

None of these stop the app from *working* — so they ship. The skill is knowing to look for them and how to fix them. That's what this is.

---

## The 9 Control Domains

A "safe AI-built website" is one that covers these. Each is a checklist item, not a vibe.

| # | Domain | Gap AI commonly leaves | The fix (principle) |
|---|--------|------------------------|---------------------|
| 1 | **Identity & access** | shared password, no MFA | real per-user auth + MFA; least privilege |
| 2 | **Data authorization** | RLS on, **no policies** | row-level rules; deny by default |
| 3 | **Secrets management** | hardcoded / client-exposed keys | server-side only; rotate; never in code |
| 4 | **Input validation & abuse** | no rate limit / bot guard | validate input; throttle; honeypot |
| 5 | **Auditability** | no record of changes | log who/what/when; append-only |
| 6 | **Supply chain** | unpinned / vulnerable deps | lockfiles; scan advisories |
| 7 | **Deploy hygiene** | secrets sprawl; no headers | env separation; security headers |
| 8 | **Verification loop** | nobody ran the scan | linters/advisors; AI-assisted review |
| 9 | **Monitoring & detection** | no eyes on events | ship logs; dashboard; alert on anomalies |

Style note: examples are concrete (**Supabase + Next.js + Vercel**) because that's the stack AI tools spit out most — but each carries a **transferable principle** so it applies anywhere.

---

## How to use it

1. Building (or AI-generated) a web app? Walk the 9 domains as a **checklist**.
2. For each, read the matching pattern + the case-study example of it applied for real.
3. Run your platform's **security advisor / linter** (domain 8) — fix what it flags.

---

## Repository layout

```
secure-ai-web-blueprint/
├── README.md            ← you are here (the blueprint + checklist)
├── CONTEXT.md           ← glossary of terms used
└── case-study/          ← the wedding-site hardening, before → after
    ├── README.md        ← the full write-up (mapped to domains + NIST)
    └── screenshots/     ← evidence
```

---

## Maps to recognized frameworks
- **NIST CSF 2.0** — PR.AA (Identity, Authentication, Access Control), DE (Detect)
- **NIST 800-53** — AC (access control), IA (identification & authentication), AU (audit), IA-5 (secrets)

---

## About
Built by **Noah Gruba** — cybersecurity (IAM / GRC focus). This blueprint is the generalized, sanitized version of security work performed on a real production application; it contains **no secrets and no personal data**.
