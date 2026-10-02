# Answer Key — Practice Test 2

**Q1. Correct: B**

Staged Rollout lets admins enable cloud authentication features (PHS, PTA, Seamless SSO) for a specific security group of users while the domain remains federated for everyone else, providing a safe pilot before full cutover.

---

**Q2. Correct: A**

B2B direct connect establishes a mutual, two-way trust relationship between two Microsoft Entra tenants specifically for scenarios like Teams shared channels, and it does not create a guest object in either tenant's directory.

---

**Q3. Correct: B**

A restricted management administrative unit prevents even Global Administrators (unless explicitly assigned a role on that unit) from managing its members, while a scoped role assignment to Executive Support grants exactly the least-privilege management needed.

---

**Q4. Correct: C**

Password writeback requires enabling the writeback feature in Microsoft Entra Connect, a Microsoft Entra ID P1 (or P2) license for SSPR writeback, and SSPR itself configured and enabled for the relevant users.

---

**Q5. Correct: A**

Duplicate Attribute Resiliency (DAR) automatically detects duplicate proxyAddresses or userPrincipalName values and appends a temporary suffix to one of them, allowing sync to continue until an administrator corrects the source data in AD.

---

**Q6. Correct: D**

Group-based licensing allows admins to disable individual service plans within a group's license assignment via 'Assign options,' resolving the duplicate/conflicting plan while preserving the group memberships needed for other purposes.

---

**Q7. Correct: D**

Pass-through Authentication uses lightweight agents installed on-premises (Microsoft recommends at least 3 for high availability) that validate credentials in real time directly against Active Directory. Passwords are never stored or synced to Entra ID, and no AD FS infrastructure is required.

---

**Q8. Correct: C**

Restricted management administrative units block management of contained objects even for Global Administrators, unless the admin also holds a role explicitly scoped to that administrative unit, exactly matching the requirement.

---

**Q9. Correct: B**

Attribute-based (rule-based) filtering configured through the Synchronization Rules Editor lets an administrator exclude specific objects by evaluating attribute values (e.g., userAccountControl or a custom attribute), enabling exclusion of individual accounts that share an OU with accounts that must sync.

---

**Q10. Correct: C**

B2B direct connect establishes a mutual, two-way trust relationship between two Entra tenants specifically for scenarios like Teams shared channels, allowing external users to participate without a guest object being created in the local directory.

---

**Q11. Correct: D**

Eligible assignments require explicit activation (removing standing access). PIM role settings let you require approval by a specific approver, require Entra MFA at activation time, and cap the activation duration (e.g., 8 hours) — all four requirements map directly to PIM role activation settings, not Access Reviews or Conditional Access.

---

**Q12. Correct: C**

The built-in 'Phishing-resistant MFA' authentication strength only includes FIDO2 security keys, Windows Hello for Business, and certificate-based authentication (smart card) — none of which are vulnerable to phishing via SMS/voice/push interception, satisfying the requirement out of the box.

---

**Q13. Correct: B**

Best practice is to verify identity through an out-of-band channel (e.g., phone call to a known number, manager confirmation) before taking any remediation action, then have the user register authentication methods so they can complete the required secure password change, and only then dismiss the risk after confirming legitimate access — this avoids both a security bypass and a permanent lockout.

---

**Q14. Correct: A**

Hybrid Cloud Trust is the newest, simplest deployment model — it requires no on-premises PKI and no specific domain controller version, relying instead on Azure AD Kerberos for authentication against on-premises resources, making it ideal when minimizing infrastructure dependencies.

---

**Q15. Correct: C**

Microsoft Authenticator passwordless phone sign-in works on both iOS and Android without requiring any password entry or specialized hardware, making it the correct persistent passwordless method for mobile-only contractors.

---

**Q16. Correct: B**

CAE enables supported services to receive near real-time signals (critical events like account disable/password reset/high user risk, and some Conditional Access policy changes) and revoke or re-evaluate access immediately, rather than relying solely on the token's original lifetime — closing the gap between a revocation event and enforcement.

---

**Q17. Correct: A**

The role settings blade for an eligible role assignment in PIM lets an admin directly configure approval workflow, justification requirement, and maximum activation duration in one place, satisfying all three requirements.

---

**Q18. Correct: A**

User risk reflects the probability that a given identity has been compromised, such as through leaked credentials. Pairing the User risk condition with the "Require password change" grant control (and SSPR enabled) remediates this risk.

---

**Q19. Correct: D**

Temporary Access Pass (TAP) is a time-limited passcode designed for onboarding and recovery scenarios, allowing a user to sign in once and register passwordless methods such as Windows Hello for Business without an existing password.

---

**Q20. Correct: A**

The Persistent browser session control, when set to "Never persistent," forces reauthentication whenever a user closes and reopens the browser, regardless of remaining token lifetime.

---

**Q21. Correct: D**

Cloud Kerberos trust does not require line-of-sight to a domain controller during registration or day-to-day sign-in (only an Azure AD Connect Kerberos Server object sync is needed), making it ideal for branch offices with unreliable WAN links and no PKI.

---

**Q22. Correct: A**

Authentication strengths let administrators restrict which combination of authentication methods satisfies a Conditional Access policy, such as requiring only phishing-resistant methods, while the generic "Require MFA" grant accepts any method the user has registered, regardless of strength.

---

**Q23. Correct: D**

The subject claim 'repo:org/repo:ref:refs/heads/main' scopes the federated credential's trust to OIDC tokens issued specifically for pushes to the main branch, matching the requirement exactly.

---

**Q24. Correct: B**

Workload identity federation lets GitHub Actions exchange a short-lived OIDC token issued by GitHub for a Microsoft Entra access token, removing the need to store any secret or certificate in the pipeline at all.

---

**Q25. Correct: A**

Microsoft Entra Workload ID Premium is the dedicated add-on license that enables Identity Protection risk detections (e.g., leaked credentials, unusual sign-in properties) and Conditional Access policies scoped specifically to workload identities such as service principals and managed identities.

---

**Q26. Correct: A**

A user-assigned managed identity has a lifecycle independent of any single Azure resource. It is created once, can be assigned to multiple resources simultaneously, and continues to exist with its Key Vault access policy intact even if individual VMs are deleted.

---

**Q27. Correct: C**

Consenting to a multi-tenant application creates a service principal (shown as an Enterprise Application) in the consuming tenant. This service principal represents the app locally, holds the tenant-specific consent grants and assigned permissions, and is what Fabrikam administrators manage.

---

**Q28. Correct: B**

By default, Microsoft Entra ID allows all users to register applications ('Users can register applications' = Yes under User settings). Best practice for least privilege is to set this to 'No' and then explicitly assign the Application Developer role to the vetted users or group who need app registration rights.

---

**Q29. Correct: C**

For Kubernetes workload identity federation, the federated credential's subject claim must exactly match the 'sub' claim in the service account token, which Kubernetes formats as system:serviceaccount:<namespace>:<service_account_name>. A mismatch causes token validation to fail.

---

**Q30. Correct: B**

A user-assigned managed identity has a lifecycle independent of any specific resource. It is created once, assigned to the VMSS, and every instance shares the identical identity and object ID, giving consistent Key Vault access even as instances scale in and out.

---

**Q31. Correct: C**

Workload identity federation lets GitHub Actions present a short-lived OIDC token that Entra ID trusts based on issuer, subject, and audience matching — no client secret or certificate needs to be created, stored, or rotated in the pipeline.

---

**Q32. Correct: C**

Conditional Access for workload identities supports only Block access or Grant access as controls, and does not support MFA or device-based controls since service principals cannot perform interactive authentication. To restrict sign-in to only the approved location, the condition must target every location except the approved one and the control must Block access.

---

**Q33. Correct: B**

Separation of duties (SoD) checks in entitlement management let you designate an incompatible access package or group; the system automatically blocks a request if the requester already holds the conflicting access, enforced at request time with no manual review needed.

---

**Q34. Correct: A**

The 'Attribute changed' trigger type in Microsoft Entra ID Governance lifecycle workflows fires a workflow automatically as soon as a specified attribute (such as employeeType) changes on a user object, without needing a scheduled run.

---

**Q35. Correct: D**

The 'Auto apply results to resource' setting on an access review automatically implements the review outcome (e.g., removing a user whose access was denied or not reviewed) at the end of the review period, eliminating the need for manual application.

---

**Q36. Correct: A**

Terms of use policies include an 'Expire consents' option that forces users to re-accept the same terms after a defined number of days, meeting recurring re-acceptance requirements without needing to publish a new document version.

---

**Q37. Correct: D**

The recommended user consent setting, 'Allow user consent for apps from verified publishers, for selected permissions,' combined with permission classifications (marking specific permissions as low impact), lets users consent only to apps requesting those classified low-impact permissions while blocking consent for apps requesting anything else.

---

**Q38. Correct: B**

Entitlement management access package request policies support configuring up to two sequential approval stages, each with its own set of approvers (e.g., manager for stage one, resource owner for stage two), satisfying multi-level sequential approval.

---

**Q39. Correct: D**

Lifecycle Workflows support 'custom task extensions,' which let you call a Logic App at specific points in a workflow (e.g., after the leaver tasks) to perform actions not natively built into Lifecycle Workflows, such as updating an on-premises HR system.

---

**Q40. Correct: D**

Entitlement management supports defining incompatible access packages (or incompatible groups/roles) directly on an access package's policy. This enforces separation of duties by blocking a request if the user already has an assignment to the designated incompatible access package.

---

**Q41. Correct: B**

Enabling 'Auto apply results to resource' ensures the review's outcome is applied automatically without admin intervention, and setting the 'If reviewers don't respond' fallback to 'Remove access' guarantees that guests whose access isn't reviewed by the deadline are automatically removed from the group.

---

**Q42. Correct: C**

The admin consent workflow (found under Enterprise Applications > Consent and permissions > Admin consent settings) lets users submit a request for admin consent when they're blocked from consenting themselves, routes it to designated reviewers (a group or specific users), and can be configured to notify requesters of the reviewer's decision.

---

