## Chapter 6: Privileged Identity Management: Just-In-Time Role Activation — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | PIM: Eligible assignment vs Active assignment? | Eligible = must activate before permissions apply (MFA/justification/approval as configured). Active = permissions already in effect, no activation needed. Exam tip: activation requirements only apply to eligible assignments. |
| 2 | What is the configurable range for PIM role activation duration? | 1 to 24 hours, set per role in activation settings. Exam tip: exam scenarios often specify an exact max duration (e.g., 8 hours) — match it to the 'Activation maximum duration' setting. |
| 3 | License required to use Microsoft Entra PIM? | Microsoft Entra ID P2 or Microsoft Entra ID Governance. Exam tip: P1 does NOT include PIM. |
| 4 | PIM for Groups — what type of group qualifies? | Cloud-only Microsoft 365 or Security groups (not synced from on-premises AD). PIM manages eligible/active Member and Owner assignments separately. Exam tip: on-prem synced groups cannot be PIM-managed. |
| 5 | Microsoft's recommended number of standing Global Administrators? | Between 2 and 4. Exceeding this recommendation triggers the PIM alert 'There are too many global administrators'. |
| 6 | List the possible PIM role activation requirements. | Azure MFA, justification (free text), ticket/incident number, and approval by one or more designated approvers. Each is toggled independently per role. |
| 7 | PIM for Azure resource roles — what scopes can it target? | Management group, subscription, resource group, or individual resource. Exam tip: choose the narrowest scope that meets the requirement (least privilege). |
| 8 | Name the three main PIM alert categories. | 1) Roles are being assigned outside of PIM. 2) Roles aren't being used (eligible but never activated). 3) Duplicate role assignments (same role via multiple paths, e.g., direct + group). |
| 9 | What recurrence options exist for Access Reviews of privileged roles? | One-time, weekly, monthly, quarterly, or annually. Reviewer can be the resource owner, selected reviewers, or the assigned user themselves (self-review). |
| 10 | What happens if an activation request requiring approval is not approved in time? | The request expires (default 1 day) and the user must resubmit. Exam tip: expiration ≠ denial — the user can simply request activation again. |
| 11 | PIM for Microsoft Entra roles vs PIM for Azure resource roles — key distinction? | Entra roles = directory-wide admin roles (Global Admin, User Admin, Exchange Admin) managed in Entra ID. Azure resource roles = Azure RBAC roles (Owner, Contributor) scoped to Azure resources/subscriptions. Different settings blades, same PIM engine. |
| 12 | Can an eligible PIM assignment have a start and end date? | Yes — eligible (and active) assignments can be permanent or time-bound with explicit start/end dates. Exam tip: some organizations force time-bound-only assignments for highly privileged roles via role settings. |
