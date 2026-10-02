## Chapter 10: Lifecycle Workflows & Application Access Governance — Practice Questions

**Q1.** A company wants an employee's account to be disabled and removed from all groups the moment HR marks the employee as terminated, without waiting for the normal scheduled run. Which built-in Lifecycle Workflow template should be used?

A) Post-offboarding of an employee
B) Onboard employee transferring between departments
C) Real-time employee termination
D) Onboard new hire employee (with pre-hire tasks)

<details>
<summary>Answer</summary>

**Correct: C**

The 'Real-time employee termination' template triggers immediately on the employeeLeaveDateTime attribute update rather than waiting for the scheduled workflow run.

**Why the others are wrong:**
- Post-offboarding runs AFTER the leave date on the normal schedule, not immediately
- This is a mover template, unrelated to termination
- This is a joiner template for onboarding, not termination

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** An admin configures a Joiner workflow so a welcome email is sent to a new hire's manager 7 days before the employee's start date, and the account is enabled on the start date. Which trigger attribute drives the timing of this workflow?

A) employeeLeaveDateTime with a negative offset
B) employeeHireDate with a configured days-before offset
C) createdDateTime of the user object
D) A scheduled trigger set to run daily

<details>
<summary>Answer</summary>

**Correct: B**

Joiner workflows are triggered off the employeeHireDate attribute, and tasks can be scheduled with an offset of days before or after that date.

**Why the others are wrong:**
- employeeLeaveDateTime is used for leaver workflows, not joiner scenarios
- createdDateTime is not used as a Lifecycle Workflow trigger attribute
- A daily scheduled trigger doesn't tie task timing to the hire date offset

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A user attempts to consent to an application requesting a permission classified as high risk under the tenant's consent policy. The request is automatically routed to the admin consent workflow. Which role can approve this request by default without additional configuration?

A) User Administrator
B) Global Administrator
C) Helpdesk Administrator
D) Groups Administrator

<details>
<summary>Answer</summary>

**Correct: B**

By default, Global Administrator, Cloud Application Administrator, and Application Administrator roles can review and approve admin consent requests.

**Why the others are wrong:**
- User Administrator has no default rights over app consent requests
- Helpdesk Administrator manages password resets, not app consent
- Groups Administrator manages group objects, not application permission consent

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A security team needs to continuously identify OAuth applications in the tenant that hold excessive or unused Graph API permissions and flag them as risky. Which capability should they use?

A) Access reviews for Azure AD roles
B) Conditional Access App Control
C) Entitlement management access packages
D) App governance in Microsoft Defender for Cloud Apps

<details>
<summary>Answer</summary>

**Correct: D**

App governance (part of Microsoft Defender for Cloud Apps) analyzes OAuth app behavior and permissions, flags overprivileged and risky apps, and provides remediation policies.

**Why the others are wrong:**
- Access reviews for roles evaluate role assignments, not app OAuth permissions
- Conditional Access App Control enforces session controls, not permission risk analysis
- Entitlement management handles access package provisioning, not app risk detection

</details>

---

**Q5.** During onboarding, a company needs a Lifecycle Workflow to call an external HR system's REST API to create a payroll record. No built-in task supports this. What should be configured?

A) A conditional access policy targeting the workflow
B) An access package with a custom approval stage
C) A custom task extension calling an Azure Logic App
D) A dynamic group rule referencing the HR attribute

<details>
<summary>Answer</summary>

**Correct: C**

Custom task extensions let a Lifecycle Workflow invoke an Azure Logic App to run custom logic, such as calling an external API, beyond the built-in tasks.

**Why the others are wrong:**
- Conditional Access controls sign-in access, not workflow task execution
- Access packages handle entitlement requests, not workflow-level custom logic
- Dynamic groups control membership scope, not external API calls

</details>

---

**Q6.** A tenant enables the admin consent workflow but does not change any default settings. How long does an admin consent request remain open before it expires?

A) 7 days
B) 14 days
C) 90 days
D) 30 days

<details>
<summary>Answer</summary>

**Correct: D**

The default expiration for admin consent requests is 30 days; administrators can adjust this to any value between 1 and 90 days.

**Why the others are wrong:**
- 7 days is not the default value
- 14 days is not the default value
- 90 days is the maximum configurable value, not the default

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** An organization wants to reduce risk from user application consent while still allowing self-service for low-impact apps from trusted vendors. Which user consent setting best meets this requirement?

A) Allow user consent for all apps
B) Allow user consent for apps from verified publishers, for selected permissions
C) Do not allow user consent
D) Allow user consent only for apps registered in this tenant

<details>
<summary>Answer</summary>

**Correct: B**

This is Microsoft's recommended balanced setting: it restricts consent to verified publishers and low-impact permissions, reducing risk while preserving productivity.

**Why the others are wrong:**
- Allowing consent for all apps carries the highest risk and is not recommended
- Blocking all user consent forces every request into admin review, hurting productivity
- This option does not exist as a standard consent setting

</details>

---

**Q8.** What primarily distinguishes the trigger used in a Mover lifecycle workflow template from the trigger used in a Joiner template?

A) Mover uses employeeLeaveDateTime; Joiner uses employeeHireDate
B) Mover uses an attribute change trigger (e.g., department); Joiner uses employeeHireDate
C) Mover only supports on-demand execution; Joiner only supports scheduled execution
D) There is no difference; both use the same trigger type

<details>
<summary>Answer</summary>

**Correct: B**

Mover workflows are triggered by an attribute change, such as a department update, while Joiner workflows are triggered by employeeHireDate.

**Why the others are wrong:**
- employeeLeaveDateTime is the leaver trigger, not the mover trigger
- Both trigger types support on-demand execution; this isn't the distinguishing factor
- The trigger types are distinctly different between the two templates

</details>

---

