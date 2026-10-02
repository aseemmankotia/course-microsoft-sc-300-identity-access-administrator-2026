## Chapter 1: Microsoft Entra Tenant, Users, Groups & Administrative Units — Practice Questions

**Q1.** A company has 50,000 users. The security team wants a dynamic group that automatically contains all users whose department attribute equals 'Finance' AND whose country attribute equals 'US'. Which rule should be used?

A) (user.department -eq "Finance") -and (user.country -eq "US")
B) (user.department -eq "Finance") -or (user.country -eq "US")
C) (user.department -eq "Finance") and (user.country -eq "US")
D) (user.Department -contains "Finance") -and (user.Country -contains "US")

<details>
<summary>Answer</summary>

**Correct: A**

-and is the correct logical operator syntax, and -eq is correct for single-valued string attributes.

**Why the others are wrong:**
- -or returns users matching either condition, not both — includes users outside Finance/US.
- Lowercase 'and' is not valid dynamic rule syntax; operators must be prefixed with a dash (-and, -or).
- -contains is intended for multi-valued properties (e.g., proxyAddresses); for a single-valued string attribute like department, -eq is the supported operator.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** Contoso delegates helpdesk staff to manage only users located in the 'Sales-EMEA' region. What is the BEST way to grant this without tenant-wide access?

A) Assign Helpdesk Administrator at directory (tenant) scope
B) Create a custom role at tenant scope with restricted permissions
C) Add the helpdesk staff as owners of the Sales-EMEA security group
D) Assign Helpdesk Administrator scoped to the Sales-EMEA administrative unit

<details>
<summary>Answer</summary>

**Correct: D**

Administrative unit scoping lets you assign a built-in or custom role limited to only the users/devices/groups contained in that AU.

**Why the others are wrong:**
- Tenant-wide assignment gives access to all users, violating the least-privilege requirement.
- A custom role at tenant scope still applies directory-wide regardless of permission set — scope, not permission granularity, is the issue.
- Group ownership only grants control over group membership, not directory-wide helpdesk actions like password resets for those users.

</details>

---

**Q3.** Contoso assigns Microsoft 365 E5 via group-based licensing to the 'AllEmployees' dynamic group. Several users show licensing errors because they already have a directly assigned Exchange Online Kiosk license, which conflicts with the Exchange Online Plan 2 included in E5. What should the admin do WITHOUT removing group-based licensing?

A) Wait 24 hours — the conflict resolves automatically
B) Delete and recreate the AllEmployees group
C) Convert AllEmployees into a Microsoft 365 group
D) Manually disable the conflicting service plan or remove the directly assigned conflicting license for those users

<details>
<summary>Answer</summary>

**Correct: D**

Group-based licensing never auto-resolves service plan conflicts; an admin must manually disable a conflicting plan or remove the duplicate direct assignment.

**Why the others are wrong:**
- There is no automatic resolution timer — the error persists until manually fixed.
- Recreating the group does not remove the conflicting direct license assignments on the users.
- Group type (security vs M365) has no effect on service plan conflicts.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** Which group type should be used to provide a shared mailbox, SharePoint site, and Planner for collaboration, while still being usable as a Conditional Access assignment target?

A) Distribution group
B) Microsoft 365 group
C) Mail-enabled security group
D) Security group

<details>
<summary>Answer</summary>

**Correct: B**

Microsoft 365 groups provide collaboration workloads (mailbox, SharePoint, Planner, Teams) and can also be targeted in Conditional Access policies.

**Why the others are wrong:**
- Distribution groups only route email; they have no Conditional Access support and no collaboration workspace.
- Mail-enabled security groups provide email distribution and security assignment but not a shared mailbox/SharePoint/Planner workspace.
- Security groups support Conditional Access but do not provide mailbox/SharePoint/Planner collaboration features.

</details>

---

**Q5.** You need to automatically assign Microsoft Entra ID P2 licenses to all users in the Finance department, with no manual intervention as users join or leave. Which approach fits?

A) Group-based licensing assigned to a dynamic group with rule (user.department -eq "Finance")
B) Direct license assignment via bulk CSV import
C) Group-based licensing assigned to a static (assigned) security group
D) A monthly PowerShell script run through Azure Automation

<details>
<summary>Answer</summary>

**Correct: A**

A dynamic group automatically adds/removes members as the department attribute changes, and group-based licensing keeps license assignment in sync without manual work.

**Why the others are wrong:**
- Bulk CSV import is a one-time manual action, not automatic on department change.
- A static group requires manual membership updates whenever users join or leave Finance.
- A scheduled script is manual maintenance overhead and not a native automatic mechanism.

</details>

---

**Q6.** You need a dynamic membership rule that includes only guest users. Which rule is correct?

A) (user.accountEnabled -eq "Guest")
B) (user.userType -eq "Guest")
C) (user.userPrincipalName -contains "#EXT#")
D) (user.mail -contains "guest")

<details>
<summary>Answer</summary>

**Correct: B**

userType is the supported attribute for distinguishing Member vs Guest accounts in dynamic membership rules.

**Why the others are wrong:**
- accountEnabled is a boolean for enabled/disabled state, not user type.
- Parsing #EXT# in the UPN is unreliable and not the supported/recommended method, even though guest UPNs often contain it.
- Filtering on the word 'guest' in an email address is unreliable and not a supported dynamic rule pattern.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** An administrator adds the custom domain contoso.com to the tenant. Which DNS record type does Microsoft Entra ID require to complete domain verification?

A) CNAME record
B) TXT record (or MX record)
C) A record
D) SRV record

<details>
<summary>Answer</summary>

**Correct: B**

Microsoft Entra ID verifies custom domain ownership using a TXT record (preferred) or an MX record added at the domain registrar.

**Why the others are wrong:**
- CNAME records are not used for Entra ID domain ownership verification.
- A records map hostnames to IP addresses and are unrelated to domain verification.
- SRV records are used for service discovery (e.g., Skype/Teams), not domain verification.

</details>

---

**Q8.** What is the primary difference between a built-in directory role and a custom role in Microsoft Entra ID?

A) Built-in roles can be scoped to administrative units, custom roles cannot
B) Custom roles require a Microsoft Entra ID P1 or P2 license, built-in roles do not
C) Built-in roles cannot be assigned to groups, only custom roles can
D) Custom roles are limited to read-only permissions

<details>
<summary>Answer</summary>

**Correct: B**

Creating and assigning custom roles requires a Microsoft Entra ID P1 or P2 license; built-in roles are available at no additional license cost.

**Why the others are wrong:**
- Both built-in AND custom roles can be scoped to an administrative unit — this is not exclusive to either.
- Both role types can, where supported, be assigned via eligible/active assignments including through PIM groups.
- Custom roles can include write/management permissions, not just read-only.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

