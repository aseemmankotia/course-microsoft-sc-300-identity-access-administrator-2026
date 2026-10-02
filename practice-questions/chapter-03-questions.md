## Chapter 3: Multi-Factor Authentication, Passwordless & Self-Service Password Reset — Practice Questions

**Q1.** A security team must ensure that Global Administrators can only sign in using phishing-resistant credentials, even from personal unmanaged devices where installing an app is not permitted. Which authentication method should be enabled and enforced?

A) FIDO2 security key
B) SMS verification
C) Voice call verification
D) Microsoft Authenticator push without number matching

<details>
<summary>Answer</summary>

**Correct: A**

FIDO2 security keys use public-key cryptography bound to the origin, making them resistant to phishing and MFA-fatigue attacks, and they don't require any app to be installed on the device.

**Why the others are wrong:**
- SMS is phishable via SIM swap and OTP relay attacks, and the exam treats it as low-assurance.
- Voice call has the same phishing weaknesses as SMS and is the lowest-assurance method Entra ID offers.
- Push without number matching is vulnerable to MFA fatigue/push-bombing, which is exactly why number matching now defaults to enabled.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** An admin needs to let a remote new hire, who has no existing credentials, register Microsoft Authenticator and a FIDO2 key on day one without ever knowing a password. Which feature should the admin issue to the user?

A) SSPR security questions
B) App password
C) Temporary Access Pass (TAP)
D) Legacy per-user MFA trusted IP exemption

<details>
<summary>Answer</summary>

**Correct: C**

A Temporary Access Pass is a time-limited passcode issued by an admin that lets a user sign in and register passwordless methods (Authenticator, FIDO2, WHfB) without knowing a password.

**Why the others are wrong:**
- Security questions are an SSPR reset method, not an onboarding credential for new users.
- App passwords are a legacy MFA bypass mechanism for non-browser apps, unrelated to onboarding.
- Trusted IP is a Conditional Access/legacy MFA network exemption, not a credential provisioning tool.

</details>

---

**Q3.** An admin configures SSPR with 'Number of methods required to reset' set to 1, and Security Questions is the only method enabled under authentication methods. Users report they cannot satisfy combined registration for SSPR. What is the cause?

A) SSPR is disabled by default and must be enabled separately in Conditional Access
B) Security Questions require Azure AD Premium P2, which the tenant lacks
C) Combined registration blocks Security Questions entirely regardless of configuration
D) Security Questions cannot be used when only 1 method is required — it only becomes selectable once 2 methods are required

<details>
<summary>Answer</summary>

**Correct: D**

Entra ID treats Security Questions as a weak single factor, so the portal only allows it as an authentication method when the policy requires 2 methods for reset, never when only 1 is required.

**Why the others are wrong:**
- SSPR is enabled/disabled per-policy independent of Conditional Access and was clearly configured here.
- Security Questions is a free-tier SSPR method available in Azure AD Free/M365 for cloud-only users, not a P2 feature.
- Security Questions can be used, just not as the sole method — it's not blocked outright.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A hybrid organization with a Windows Server 2016 domain functional level wants passwordless Windows sign-in for hybrid Azure AD-joined devices but has no PKI/AD CS infrastructure and wants the least deployment complexity. Which Windows Hello for Business deployment model should be used?

A) Cloud Kerberos Trust
B) Certificate Trust
C) Key Trust
D) Cloud-only deployment

<details>
<summary>Answer</summary>

**Correct: A**

Cloud Kerberos Trust is the current recommended hybrid model — it requires no PKI and no on-prem key registration writeback, simplifying deployment while still enabling on-prem resource access.

**Why the others are wrong:**
- Certificate Trust requires Active Directory Certificate Services to issue authentication certificates, which the org doesn't have.
- Key Trust works without PKI but has heavier prerequisites (key sync via Azure AD Connect, line-of-sight to a DC) making it more complex than Cloud Kerberos Trust.
- Cloud-only applies to Azure AD-joined devices with no on-prem AD at all — it doesn't apply to hybrid-joined devices needing on-prem resource access.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** Which authentication method offers the strongest resistance to real-time phishing and MFA-fatigue push-bombing attacks while also working when the device has no network connectivity?

A) SMS one-time passcode
B) Voice call verification
C) Microsoft Authenticator push notification
D) FIDO2 security key

<details>
<summary>Answer</summary>

**Correct: D**

FIDO2 uses a hardware-bound cryptographic challenge-response performed locally on the device, so it works offline and can't be relayed or phished like OTP or push approvals.

**Why the others are wrong:**
- SMS OTPs can be phished/relayed and depend on cellular network availability.
- Voice call has the same phishing and connectivity weaknesses as SMS.
- Authenticator push requires network connectivity and, without number matching, is susceptible to fatigue attacks.

</details>

---

**Q6.** An admin wants Microsoft Authenticator push notifications to require the end user to type a number displayed on the sign-in screen into the app. Where must this be configured?

A) Legacy multifactor authentication service settings
B) Authentication methods policy > Microsoft Authenticator > Configure
C) Conditional Access > Grant controls
D) The Microsoft Authenticator app's local settings on the phone

<details>
<summary>Answer</summary>

**Correct: B**

Number matching is a per-method setting managed under the Authentication methods policy for Microsoft Authenticator, and it is enabled by default (Microsoft managed) tenant-wide since May 2023.

**Why the others are wrong:**
- Legacy MFA service settings do not expose number-matching controls — that surface is being deprecated in favor of the Authentication methods policy.
- Conditional Access controls when MFA is required, not how the Authenticator prompt behaves.
- Number matching is enforced server-side by Entra ID, not a toggle inside the mobile app itself.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** What is the maximum lifetime an admin can configure for a Temporary Access Pass in the Authentication methods policy?

A) 30 days
B) 90 days
C) 1 year
D) Unlimited (no expiration)

<details>
<summary>Answer</summary>

**Correct: A**

TAP lifetime is configurable between 10 minutes and 30 days (43,200 minutes); it always expires and can also be restricted to one-time use.

**Why the others are wrong:**
- 90 days exceeds the documented maximum and is not a selectable value.
- 1 year is far beyond the allowed range for a TAP, which is meant to be short-lived.
- TAP always has an expiration — it cannot be set to never expire.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Which statement correctly describes the relationship between the Authentication methods policy and legacy per-user MFA / legacy MFA service settings?

A) The Authentication methods policy is the modern, unified control plane for enabling and restricting auth methods tenant-wide, and Microsoft is retiring the legacy per-user MFA and legacy MFA service settings surfaces
B) Legacy per-user MFA is required to enable FIDO2 and Windows Hello for Business registration
C) Legacy MFA service settings control number matching, while the Authentication methods policy only manages SMS and voice
D) The Authentication methods policy applies only to Azure AD B2B guest users, not member users

<details>
<summary>Answer</summary>

**Correct: A**

Microsoft consolidated method management into the Authentication methods policy (covering Authenticator, FIDO2, TAP, certificate-based auth, SMS, voice, etc.) and is deprecating the older per-user MFA on/off/enforced model and the legacy MFA service settings page.

**Why the others are wrong:**
- FIDO2 and WHfB are enabled/managed exclusively in the Authentication methods policy, not legacy per-user MFA.
- Number matching is controlled by the Authentication methods policy's Microsoft Authenticator settings, not legacy MFA service settings.
- The Authentication methods policy applies to all users in the tenant, member and guest alike, subject to group targeting.

</details>

---

