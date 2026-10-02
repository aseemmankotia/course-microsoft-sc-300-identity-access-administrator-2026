## Chapter 5: Microsoft Entra ID Protection: Risk Detections & Risk Policies — Practice Questions

**Q1.** A user's sign-in triggers a 'leaked credentials' risk detection. The security team wants Microsoft Entra ID Protection to automatically force this user to change their password before they can access any resource, regardless of which app they sign into next. Which policy type should be configured?

A) Sign-in risk policy requiring MFA
B) User risk policy requiring a password change
C) A Conditional Access policy blocking legacy authentication
D) An access review requiring manager approval

<details>
<summary>Answer</summary>

**Correct: B**

Leaked credentials is a user risk detection tied to the account itself, not a single session. User risk policy is the only policy type whose remediation action is 'require password change', which invalidates the compromised credential everywhere.

**Why the others are wrong:**
- Sign-in risk policy remediates via MFA, not password change — it doesn't invalidate the leaked password.
- Blocking legacy auth is unrelated to remediating a leaked credential detection.
- Access reviews are for periodic entitlement recertification, not real-time risk remediation.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A user signs in from Tokyo, then 20 minutes later signs in from New York — a physically impossible travel pattern. Identity Protection flags this at Medium risk. The tenant has a risk-based Conditional Access policy requiring MFA when sign-in risk is Medium or High. What happens if the user successfully completes MFA?

A) The user account is permanently locked until an admin dismisses the risk
B) The sign-in is allowed and the sign-in risk is remediated for that session
C) The user's password is automatically reset
D) The detection is deleted from the risk detections report

<details>
<summary>Answer</summary>

**Correct: B**

Sign-in risk is session-scoped. Successfully satisfying the required control (MFA) remediates the risk for that specific sign-in and access is granted.

**Why the others are wrong:**
- Sign-in risk policies don't lock accounts — that's a user risk policy configured to block access.
- Sign-in risk remediation is MFA, not password reset — password reset is the user risk remediation.
- Remediated detections remain visible in reports with a 'remediated' status; they aren't deleted.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** An organization wants users who are flagged as risky to be able to fix their own account risk without contacting the helpdesk. Which prerequisite MUST be in place for self-remediation to work?

A) The user must be assigned an Entra ID P1 license
B) The user must be a member of the Global Administrator role
C) The user risk policy must be set to 'Report-only' mode
D) Self-service password reset (SSPR) must be enabled and the user must be registered for MFA

<details>
<summary>Answer</summary>

**Correct: D**

Self-remediation via user risk policy requires SSPR to be enabled (so the user can reset their password) and combined registration for MFA (so they can prove identity before resetting).

**Why the others are wrong:**
- Risk policies and self-remediation require P2, not just P1.
- Being a Global Admin has nothing to do with self-remediation eligibility.
- Report-only mode only logs what would happen — it doesn't enforce or allow remediation.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** Which Microsoft Entra ID license is required to configure and enforce automated User risk and Sign-in risk policies (not just report-only evaluation) in Identity Protection?

A) Microsoft Entra ID Free
B) Microsoft Entra ID P2
C) Microsoft Entra ID P1
D) Microsoft 365 Business Basic

<details>
<summary>Answer</summary>

**Correct: B**

Full Identity Protection capability — the risk detection catalog, risk investigation, and enforceable user/sign-in risk policies — requires Microsoft Entra ID P2.

**Why the others are wrong:**
- Free tier has no risk detection or risk-based policy capability.
- P1 allows a limited real-time sign-in risk condition inside Conditional Access, but not the full Identity Protection policy set or user risk.
- M365 Business Basic doesn't include Entra ID P2 features by default.

</details>

---

**Q5.** A company has an admin-confirmed compromised user. The admin manually flags the account as 'Confirmed compromised' in Identity Protection. What is the immediate effect of this action?

A) The user's risk level is set to High and the user risk policy remediation is triggered
B) The user account is deleted from Microsoft Entra ID
C) The user's MFA methods are automatically re-registered
D) Nothing changes until the next sign-in attempt

<details>
<summary>Answer</summary>

**Correct: A**

Confirming a user as compromised sets their user risk to High immediately, which triggers whatever remediation the user risk policy specifies (typically forced password change or block).

**Why the others are wrong:**
- Confirming compromise never deletes the account.
- MFA methods aren't touched by this action; the user still uses existing methods to remediate.
- The risk state changes immediately in the directory, not just on next sign-in.

</details>

---

**Q6.** You are configuring a risk-based Conditional Access policy in the Microsoft Entra admin center. You want users detected at High sign-in risk to be blocked, but users at Low sign-in risk to sign in without extra friction. How should you configure the risk level condition?

A) Set 'User risk' condition to include only High
B) Enable Security Defaults instead of Conditional Access
C) Set 'Sign-in risk' condition to include only High, and create a separate policy or grant control that allows Low without extra requirements
D) Set the sign-in risk condition to 'All' and require MFA for every level

<details>
<summary>Answer</summary>

**Correct: C**

Sign-in risk (not user risk) is the correct condition for per-session, per-sign-in enforcement. Selecting only High for the block policy, and leaving Low unselected/unrestricted, achieves the desired graduated response.

**Why the others are wrong:**
- User risk is account-scoped and persistent — wrong condition for a per-sign-in block decision.
- Security Defaults offers no granular risk-level control.
- Requiring MFA for every level, including Low, adds unnecessary friction contrary to the stated requirement.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Which of the following is classified as a User risk detection rather than a Sign-in risk detection in Microsoft Entra ID Protection?

A) Anonymous IP address
B) Leaked credentials
C) Atypical travel (impossible travel)
D) Unfamiliar sign-in properties

<details>
<summary>Answer</summary>

**Correct: B**

Leaked credentials is discovered offline (e.g., dark web / paste site scans) and is tied to the account, not a specific sign-in, making it a user risk detection.

**Why the others are wrong:**
- Anonymous IP address is evaluated in real time during a specific sign-in — a sign-in risk detection.
- Atypical travel is evaluated based on the properties of a specific sign-in event — sign-in risk.
- Unfamiliar sign-in properties is also evaluated per sign-in session — sign-in risk.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Which statement correctly distinguishes the legacy Identity Protection 'User risk policy' / 'Sign-in risk policy' from risk-based Conditional Access policies?

A) Microsoft has been retiring the legacy Identity Protection policies in favor of configuring user risk and sign-in risk conditions directly within Conditional Access policies
B) The legacy policies support custom risk detections that Conditional Access cannot use
C) Legacy policies require Entra ID P1, while Conditional Access risk policies require P2
D) Risk-based Conditional Access policies cannot be scoped to specific groups or apps

<details>
<summary>Answer</summary>

**Correct: A**

Microsoft has been consolidating risk-based enforcement into Conditional Access, using the User risk and Sign-in risk conditions there, and retiring the classic standalone Identity Protection policies.

**Why the others are wrong:**
- Both approaches draw from the same underlying risk detection engine — there's no separate detection set exclusive to legacy policies.
- The license requirement is the same regardless of where the policy is configured — P2 for full risk-based enforcement.
- Conditional Access risk policies can be scoped by users, groups, and applications just like any other CA policy.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

