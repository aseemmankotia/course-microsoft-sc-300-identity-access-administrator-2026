## Chapter 3: Multi-Factor Authentication, Passwordless & Self-Service Password Reset — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Since when has number matching been the Microsoft-managed default for Authenticator push notifications? | May 2023. It's now enabled tenant-wide by default and configured in the Authentication methods policy, not the legacy portal or the phone app. |
| 2 | Temporary Access Pass (TAP) — minimum and maximum lifetime? | Minimum 10 minutes, maximum 30 days (43,200 minutes). Can also be restricted to one-time use. Exam tip: used to bootstrap passwordless registration without a password. |
| 3 | SSPR — how many methods can be required for password reset? | 1 or 2 (admin-configurable). Exam tip: Security Questions can only be selected when 2 methods are required, never when only 1 is required. |
| 4 | Windows Hello for Business: name the 4 deployment models. | Cloud Kerberos Trust, Key Trust, Certificate Trust, Cloud-only. Exam tip: Cloud Kerberos Trust is the current recommended hybrid model — no PKI, lightest prerequisites. |
| 5 | Key Trust vs Certificate Trust for WHfB — key difference? | Key Trust needs no PKI but requires Windows Server 2016+ DFL and key sync; Certificate Trust requires AD CS to issue authentication certificates to users. |
| 6 | Cloud Kerberos Trust vs Key Trust — main advantage? | Cloud Kerberos Trust removes the need for the on-prem key-writeback/line-of-sight-to-DC requirement that Key Trust has, simplifying hybrid deployment. |
| 7 | FIDO2 security key vs Authenticator push — which is phishing-resistant? | FIDO2. It uses origin-bound public-key cryptography, resistant to phishing and MFA-fatigue attacks; push (even with number matching) still relies on network round-trips and user approval. |
| 8 | Where do you enable/restrict FIDO2, Authenticator, TAP, and Certificate-Based Auth tenant-wide? | Entra admin center > Protection > Authentication methods > Policies. This replaces the legacy MFA service settings page for method management. |
| 9 | Combined security info registration — what is it and where do users go? | A single registration experience for both MFA and SSPR methods, at aka.ms/mysecurityinfo (or My Account > Security info). Enabled by default for new tenants. |
| 10 | SSPR rule: when can Security Questions be used as an authentication method? | Only when 'Number of methods required' is set to 2. It cannot be the sole method when only 1 method is required. |
| 11 | Legacy per-user MFA states (old model)? | Disabled, Enabled, Enforced — configured per user in the legacy MFA service settings blade. Exam tip: this legacy surface is being retired in favor of Conditional Access + Authentication methods policy. |
| 12 | App passwords — what are they used for and where configured? | Legacy bypass credentials for non-browser apps that don't support modern MFA prompts; configured in legacy MFA service settings. Exam tip: not usable when Security Defaults or most CA-based MFA setups are in place. |
