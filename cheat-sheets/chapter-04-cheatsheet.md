## Chapter 4 Cheat Sheet: Conditional Access

### Policy Evaluation Logic
| Scope | Logic |
|---|---|
| Multiple applicable policies | **AND** — all must be satisfied, no priority ordering |
| Grant controls: 'Require one of' | **OR** — any one control satisfies |
| Grant controls: 'Require all' | **AND** — every control required |

### Assignments
- Users/groups, cloud apps (or user actions), **workload identities** (service principals, requires **P2**)
- Can include/exclude — exclusions always override inclusions

### Conditions
| Condition | License |
|---|---|
| Sign-in risk / User risk | **P2** (Identity Protection) |
| Device platform | P1 |
| Location (named locations) | P1 |
| Client apps | P1 |

### Grant Controls (block/allow gate)
- Require MFA
- Require device marked as **compliant** (Intune)
- Require **hybrid Azure AD joined** device
- Require approved client app / app protection policy
- Require password change / Terms of Use

### Session Controls (post-access experience)
- **Sign-in frequency** — periodic reauth (hours/days)
- **Persistent browser session** — Always / Never persistent
- **App-enforced restrictions** — only for apps that support it (SharePoint, Exchange Online)
- Conditional Access App Control (via Defender for Cloud Apps)

### Named Locations
- Mark IP ranges as **trusted**
- Country/region-based via GPS or IP lookup
- Limit: **195 named locations**, up to **195 IP ranges each** per tenant

### Report-Only Mode
- Evaluates policy, does NOT enforce
- Logs: Sign-in logs > **Conditional Access tab** > Report-only Success/Failure
- Use before flipping policy state to **On**

### What If Tool
- Location: Conditional Access > **What If**
- Simulates policies for ONE user + condition set
- Troubleshooting tool — not bulk analysis (use Report-only + sign-in logs for that)

### Common Exam Traps
1. Assuming CA policies have priority — they don't; all applicable = AND.
2. Confusing 'Require one of' (OR) with 'Require all' (AND) in grant controls.
3. Thinking What If replaces Report-only mode for rollout testing — it doesn't, it's single-scenario only.
4. Forgetting sign-in/user risk conditions need **P2**, not P1.
5. Confusing hybrid Azure AD join (on-prem sync) with Intune compliance (device management).
