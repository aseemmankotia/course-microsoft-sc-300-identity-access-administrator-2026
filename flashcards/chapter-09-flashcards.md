## Chapter 9: Entitlement Management & Access Reviews — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Max number of approval stages in an access package policy? | 2. Each stage can use different approvers (specific approvers, manager, sponsor) plus separate fallback/escalation approvers per stage. |
| 2 | Which resource types can be added to an access package catalog? | Cloud (not on-prem synced) Azure AD security groups, Microsoft 365 groups/Teams, SharePoint Online sites, and Azure AD enterprise applications. |
| 3 | How does a partner user with no directory account request access before a B2B invite? | Add the partner domain as a Connected Organization, then set the access package requestor scope to 'Users not in your directory' scoped to that org. |
| 4 | Access review recurrence options | One-time (no recurrence) or recurring: Weekly, Monthly, Quarterly, Semi-Annually, Annually. Instance duration must be ≤ the recurrence interval. |
| 5 | What does 'Auto apply results to resource' do? | Automatically enforces the review outcome at period end without an admin manually clicking 'Apply results.' Pair with the 'If reviewers don't respond' fallback setting. |
| 6 | Default behavior if auto-apply is OFF and reviewer never responds? | Access is NOT automatically removed — an admin must manually apply results in the portal. Classic exam trap. |
| 7 | Reviewer type options for an access review | Self-review, Manager, Group owners (for group membership reviews), or specific designated reviewers. |
| 8 | Terms of Use document format requirement | Must be a PDF. Optionally configure expiration (specific date or every N days) forcing re-acceptance, and enforce per-device consent. |
| 9 | Two types of connected organizations | Azure AD (Microsoft Entra) tenant-based, and 'other directory' (non-Azure AD, e.g., Google Workspace/other identity providers via B2B). |
| 10 | Catalog vs Access Package | Catalog = container grouping resources for reuse. Access Package = bundle of resources from one catalog plus one or more assignment policies (requestor scope, approval, lifecycle). |
| 11 | Assignment duration options in an access package policy | No expiration, expire on a specific date, or expire after a set number of days/hours. Expiring assignments can trigger notification emails before removal. |
| 12 | Access package requestor scope choices | 1) Specific users/groups 2) All members of your directory 3) All users (members + guests) incl. connected orgs 4) Users not in your directory, scoped to a specific connected organization. |
