## Chapter 4: Conditional Access: Assignments, Conditions & Controls — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | CA policy evaluation logic when multiple policies apply? | All applicable policies must be satisfied — AND logic across policies. Exam tip: there is no priority ordering between CA policies. |
| 2 | Grant control 'Require one of the selected controls' vs 'Require all the selected controls'? | 'Require one of' = OR logic (any single control satisfies). 'Require all' = AND logic (every listed control must be satisfied). |
| 3 | Report-only mode purpose? | Evaluates the policy without enforcing grant/block. Results log as 'Report-only: Success/Failure' under Sign-in logs > Conditional Access tab. Use before setting a policy to On. |
| 4 | What If tool — where and what does it do? | Azure AD > Conditional Access > What If. Simulates which policies apply for one specific user/app/condition combination — a troubleshooting tool, not a bulk-impact simulator. |
| 5 | Which CA conditions require Azure AD Premium P2? | Sign-in risk and user risk conditions (Identity Protection). Device platform, client apps, and location conditions are P1. |
| 6 | How to mark a named location as trusted? | Conditional Access > Named locations > New IP location > check 'Mark as trusted location'. Trusted locations can be excluded from MFA policies or lower risk scoring. |
| 7 | Named location limits per tenant? | Up to 195 named locations, each with up to 195 IP ranges. Exam occasionally tests this exact number. |
| 8 | Sign-in frequency session control purpose? | Forces periodic reauthentication at a set interval (e.g., every 4 hours) regardless of an otherwise-valid token — reduces the risk window for a compromised session. |
| 9 | Persistent browser session options? | 'Always persistent' (session survives browser close) or 'Never persistent' (session ends on browser close). Independent from sign-in frequency setting. |
| 10 | Require hybrid Azure AD joined device vs Require compliant device? | Hybrid join = device joined to on-prem AD + synced to Azure AD via Azure AD Connect. Compliant device = evaluated against Intune compliance policy. Different data sources, both are grant controls. |
| 11 | Conditional Access for workload identities — requirements? | Targets service principals; requires Azure AD Premium P2. Supports location and multifactor-style conditions but not sign-in risk (as of GA). |
| 12 | App-enforced restrictions example? | Passes device signal to the app itself (e.g., SharePoint Online, Exchange Online) to allow a limited or full session — only works with apps that natively support this session control. |
