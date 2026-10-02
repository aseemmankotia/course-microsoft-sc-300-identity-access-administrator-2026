# Answer Key — Practice Test 1

**Q1. Correct: C**

Administrative units let you scope Microsoft Entra role assignments (such as Helpdesk Administrator or User Administrator) to a defined subset of users, groups, or devices, restricting an admin's permissions to only members of that AU.

---

**Q2. Correct: B**

Microsoft Entra B2B collaboration is designed for inviting external business partners as guest users who authenticate with their own organization's existing identity, giving them access to internal resources without the resource tenant creating or managing full accounts for them.

---

**Q3. Correct: B**

The default Microsoft Entra Connect sync cycle runs every 30 minutes; this scheduler value is directly tested on the exam and can be changed with Set-ADSyncScheduler if a different interval is required.

---

**Q4. Correct: C**

Password hash synchronization requires no additional on-premises authentication agents beyond the Microsoft Entra Connect server itself, fully supports Conditional Access, and is the only hybrid method that enables cloud-side leaked credential detection because password hashes are stored (in secured hashed form) in Microsoft Entra ID.

---

**Q5. Correct: C**

Cloud sync relies on lightweight, easily deployed provisioning agents rather than the full Microsoft Entra Connect sync engine, is configured and managed from the cloud admin center, and natively supports multi-forest scenarios more simply than the classic sync engine.

---

**Q6. Correct: A**

In Exchange hybrid deployments, users whose mailboxes still reside on-premises can encounter Exchange Online service plan license errors because their synchronized Exchange-related attributes (such as recipient type and proxy addresses) are still pointed at the on-premises mailbox, preventing the cloud service plan from provisioning correctly until the mailbox is migrated to Exchange Online.

---

**Q7. Correct: D**

Administrative units let you scope directory roles like User Administrator to a defined subset of users or groups, so a role assignment scoped to an administrative unit only grants rights over members of that unit, not the whole tenant.

---

**Q8. Correct: D**

Microsoft Entra B2B collaboration lets external users authenticate with their home organization's Microsoft Entra credentials and be invited as guest users in the resource tenant, requiring no separate password management by the host company.

---

**Q9. Correct: C**

Pass-through Authentication validates every sign-in in real time directly against on-premises Active Directory, so a disabled AD account is immediately blocked from cloud sign-in without depending on any Entra Connect sync cycle.

---

**Q10. Correct: B**

Group-based licensing allows a user to be assigned multiple licenses from different groups simultaneously as long as there is no direct service plan conflict (such as two mutually exclusive plans that cannot coexist); here the E3 and E5 licenses can both apply since there's no overlapping conflicting plan.

---

**Q11. Correct: B**

FIDO2 security keys are portable external hardware credentials that are not bound to a single device, making them ideal for shared-kiosk scenarios where multiple workers need passwordless sign-in on the same shared workstation.

---

**Q12. Correct: A**

Sign-in frequency lets administrators force reauthentication after a specified time interval, and scoping the policy with a device filter condition allows it to apply only to unmanaged/non-compliant devices while compliant devices remain unaffected.

---

**Q13. Correct: B**

These four settings all live under the role's Activation tab in PIM role settings and together enforce MFA, an approval workflow, and mandatory justification text every time a user activates the eligible Global Administrator assignment.

---

**Q14. Correct: D**

Leaked credentials is classified as a user risk detection, an offline signal indicating the account's credentials were exposed. A user risk policy configured to require a secure password change at High risk directly remediates this specific detection type.

---

**Q15. Correct: B**

When the SSPR policy requires 2 methods to reset, a user must have at least two registered methods before SSPR is available. With only one method registered, the reset flow is blocked until the user completes registration of a second method, typically via combined registration or Security Info.

---

**Q16. Correct: D**

SharePoint Online and Exchange Online natively support app-enforced restrictions through Conditional Access. Enabling this session control delivers a 'limited access' web-only experience that blocks download, print, and sync for guests on unmanaged devices while still allowing browser-based collaboration.

---

**Q17. Correct: C**

PIM role settings (Activation tab) let you require justification, Azure AD MFA, and approval on activation for a specific role — exactly the controls described.

---

**Q18. Correct: C**

FIDO2 security keys are hardware tokens that any worker can tap or insert to authenticate on a shared device, without needing a personally enrolled device or smartphone.

---

**Q19. Correct: A**

Sign-in frequency forces users to re-authenticate after a specified time period (here, 4 hours), regardless of prior sign-in activity.

---

**Q20. Correct: A**

User risk policies in Identity Protection (or Conditional Access using the User risk condition) evaluate the user risk level and can require a secure password change as the remediation action for High risk.

---

**Q21. Correct: D**

The default SSPR policy requires users to register at least 2 authentication methods, and 2 methods are required at reset time by default (two-gate policy).

---

**Q22. Correct: A**

A Conditional Access policy using the 'client apps' condition scoped to legacy authentication clients, with a Block access grant control and the break-glass account excluded, is the supported way to selectively block legacy auth while keeping existing CA policies intact.

---

**Q23. Correct: B**

Federated credentials (workload identity federation) let GitHub Actions exchange its OIDC token for a Microsoft Entra access token, eliminating the need to store any secret or certificate.

---

**Q24. Correct: B**

User-assigned managed identities exist as standalone Azure resources independent of any VM's lifecycle and can be assigned to multiple resources simultaneously, which fits the sharing requirement.

---

**Q25. Correct: D**

A daemon with no signed-in user must use application permissions, which grant the app its own identity-based access; because there is no user to consent, an administrator must explicitly grant admin consent.

---

**Q26. Correct: C**

The app registration creates a global application object in its home tenant defining the app's identity, while a service principal is the local security principal created in each tenant that the application uses to access resources and be assigned permissions.

---

**Q27. Correct: B**

Managed identities and workload identity federation eliminate the credential entirely, removing the risk of expiration-related outages, which is the recommended best practice for workload identity credential management.

---

**Q28. Correct: C**

Applying Conditional Access policies to workload identities (service principals) requires a Microsoft Entra Workload ID Premium license.

---

**Q29. Correct: D**

Workload identity federation lets GitHub Actions exchange a short-lived OIDC token for an Entra ID access token, based on a federated identity credential configured on the app registration's service principal that specifies the trusted issuer, subject (repo/environment), and audience. No secret or certificate is ever stored in GitHub.

---

**Q30. Correct: B**

A system-assigned managed identity gives the Function App an automatically managed Azure AD identity with no credentials to store or rotate. Because there is no signed-in user, the workload must use an application (app-only) permission, which requires an administrator to grant admin consent before the Function can call Microsoft Graph.

---

**Q31. Correct: A**

Microsoft Entra ID enforces a limit of 20 federated identity credentials per application object. This is enough to support multiple external workload identity providers (e.g., GitHub Actions, Kubernetes service account issuers, Terraform Cloud) on the same app registration without needing separate app registrations for each.

---

**Q32. Correct: D**

The application object for a multi-tenant app exists only once, in its home (publisher) tenant — Contoso. When an admin in a resource tenant like Fabrikam consents, Microsoft Entra ID creates a service principal in Fabrikam's tenant. This service principal is the local, tenant-specific representation of the app and is where Fabrikam's consent grants, app role assignments, and conditional access scoping are applied.

---

**Q33. Correct: D**

Access packages in a catalog bundle multiple resource types (groups, Teams, SharePoint sites, apps) for self-service request, and entitlement management supports two-stage approval policies (e.g., owner then manager).

---

**Q34. Correct: A**

Lifecycle workflows can trigger on the employeeHireDate attribute and the built-in 'Onboard employee' template includes tasks like adding users to groups and sending a welcome email, fully automated.

---

**Q35. Correct: A**

'No change' is a valid fallback decision for non-responses, and with auto-apply enabled that decision is applied automatically when the review ends, requiring no manual action.

---

**Q36. Correct: A**

PIM eligible assignments combined with role activation settings (require MFA, require justification, set maximum activation duration) deliver just-in-time, zero-standing-access privileged role activation.

---

**Q37. Correct: C**

Terms of use gates access behind acceptance of a document (e.g., via Conditional Access), while access reviews periodically recertify whether existing assignments should remain.

---

**Q38. Correct: C**

Disabling user consent and enabling the admin consent workflow routes high-impact app requests to admins for review, while a built-in app consent policy (e.g., permitting verified publishers with low-impact permissions) still lets users self-consent to trusted low-risk apps.

---

**Q39. Correct: A**

Lifecycle workflows support attribute-based triggers (such as changes to employeeLeaveDateTime) and can execute Leaver tasks — disable account, remove from groups, revoke access — on a defined offset (e.g., 7 days after the attribute value), fully automating this exact scenario.

---

**Q40. Correct: D**

The admin consent workflow lets a user who is blocked from consenting submit a request; designated reviewers (who don't need Global Administrator) then approve or deny the specific permission grant directly from the My Access/admin consent requests portal, satisfying least-privilege app access governance.

---

**Q41. Correct: A**

PIM access reviews for Microsoft Entra roles support setting the non-response default decision to 'Remove access' and enabling 'Auto apply results to resource,' which together satisfy both requirements: automatic removal on non-response and automatic enforcement of the review outcome, on the quarterly recurrence.

---

**Q42. Correct: B**

Terms of use is enforced through a Conditional Access grant control that requires users to view and accept an uploaded PDF statement before sign-in completes, and it provides a per-user acceptance report along with options for expiration and mandatory reacceptance.

---

