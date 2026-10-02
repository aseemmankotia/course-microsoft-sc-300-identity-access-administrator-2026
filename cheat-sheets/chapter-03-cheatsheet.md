## Ch.3 Cheat Sheet — MFA, Passwordless & SSPR

### Authentication Methods Policy vs Legacy
| Feature | Legacy MFA Service Settings / Per-User MFA | Authentication Methods Policy |
|---|---|---|
| Scope | Per-user On/Off/Enforced | Tenant-wide, per-method, group-targeted |
| Controls | App passwords, trusted IPs, remember MFA | Authenticator, FIDO2, TAP, CBA, SMS, Voice, WHfB |
| Number matching | Not configurable here | Configured here; Microsoft-managed default = **ON** (since May 2023) |
| Exam status | Being retired | Modern, tested surface |

### Passwordless Methods
| Method | Phishing-resistant? | Needs network? | Onboarding use |
|---|---|---|---|
| FIDO2 security key | Yes | No (local crypto) | Registered via Security Info |
| Windows Hello for Business | Yes | No | Built into device sign-in |
| Microsoft Authenticator (passwordless) | Partial (number matching helps) | Yes | App-based |
| Temporary Access Pass | N/A (bootstrap only) | Yes | Issues to new/locked-out users |

### Windows Hello for Business Deployment Models
| Model | PKI Required? | On-prem dependency | Recommended for |
|---|---|---|---|
| Cloud Kerberos Trust | No | Minimal | Hybrid, current default recommendation |
| Key Trust | No | Higher (line-of-sight to DC, WS2016+ DFL) | Hybrid, legacy deployments |
| Certificate Trust | Yes (AD CS) | Yes | Orgs with existing PKI |
| Cloud-only | No | None | Pure Azure AD-joined devices |

### SSPR
- Number of methods required: **1 or 2** (admin choice)
- Security Questions: only selectable when **2 methods required**
- Methods: Mobile app notification, Mobile app code, Email, Mobile phone, Office phone, Security questions
- Combined registration: unifies MFA + SSPR setup at **aka.ms/mysecurityinfo**

### Temporary Access Pass (TAP)
- Lifetime: **10 minutes – 30 days**
- One-time use toggle available
- Used to onboard passwordless credentials without a password
- Can be scoped so it can't be used to reset other users' credentials

### Number Matching
- Default (Microsoft managed): **Enabled** since May 2023
- Configured in: Authentication methods policy > Microsoft Authenticator > Configure
- Purpose: mitigates MFA fatigue / push-bombing attacks

### Exam Gotchas
1. Legacy per-user MFA does **not** control FIDO2/WHfB — that's Authentication methods policy only.
2. Security Questions cannot be the only SSPR method when only 1 method is required.
3. Number matching is no longer a phone-app toggle — it's tenant policy, on by default.
4. Cloud Kerberos Trust ≠ Key Trust — Cloud Kerberos Trust has fewer on-prem prerequisites.
5. TAP always expires (max 30 days) — never permanent.
