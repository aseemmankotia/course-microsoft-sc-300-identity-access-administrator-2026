## Chapter 11: Full SC-300 Exam Simulation & Time-Management Strategy — Practice Questions

**Q1.** With 8 minutes remaining on the SC-300 exam, you have 5 flagged questions unanswered: one case-study question and four standalone questions. What should you do first?

A) Reread the entire case study scenario to ensure accuracy on its question
B) Skip all remaining questions because case studies take too long
C) Answer the four standalone questions first since they need no scenario re-reading, then attempt the case study question with any remaining time
D) Select the same answer letter for all five questions to save time

<details>
<summary>Answer</summary>

**Correct: C**

Standalone questions can be answered quickly without re-reading a scenario, maximizing the number of scored attempts in limited time.

**Why the others are wrong:**
- Re-reading the full case study burns remaining time and may leave zero questions answered
- Leaving questions blank guarantees zero credit versus an educated guess
- Guessing without reading any question text removes even a chance-based advantage from eliminating obviously wrong options

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A company requires that external partner users lose access to a shared project's resources automatically 90 days after being added, unless a specific manager approves continued access. Which feature should you implement?

A) Conditional Access session controls
B) Privileged Identity Management eligible assignment
C) A dynamic group membership rule based on department attribute
D) Access reviews with a recurring review and a designated approver

<details>
<summary>Answer</summary>

**Correct: D**

Recurring access reviews with a defined reviewer enforce periodic recertification and automatic removal unless approved, matching every part of the requirement.

**Why the others are wrong:**
- Session controls govern in-session behavior (like blocking downloads), not access expiration
- PIM is designed for time-bound elevation of privileged admin roles, not general project resource access for external partners
- Dynamic group rules assign membership by attribute but have no native time-based expiration or approval mechanism

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A requirement states that users must be able to self-service request access to a bundle of resources through a catalog, with access automatically expiring after a set period. Which single Microsoft Entra feature satisfies ALL parts of this requirement?

A) Privileged Identity Management
B) Dynamic group membership rules
C) Entitlement management access packages
D) Conditional Access

<details>
<summary>Answer</summary>

**Correct: C**

Access packages combine a self-service request catalog with resource bundling and configurable assignment expiration in one feature.

**Why the others are wrong:**
- PIM handles just-in-time elevation of privileged administrative roles, not general self-service catalog requests for resources
- Dynamic groups auto-assign membership from attributes but have no self-service request workflow
- Conditional Access enforces access controls at sign-in; it does not provision or expire resource access

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** An organization wants to require MFA only when a sign-in is assessed as medium or high risk, without prompting MFA on every sign-in. Which feature should be configured?

A) Security defaults
B) PIM approval workflow
C) Conditional Access policy using a sign-in risk condition
D) Per-user MFA enabled in the legacy MFA portal

<details>
<summary>Answer</summary>

**Correct: C**

A Conditional Access policy with a sign-in risk condition enforces MFA only when the calculated risk level matches the configured threshold.

**Why the others are wrong:**
- Security defaults enforce MFA broadly for all users with no risk-based granularity
- PIM approval workflows govern privileged role activation, not general sign-in risk response
- Per-user (legacy) MFA always requires MFA for that user regardless of risk level

</details>

---

**Q5.** Which Microsoft Entra governance feature lets you require periodic recertification of a user's continued need for an application role assignment, with options for self-review or manager review?

A) Entitlement management access packages
B) Identity Protection
C) Access reviews
D) Conditional Access

<details>
<summary>Answer</summary>

**Correct: C**

Access reviews are purpose-built for recurring recertification of existing role, group, or app assignments with configurable reviewers.

**Why the others are wrong:**
- Access packages provision and bundle access initially; recertification is typically layered on via an associated access review, not the package feature itself
- Identity Protection evaluates risk signals, it does not manage recertification workflows
- Conditional Access enforces sign-in controls, not periodic assignment recertification

</details>

---

**Q6.** In Privileged Identity Management, what is the maximum value, in hours, an administrator can configure for the 'activation maximum duration' role setting?

A) 8
B) 12
C) 24
D) 72

<details>
<summary>Answer</summary>

**Correct: C**

PIM role settings allow the activation maximum duration to be configured up to 24 hours.

**Why the others are wrong:**
- 8 hours is a common default value, not the configurable maximum
- 12 hours is a plausible intermediate value but not the actual ceiling
- 72 hours exceeds the allowed configuration range for activation duration

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Given an SC-300 exam with roughly 50 questions in 120 minutes, where case studies consume about 20% of total time for about 15% of questions, approximately how many minutes should you budget per standalone (non-case-study) question to stay on pace?

A) ~2 minutes
B) ~1 minute
C) ~4 minutes
D) ~6 minutes

<details>
<summary>Answer</summary>

**Correct: A**

Roughly 96 of the 120 minutes remain for about 42-43 standalone questions after removing case-study time, which works out to about 2 minutes per question.

**Why the others are wrong:**
- 1 minute per question is too aggressive and leaves no buffer for flagged review
- 4 minutes per question would overrun the total available time before finishing all questions
- 6 minutes per question would make it impossible to complete the exam within 120 minutes

</details>

---

**Q8.** What is the primary difference between flagging a question for review and simply leaving it unanswered in a computer-based certification exam?

A) Flagged questions are automatically graded as correct
B) Flagging marks the question in the navigator for quick return while any currently selected answer is still recorded, whereas an unanswered question records no answer at all
C) Flagged questions are removed from scoring entirely
D) Flagging changes the point weight assigned to the question

<details>
<summary>Answer</summary>

**Correct: B**

Flagging is purely a navigation aid; it preserves whatever answer is currently selected so you can return to reconsider it, while an unanswered item has no selection recorded.

**Why the others are wrong:**
- Flagging has no effect on grading correctness
- Flagged questions remain fully scored, they are not excluded
- Flagging does not alter the scoring weight of a question

</details>

---

