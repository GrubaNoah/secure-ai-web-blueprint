# Case-Study Screenshots — capture list

Drop screenshots here as you do each phase. Name them exactly as listed so the
case-study write-up can embed them.

> **Sanitization rule (public repo):** blur or redact anything sensitive before a
> shot goes in the *public* blueprint — real emails, secrets/keys, tokens, full
> guest PII. For the admin/data views, prefer seeded **fake** data or blur.

| Phase | Filename | What to capture |
|---|---|---|
| 2 — Auth | `02-auth-providers.png` | Supabase → Authentication → Providers (Email enabled) |
| 2 — Auth | `02-signups-disabled.png` | the "allow new sign-ups" setting turned OFF |
| 2 — Auth | `02-users-created.png` | Authentication → Users list (your 2 accounts — blur emails for public) |
| 2 — Auth | `02-mfa-enabled.png` | MFA / TOTP enabled in auth settings |
| 3 — Roles | `03-user-roles-sql.png` | SQL editor: `user_roles` table + `is_admin()` created |
| 4 — RLS | `04-rls-policies.png` | the new RLS policies on `rsvps` |
| 5 — Audit | `05-audit-log.png` | `rsvp_audit` table with a logged change |
| 6 — App | `06-admin-login.png` | the new email+password+MFA admin login screen |
| 6 — App | `06-totp-enroll.png` | scanning the TOTP QR in an authenticator app |
| 7 — Verify | `07-advisor-clean.png` | Supabase security advisor after fixes |
| 7 — Verify | `07-denied-non-admin.png` | a non-admin/anon blocked from reading RSVPs |
| 9 — SIEM | `09-axiom-dashboard.png` | Axiom dashboard of auth/traffic events |
| 9 — SIEM | `09-axiom-alert.png` | an alert rule (e.g. failed admin logins) |

Tip: Windows snip = **Win + Shift + S**.
