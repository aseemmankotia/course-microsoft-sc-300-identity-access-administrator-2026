## Chapter 7: App Registrations, Service Principals & API Permissions — Practice Questions

**Q1.** A backend service runs on a nightly schedule with no signed-in user and must read all users' mailbox items via Microsoft Graph. Which permission type and consent should be configured on the app registration?

A) Delegated permission, Mail.Read, with admin consent
B) Delegated permission, Mail.Read, with user consent
C) Application permission, Mail.Read, with admin consent
D) Application permission, Mail.Read, with user consent

<details>
<summary>Answer</summary>

**Correct: C**

No signed-in user is present, so the app must act as itself using an application permission. Application permissions always require admin consent — there is no user-consent path for them.

**Why the others are wrong:**
- Delegated permissions require a signed-in user context, which does not exist for an unattended nightly job.
- Delegated permissions are the wrong permission type for a daemon with no user context, regardless of consent method.
- Application permissions cannot be granted via user consent under any tenant setting — the option does not exist.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** In Azure AD (Microsoft Entra ID), what is the relationship between an app registration's application object and its service principal?

A) The application object and service principal are the same object, just shown in two different portal blades
B) The service principal is created first and the application object is generated automatically only when the app is multi-tenant
C) The application object exists in every tenant that uses the app, while the service principal exists only in the home tenant
D) The application object is the global definition created once in the home tenant; a service principal is the local, tenant-specific instance created wherever the app is used

<details>
<summary>Answer</summary>

**Correct: D**

The application object is the global template stored only in the app's home directory. A service principal (shown as an Enterprise Application) is created in every tenant — including the home tenant — where the app is granted access, and it is the object actually referenced during authentication and authorization.

**Why the others are wrong:**
- They are distinct object types with different schemas and different scopes (global vs per-tenant), not just different UI views.
- The application object is created first, at registration time, in the home tenant; the service principal follows.
- This reverses the actual behavior — the application object is single-tenant-scoped (home tenant only) while service principals can exist in multiple tenants.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A company is building a SaaS application that other organizations' Azure AD tenants will consent to and use with their own users. Which supported account type should be selected during app registration?

A) Accounts in any organizational directory (Any Azure AD directory - Multitenant)
B) Accounts in this organizational directory only
C) Personal Microsoft accounts only
D) Accounts in any organizational directory and personal Microsoft accounts, with a managed identity enabled

<details>
<summary>Answer</summary>

**Correct: A**

A SaaS app consumed by multiple external Azure AD tenants must be registered as multi-tenant so that a service principal can be provisioned in each consuming tenant when they consent.

**Why the others are wrong:**
- Single-tenant restricts sign-in and consent to the home tenant only — external tenants could not use the app.
- Personal accounts only would exclude all organizational (work/school) tenants entirely.
- Managed identities are for Azure resources authenticating to Azure AD, not for a customer-facing multi-tenant SaaS app registration.

</details>

---

**Q4.** An administrator is creating a new client secret for an app registration in the Azure portal. What is the maximum validity period they can select?

A) 12 months
B) 18 months
C) 24 months
D) 36 months

<details>
<summary>Answer</summary>

**Correct: C**

Client secrets can be created with a maximum lifetime of 24 months (2 years) in the portal. Certificates are recommended over secrets for longer-lived, higher-security scenarios.

**Why the others are wrong:**
- 12 and 18 months are valid selectable durations but not the maximum available option.
- 18 months is a valid shorter preset, not the maximum.
- 36 months exceeds the platform-enforced maximum secret lifetime.

</details>

---

**Q5.** A regular user (no admin role) attempts to sign in to a third-party app that requests the application permission Directory.Read.All. Tenant consent settings block user consent for this permission, but the admin consent workflow is enabled. What happens?

A) The user is automatically granted access because application permissions bypass consent settings
B) The sign-in fails permanently with no recourse for the user
C) The app is automatically registered as an enterprise application without any consent
D) The user can submit a consent request that is routed to a designated reviewer (e.g., Global Administrator or Cloud Application Administrator) for approval

<details>
<summary>Answer</summary>

**Correct: D**

The admin consent workflow lets a blocked user submit a request that notifies assigned reviewers (users in roles such as Global Administrator, Application Administrator, or Cloud Application Administrator, or specifically designated reviewers), who can approve or deny it — the request expires after a configurable number of days (default 30).

**Why the others are wrong:**
- Application permissions specifically require explicit admin consent — they are never auto-granted.
- Without the workflow, sign-in would indeed fail with no path forward, but the workflow being enabled provides a request path.
- Enterprise application (service principal) creation happens at first use, but permission grant still requires consent — it is not automatic.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** A user with no administrative role consents to an app requesting the delegated permission User.Read.All on their own behalf. What access does the app actually receive?

A) Full read access to all users in the tenant, because User.Read.All always grants tenant-wide access once consented
B) No access at all, because a non-admin can never consent to User.Read.All
C) Access is granted but only takes effect after a Global Administrator manually approves the token
D) Access limited to what the consenting user themself is authorized to see, since delegated permissions are bounded by the signed-in user's own privileges

<details>
<summary>Answer</summary>

**Correct: D**

Delegated permissions grant the app the ability to act as the signed-in user, but the effective access is always capped by that user's own directory privileges — a non-admin user's consent to User.Read.All will not expose data they themselves couldn't otherwise access.

**Why the others are wrong:**
- This ignores the fundamental delegated-permission rule that access is bounded by the user's own privileges — the app does not get more access than the user has.
- Depending on tenant consent settings, non-admins CAN consent to User.Read.All (it is not admin-restricted by default in all tenants), but the effective scope is still limited.
- Delegated consent by the user takes effect immediately; no separate admin approval step occurs unless admin consent was specifically required by policy.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A development team wants business users to be assigned one of three custom access levels (Viewer, Editor, Admin) within their line-of-business application, enforced and visible as a claim in the issued token. What should they configure?

A) Azure AD Privileged Identity Management role assignments
B) Delegated permissions scoped per user in the API permissions blade
C) App roles defined in the application manifest, assigned to users or groups on the enterprise application
D) Conditional Access policies with custom session controls

<details>
<summary>Answer</summary>

**Correct: C**

App roles are custom roles defined in the app registration's manifest (appRoles) and assigned to users/groups (or other service principals) on the corresponding enterprise application. They appear in the token as the 'roles' claim, which the app's own authorization code checks.

**Why the others are wrong:**
- PIM manages just-in-time elevation for Azure AD built-in/Azure roles, not custom application-defined authorization roles.
- Delegated permissions control what Microsoft Graph/API data the app can access on behalf of a user — they are not custom app-defined business roles.
- Conditional Access controls sign-in conditions (MFA, location, device) — it does not define or issue custom authorization roles.

</details>

---

**Q8.** A tenant administrator wants to reduce consent-related risk while still allowing employees to install low-risk apps without IT involvement. Which user consent setting should be configured?

A) Do not allow user consent
B) Allow user consent for all apps
C) Allow user consent for apps from verified publishers, or for permissions classified as low risk
D) Disable the admin consent workflow entirely

<details>
<summary>Answer</summary>

**Correct: C**

This middle-ground setting lets users consent only to apps published by verified publishers requesting permissions classified as low risk, blocking consent for unverified or high-risk apps while preserving self-service for safe scenarios.

**Why the others are wrong:**
- This blocks ALL user consent, forcing every app through the admin consent workflow, which removes self-service entirely — more restrictive than required.
- This allows consent to any app regardless of publisher verification or risk, which increases risk rather than reducing it.
- Disabling the admin consent workflow removes the fallback approval path for blocked requests, worsening the situation rather than balancing risk and usability.

</details>

---

