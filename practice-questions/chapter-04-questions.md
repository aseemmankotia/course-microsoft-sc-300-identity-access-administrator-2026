## Chapter 4: Conditional Access: Assignments, Conditions & Controls — Practice Questions

**Q1.** A company requires that all users sign in with MFA unless they are on a hybrid Azure AD joined OR Intune-compliant device from a trusted named location. Which configuration achieves this with the FEWEST policies?

A) Two separate policies: one requiring MFA for all users, another requiring compliant device for all users, both enabled
B) One policy with Grant control set to 'Require one of the selected controls': Require MFA OR Require compliant device OR Require hybrid join
C) Mark the corporate IP range as trusted and exclude the trusted location from a sign-in risk policy
D) One policy assigned to all users/cloud apps, using a Filter for devices condition to exclude devices marked compliant or hybrid joined, plus a trusted named location exclusion, with Grant control = Require MFA

<details>
<summary>Answer</summary>

**Correct: D**

A single policy using device filter conditions and named location exclusions correctly scopes MFA enforcement only to non-compliant, non-hybrid, non-trusted-location sign-ins.

**Why the others are wrong:**
- Two separate always-on policies stack with AND logic across policies, forcing MFA AND compliant device for everyone, everywhere — not the intended exception.
- 'Require one of' lets ANY single control satisfy access, meaning a user could bypass MFA just by being hybrid joined even from an untrusted location — wrong logic for the requirement.
- This only affects a risk-based policy and does nothing to control MFA requirements based on device state.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A user signs in and their sign-in matches conditions for two active Conditional Access policies. Policy A's grant control is 'Require MFA'. Policy B's grant control is 'Require hybrid Azure AD joined device'. What is the result?

A) Only the policy with the higher configured priority is enforced
B) The user must satisfy BOTH MFA and hybrid join requirements, because all applicable policies are enforced with AND logic
C) The user satisfies whichever policy's requirement is completed first; the other is skipped
D) Azure AD automatically merges the two policies into one policy using OR logic

<details>
<summary>Answer</summary>

**Correct: B**

Conditional Access policies have no priority ordering — every applicable policy must be independently satisfied, meaning the requirements are combined with AND logic.

**Why the others are wrong:**
- Conditional Access policies do not have a priority/ordering mechanism like NSG rules or Azure Policy.
- There is no 'first completed wins' mechanic; unmet requirements from any applicable policy will block access.
- Policies are evaluated independently and never automatically merged.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** An administrator wants to determine the impact of a new Conditional Access policy requiring MFA for all users before enforcing it in production. What should the administrator do?

A) Set the policy state to Report-only and review the Conditional Access tab in sign-in logs for would-be results
B) Enable the policy and monitor the Azure AD sign-in logs for authentication failures
C) Run the What If tool against every user in the tenant individually before enabling
D) Deploy the policy first in a separate test tenant, then recreate it in production

<details>
<summary>Answer</summary>

**Correct: A**

Report-only mode evaluates the policy against real sign-ins without enforcing grant or block, logging 'Report-only: Success/Failure' results for safe impact analysis.

**Why the others are wrong:**
- Enabling the policy live risks locking out users before impact is understood — exactly what Report-only mode avoids.
- The What If tool tests one user/condition combination at a time and is meant for troubleshooting a specific scenario, not bulk impact analysis across the tenant.
- A separate tenant does not reflect real production sign-in patterns and adds unnecessary overhead; it is not the standard approach.

</details>

---

**Q4.** Which Conditional Access condition requires Azure AD Premium P2 (Identity Protection) to be evaluated?

A) Sign-in risk
B) Device platform
C) Client apps
D) Named locations

<details>
<summary>Answer</summary>

**Correct: A**

Sign-in risk and user risk conditions rely on Identity Protection's risk detections, which require Azure AD Premium P2 licensing.

**Why the others are wrong:**
- Device platform is a P1-level condition, available without Identity Protection.
- Client apps is a P1-level condition used to distinguish browser, mobile, and desktop app access.
- Named locations (IP ranges/countries) are a P1-level condition used for location-based policies.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** An admin configures a Conditional Access policy with grant controls 'Require MFA' and 'Require compliant device', set to 'Require one of the selected controls'. What is required for the user to gain access?

A) The user must satisfy MFA AND have a compliant device
B) Access is blocked entirely regardless of the controls selected
C) The user must satisfy either MFA OR have a compliant device — only one control needs to be met
D) Neither control is enforced because the policy is effectively disabled

<details>
<summary>Answer</summary>

**Correct: C**

'Require one of the selected controls' applies OR logic — satisfying any single listed control is sufficient for access.

**Why the others are wrong:**
- AND logic (requiring every control) only applies when 'Require all the selected controls' is chosen.
- Grant controls that are satisfied result in access being granted, not blocked.
- The policy is fully active; OR logic simply lowers the bar to any one control being met.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** How does an administrator mark a named location's IP ranges as trusted so it can be used to reduce MFA prompts or lower risk scoring?

A) Conditional Access > Named locations > New IP location, then check 'Mark as trusted location'
B) Add the IP addresses to a Conditional Access policy's exclude group
C) Configure the IP ranges under Azure AD Connect trusted zones
D) Add the IP ranges to the tenant's allowed domains list

<details>
<summary>Answer</summary>

**Correct: A**

Named locations support marking specific IP ranges as trusted directly in the Named Locations blade, which then can be referenced in policy conditions.

**Why the others are wrong:**
- Exclude groups are for users/groups, not IP ranges, and don't create a trusted location object.
- Azure AD Connect trusted zones is not a real Conditional Access feature.
- Allowed domains lists relate to B2B collaboration settings, not named locations.

</details>

---

**Q7.** You want users to reauthenticate every 4 hours when accessing a sensitive line-of-business app from an unmanaged device. Which session control should you configure?

A) Persistent browser session set to Never persistent
B) App-enforced restrictions
C) Sign-in frequency set to 4 hours
D) Cloud App Security session control

<details>
<summary>Answer</summary>

**Correct: C**

Sign-in frequency forces periodic reauthentication at a defined interval, regardless of existing valid tokens.

**Why the others are wrong:**
- Persistent browser session controls whether the browser remembers the session after closing, not periodic reauthentication timing.
- App-enforced restrictions only work with apps that natively support passing device signals (e.g., SharePoint, Exchange Online) and don't set reauthentication intervals.
- Cloud App Security session control (via Defender for Cloud Apps) is for real-time monitoring/blocking actions, not scheduled reauthentication.

</details>

---

**Q8.** What is the fundamental difference between grant controls and session controls in Conditional Access?

A) Grant controls apply only to browser-based access, while session controls apply only to native mobile apps
B) Grant controls determine whether access is allowed or denied and what's required to obtain it; session controls restrict the ongoing experience within an already-granted session
C) Grant controls are evaluated before authentication completes, while session controls only activate during a detected risk event
D) Grant controls require Azure AD Premium P1, while session controls require Azure AD Premium P2

<details>
<summary>Answer</summary>

**Correct: B**

Grant controls (MFA, compliant device, hybrid join, etc.) gate the initial access decision; session controls (sign-in frequency, persistent browser, app-enforced restrictions) limit what happens after access is granted.

**Why the others are wrong:**
- Both grant and session controls can apply across browser and native app clients depending on configuration — this isn't a fixed boundary.
- Session controls are not tied to risk detection; they apply based on policy assignment regardless of risk state.
- Licensing for most grant and session controls (MFA, sign-in frequency, compliant device) is P1-level; the split described is inaccurate.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

