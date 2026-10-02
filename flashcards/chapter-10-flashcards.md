## Chapter 10: Lifecycle Workflows & Application Access Governance — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Lifecycle Workflows: default scheduled run interval? | Every 3 hours by default. Exam tip: on-demand execution bypasses this schedule for immediate testing or one-off runs. |
| 2 | Max number of Lifecycle Workflows per tenant? | 50. Exam tip: use execution condition scope rules to reuse fewer workflows across multiple populations instead of creating many. |
| 3 | Max tasks allowed in a single Lifecycle Workflow? | 25 tasks per workflow, combining built-in tasks and custom task extensions. |
| 4 | Admin consent workflow — default request expiration? | 30 days, configurable from 1–90 days. After expiration, the user must resubmit the consent request. |
| 5 | On-demand Lifecycle Workflow run — max users processed at once? | 100 users per on-demand execution. Useful for testing a workflow before enabling its schedule. |
| 6 | 'Allow user consent for apps from verified publishers, for selected permissions' vs 'Allow user consent for all apps' | Verified publisher option restricts consent to low-impact permissions from verified vendors — Microsoft's recommended default. 'All apps' imposes no restriction and carries the highest risk. |
| 7 | Which Lifecycle Workflow template disables an account immediately on termination instead of on the next scheduled run? | Real-time employee termination — triggers instantly off employeeLeaveDateTime, bypassing the standard 3-hour schedule. |
| 8 | What trigger type does the Mover lifecycle workflow template use? | An attribute change trigger (e.g., department attribute update) — not employeeHireDate or employeeLeaveDateTime. |
| 9 | How do you extend a Lifecycle Workflow to call an external system (e.g., HR API)? | Add a custom task extension that invokes an Azure Logic App, using an app registration granted the appropriate custom task extension permission. |
| 10 | Which product provides App Governance risky-permission detection for OAuth apps? | Microsoft Defender for Cloud Apps (App Governance capability) — separate from base Entra ID P2 licensing. |
| 11 | Who can approve admin consent requests by default? | Global Administrator, Cloud Application Administrator, or Application Administrator — or any user/group explicitly configured as a reviewer. |
| 12 | What makes up a Lifecycle Workflow's 'execution condition'? | Trigger (event, e.g., hire date) + Scope (rule-based attribute filter, e.g., department eq 'Sales'). A workflow only runs for users matching both. |
