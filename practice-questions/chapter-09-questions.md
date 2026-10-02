## Chapter 9: Entitlement Management & Access Reviews — Practice Questions

**Q1.** A consulting partner's employees do not yet have Azure AD guest accounts in your tenant, but you want them to be able to request an access package for a project workspace. What should you configure?

A) Bulk-invite every partner employee as a B2B guest before creating the access package
B) Create a dynamic security group based on the partner's email domain
C) Enable self-service group management for the resource group
D) Add the partner's domain as a connected organization and set the access package requestor scope to 'Users not in your directory' for that organization

<details>
<summary>Answer</summary>

**Correct: D**

Connected organizations let entitlement management recognize external users from a partner tenant (or non-Azure AD directory) so they can be targeted by requestor scope and request access even before a formal B2B invitation exists — the invite is created automatically on request.

**Why the others are wrong:**
- Bulk-inviting first works but is unnecessary extra admin overhead and doesn't scale — connected orgs exist precisely to avoid this step
- Dynamic groups require the users to already exist as objects in the directory, which external users don't yet have
- Self-service group management is unrelated to entitlement management access packages

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** Which resource type CANNOT be added directly to an access package catalog?

A) A cloud-only Azure AD security group
B) A Microsoft 365 group / Team
C) A SharePoint Online site
D) An on-premises Active Directory security group synced via Entra Connect

<details>
<summary>Answer</summary>

**Correct: D**

Entitlement management only supports cloud-managed resources: cloud security groups, Microsoft 365 groups/Teams, SharePoint Online sites, and Azure AD enterprise applications. On-premises synced groups are read-only from the cloud and cannot be added.

**Why the others are wrong:**
- Cloud security groups are a fully supported resource type
- M365 groups/Teams are a supported resource type
- SharePoint Online sites are a supported resource type

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** An admin wants a two-tier approval process: the requestor's manager approves first, then a resource owner approves. What is the maximum number of approval stages Entra ID access package policies support?

A) 1
B) 3
C) 2
D) Unlimited

<details>
<summary>Answer</summary>

**Correct: C**

Access package approval policies support a maximum of 2 sequential approval stages, each with its own approvers and optional fallback/escalation approvers.

**Why the others are wrong:**
- 1 stage would not allow the two-tier manager-then-owner scenario described
- 3 stages exceeds the supported maximum
- There is a fixed cap, not unlimited stages

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** You configure a quarterly access review for a group's guest members. You want guest access automatically removed at the end of the review period if the assigned reviewer never responds, without an admin manually applying results. Which two settings must you configure together?

A) Enable 'Auto apply results to resource' and set 'If reviewers don't respond' to No change
B) Enable 'Auto apply results to resource' and set 'If reviewers don't respond' to Remove access
C) Set recurrence to Annually and leave auto-apply disabled
D) Assign a Terms of Use policy to the group

<details>
<summary>Answer</summary>

**Correct: B**

Auto-apply removes the need for manual 'Apply results' action, and 'Remove access' as the non-response fallback ensures access is actually revoked, not left unchanged.

**Why the others are wrong:**
- 'No change' would leave the guest's access intact, contradicting the requirement
- Annual recurrence with auto-apply disabled still requires a manual admin action to enforce removal
- Terms of Use enforces acceptance of a document, it does not drive access review outcomes

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** A company needs guests to review their own continued need for access to a finance access package every 90 days. Which reviewer type satisfies this with the least configuration?

A) Manager of the guest user
B) Group owner
C) Self-review
D) A specific named administrator

<details>
<summary>Answer</summary>

**Correct: C**

Self-review lets the assigned user attest to their own need for continued access, which is the standard low-overhead option for guest access reviews since guests typically have no manager object in the tenant.

**Why the others are wrong:**
- Guest users frequently have no manager attribute populated, making manager review unreliable
- Group owner review is designed for reviewing group membership overall, not individualized guest attestation
- A named admin adds unnecessary manual workload compared to self-review

</details>

---

**Q6.** Which statement about access review recurrence and duration is correct?

A) Access reviews must always recur weekly regardless of resource type
B) Duration of each review instance can exceed the recurrence interval, causing overlapping reviews
C) A review can be one-time (non-recurring) or recurring (weekly, monthly, quarterly, semi-annually, or annually), and each instance's duration must be less than or equal to the recurrence interval
D) Recurrence settings only apply to access packages, not to groups or applications

<details>
<summary>Answer</summary>

**Correct: C**

Reviews can be one-time or set to recur at fixed intervals, and the platform enforces that instance duration cannot exceed the chosen interval so instances don't overlap.

**Why the others are wrong:**
- Weekly is only one of several supported intervals, not mandatory
- The platform blocks configuring a duration longer than the interval
- Recurrence applies to reviews on groups, applications, and access packages alike

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Which requirement applies to Terms of Use policies in Microsoft Entra ID Governance?

A) The terms of use document must be a Word (.docx) file
B) Terms of use can only be assigned to internal member accounts, never guests
C) The terms of use document must be uploaded as a PDF file
D) Terms of use policies cannot expire or require re-acceptance

<details>
<summary>Answer</summary>

**Correct: C**

Entra ID requires the terms of use content to be uploaded as a PDF document; it can optionally be configured to expire and force re-acceptance on a schedule or specific date, and per-device consent.

**Why the others are wrong:**
- .docx is not a supported format for the terms of use document
- Terms of use can and often are targeted specifically at guest/external users
- Expiration and forced re-acceptance are supported optional settings

</details>

---

**Q8.** What is the primary difference between a catalog and an access package in Entitlement Management?

A) A catalog is a container that groups resources (groups, Teams, apps, sites); an access package is a bundle of one or more resources from a catalog governed by policies
B) A catalog and an access package are interchangeable terms for the same object
C) A catalog defines approval policies while access packages only hold resources with no policies
D) Access packages can span multiple tenants, but catalogs are limited to a single tenant

<details>
<summary>Answer</summary>

**Correct: A**

Catalogs organize resources for reuse; access packages select specific resources from one catalog and attach one or more assignment policies defining requestor scope, approval, and lifecycle.

**Why the others are wrong:**
- They are distinct objects with different roles in the hierarchy
- Policies live on the access package, not the catalog
- Catalogs, not access packages, are the container concept — and cross-tenant behavior is governed by connected organizations, not this distinction

</details>

---

