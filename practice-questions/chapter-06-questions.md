## Chapter 6: Privileged Identity Management: Just-In-Time Role Activation — Practice Questions

**Q1.** A company wants Global Administrators to gain access only when needed, requiring MFA, a justification, and manager approval, with automatic expiration after 8 hours. Which configuration meets this requirement?

A) Assign the users as eligible for Global Administrator, configure the role's activation settings to require MFA, justification, and approval, with maximum activation duration set to 8 hours
B) Assign the users as permanent active Global Administrators and enforce a Conditional Access MFA policy
C) Create a Microsoft 365 group with PIM for Groups and assign it the Global Administrator role
D) Use Identity Protection to require MFA whenever a Global Administrator signs in

<details>
<summary>Answer</summary>

**Correct: A**

PIM eligible assignments with role activation settings (require MFA, justification, approval, max duration) deliver time-bound, justified, approved access exactly as required.

**Why the others are wrong:**
- Permanent active assignment grants standing access — it does not satisfy the 'only when needed' and expiration requirement.
- PIM for Groups is for group membership/ownership, not directly for assigning a directory role to individuals with approval workflow described here.
- Conditional Access MFA enforces sign-in MFA but does not create time-bound eligibility, approval, or automatic expiration.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** External contractors need temporary Contributor access to a single Azure subscription, without receiving any Microsoft Entra directory role. Which PIM capability should you use?

A) PIM for Azure resource roles
B) PIM for Microsoft Entra roles
C) PIM for Groups
D) Access reviews for Microsoft 365 groups

<details>
<summary>Answer</summary>

**Correct: A**

PIM for Azure resource roles manages time-bound RBAC role assignments (e.g., Contributor) scoped to management groups, subscriptions, resource groups, or resources.

**Why the others are wrong:**
- PIM for Entra roles governs directory-wide roles like Global Administrator, not Azure RBAC roles.
- PIM for Groups grants membership/ownership of a group, which is an indirect and unnecessary layer for a single subscription-scoped RBAC assignment.
- Access reviews evaluate existing assignments/memberships; they don't grant time-bound access themselves.

</details>

---

**Q3.** An admin enables PIM for a cloud-only security group and sets membership as eligible. Activation must require a justification but no approval. Which setting accomplishes this?

A) Assign the group Owner role permanently and enable Conditional Access for the group
B) Configure the setting in the Microsoft Entra role settings blade instead of the group settings blade
C) Enable an access review with self-attestation instead of activation settings
D) In the group's PIM role settings for Member, require justification on activation and leave 'Require approval to activate' unchecked

<details>
<summary>Answer</summary>

**Correct: D**

PIM for Groups has its own activation settings blade (per Member/Owner) where you toggle justification and approval independently, matching the requirement exactly.

**Why the others are wrong:**
- A permanent Owner assignment removes the eligible/activation model entirely.
- Entra role settings apply to directory roles, not to group membership/ownership managed via PIM for Groups.
- Access reviews audit existing assignments periodically; they do not control activation requirements.

</details>

---

**Q4.** What is the key difference between an eligible assignment and an active assignment in Microsoft Entra PIM?

A) Eligible assignments never expire, while active assignments always expire after 24 hours
B) Eligible assignments only apply to Azure resource roles; active assignments only apply to Entra roles
C) Active assignments always require MFA, while eligible assignments never do
D) An eligible assignment requires the user to perform an activation step before using the role; an active assignment grants immediate use of the role's permissions without activation

<details>
<summary>Answer</summary>

**Correct: D**

Eligible = must activate (subject to MFA/justification/approval) before the permissions apply; Active = permissions are already in effect (permanently or for a fixed window) with no activation step.

**Why the others are wrong:**
- Expiration behavior is independent of eligible/active — both can be time-bound or permanent depending on role settings.
- Both eligible and active assignment types apply to Entra roles, Azure resource roles, and PIM for Groups.
- MFA/justification requirements are configured per role activation settings and apply to eligible activation, not tied to active assignments in this way.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** Your tenant has 12 permanent Global Administrators. Which PIM alert is most likely to be triggered?

A) Roles are being assigned outside of Privileged Identity Management
B) Duplicate role assignments exist
C) Roles aren't being used
D) There are too many global administrators

<details>
<summary>Answer</summary>

**Correct: D**

Microsoft recommends organizations keep between 2 and 4 Global Administrators; PIM raises a dedicated alert when the count of standing Global Administrators exceeds this recommendation.

**Why the others are wrong:**
- That alert fires when roles are assigned directly in the Entra admin portal/Graph rather than through PIM, unrelated to admin count.
- That alert flags the same principal assigned to a role through multiple paths (e.g., direct + group), not overall admin count.
- That alert flags eligible roles that are never activated, not an excess of standing assignments.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** You need eligible assignments for the Global Reader role reviewed every quarter, where assigned users confirm their own continued need. Which feature should you configure?

A) A PIM alert for unused roles
B) A Conditional Access policy targeting the Global Reader role
C) PIM for Groups applied to the Global Reader role
D) An access review scoped to the Global Reader role, recurring quarterly, with self-review enabled

<details>
<summary>Answer</summary>

**Correct: D**

Access reviews for privileged roles can be scoped to a specific Entra role, set to recur on a schedule (weekly/monthly/quarterly/annually), and configured for self-review by the assigned user.

**Why the others are wrong:**
- Alerts notify admins of risky configurations but don't drive a recurring attestation workflow.
- Conditional Access controls sign-in requirements, not periodic recertification of role assignments.
- PIM for Groups manages group membership/ownership, not periodic review of directory role assignments directly.

</details>

---

**Q7.** Which licensing is required to use Microsoft Entra Privileged Identity Management?

A) Microsoft Entra ID P2 or Microsoft Entra ID Governance
B) Microsoft Entra ID Free
C) Microsoft Entra ID P1
D) Microsoft Defender for Identity

<details>
<summary>Answer</summary>

**Correct: A**

PIM is a premium feature requiring Microsoft Entra ID P2 (or the Entra ID Governance add-on/license) for users who are eligible for or manage privileged roles.

**Why the others are wrong:**
- The Free tier does not include PIM at all.
- P1 provides Conditional Access and other premium features but not PIM.
- Defender for Identity is a separate on-premises threat detection product, unrelated to PIM licensing.

</details>

---

**Q8.** A user is eligible for the Exchange Administrator role but cannot perform admin tasks in the Exchange admin center. What must they do?

A) Go to My Roles in PIM and activate the Exchange Administrator role, completing any required MFA/justification/approval
B) Wait for the tenant's scheduled maintenance window
C) Ask a Global Administrator to reassign the role directly in the Entra admin center
D) Enable PIM for Groups for their user account

<details>
<summary>Answer</summary>

**Correct: A**

Eligible assignments grant no standing permissions — the user must explicitly activate via PIM > My Roles, satisfying any configured MFA, justification, or approval before the role permissions apply.

**Why the others are wrong:**
- There is no maintenance-window concept in PIM; activation is on-demand.
- Direct reassignment bypasses PIM's eligible model and creates a standing (active) assignment, which is not the intended workflow and is a common exam distractor.
- PIM for Groups applies to group-based eligibility, not to this individually eligible directory role scenario.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

