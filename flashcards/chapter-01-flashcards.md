## Chapter 1: Microsoft Entra Tenant, Users, Groups & Administrative Units — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Max character length of a dynamic group membership rule? | 3,072 characters. Exam tip: overly complex nested conditions can hit this limit — simplify using nested/helper groups. |
| 2 | Max number of owners allowed per group in Microsoft Entra ID? | 100 owners. Exam tip: member count limit is far larger — owners is the constrained number the exam tests. |
| 3 | Which license is required to use dynamic groups or custom roles? | Microsoft Entra ID P1 (or P2). Exam tip: Free tier cannot create dynamic membership rules or custom roles. |
| 4 | Can mail-enabled security groups be used for group-based licensing? | No. Only security groups and Microsoft 365 groups support group-based licensing — distribution and mail-enabled security groups are excluded. |
| 5 | Security group vs Microsoft 365 group — which gives a shared mailbox, SharePoint site, and Planner? | Microsoft 365 group. Security groups only manage access/permissions, not collaboration workloads. |
| 6 | Dynamic rule to include only guest users? | (user.userType -eq "Guest"). Exam tip: don't rely on parsing #EXT# in the UPN — userType is the supported attribute. |
| 7 | Dynamic rule operator for exact match on a single-valued string attribute (e.g., department)? | -eq. Exam tip: -contains is for multi-valued properties like proxyAddresses or otherMails, not simple strings. |
| 8 | DNS record type(s) accepted to verify a custom domain in Microsoft Entra ID? | TXT record (preferred) or MX record. Exam tip: CNAME is NOT a supported verification method. |
| 9 | What happens when group-based licensing assigns two conflicting service plans (e.g., Exchange Online Plan + Kiosk)? | A licensing error appears; the admin must manually disable one conflicting plan or remove the duplicate license. There is no auto-resolution. |
| 10 | How do you delegate a role to manage only users in one region without tenant-wide access? | Assign the role (built-in or custom) scoped to an Administrative Unit containing only those users. Scoping restricts reach, not permissions. |
| 11 | Member user vs Guest user — default access difference? | Guests get restricted default directory permissions (can't enumerate users/groups by default); Members get full default access. Controlled via External collaboration settings. |
| 12 | Can both built-in AND custom roles be scoped to an Administrative Unit? | Yes — AU scoping applies to both built-in and custom roles. Exam tip: commonly missed — it's not exclusive to custom roles. |
