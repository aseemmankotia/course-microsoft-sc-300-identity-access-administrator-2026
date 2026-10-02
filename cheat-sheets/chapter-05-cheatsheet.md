# Entra ID Protection — Risk Detections & Risk Policies

## Risk Policy Types
| Policy | Scope | Trigger Example | Default Remediation |
|---|---|---|---|
| User risk policy | Account (persistent) | Leaked credentials, confirmed compromise | Require password change / Block |
| Sign-in risk policy | Single session | Anonymous IP, impossible travel | Require MFA / Block |

**Exam rule:** User risk → password change. Sign-in risk → MFA. Never swap these.

## Risk Levels
- Low, Medium, High, No risk detected
- Policies enforce at a *minimum* selected level (e.g., "Medium and above")

## Detection Classification
| Detection | Category | Evaluation |
|---|---|---|
| Leaked credentials | User risk | Offline |
| Azure AD threat intelligence | User risk | Offline |
| Anomalous user activity / mass access to sensitive files | User risk | Offline |
| Anonymous IP address | Sign-in risk | Real-time |
| Atypical travel (impossible travel) | Sign-in risk | Real-time/near real-time |
| Unfamiliar sign-in properties | Sign-in risk | Real-time |
| Malicious IP / suspicious browser | Sign-in risk | Offline |

## Remediation Requirements
| Remediation | Requires |
|---|---|
| Self-service password change | SSPR enabled |
| Self-service MFA satisfaction | Combined registration completed |
| Admin: Confirm compromised | Sets risk = High immediately |
| Admin: Dismiss risk | Closes detection, no forced action |
| Admin: Reset password | Immediate forced remediation of user risk |

## Licensing
| License | Capability |
|---|---|
| Entra ID Free | No Identity Protection |
| Entra ID P1 | Sign-in risk CONDITION in Conditional Access only (limited, real-time) |
| Entra ID P2 | Full risk detection catalog, User risk + Sign-in risk policies, investigation reports |

## Configuration Location (2026)
- **Current/recommended:** Conditional Access policy → Conditions → "User risk" / "Sign-in risk"
- **Legacy (being retired):** Identity Protection → "User risk policy" / "Sign-in risk policy" standalone blades
- Exam may still reference both; know that CA-based configuration is the direction Microsoft is moving toward.

## Investigation
- **Risky users** report: current user risk level, risk history, detections tied to account
- **Risky sign-ins** report: per-session risk level, detection type, location/device, remediated/dismissed status
- **Risk detections** report: raw detection list across both categories

## Common Exam Traps
1. Confusing password-change remediation (user risk) with MFA remediation (sign-in risk)
2. Assuming P1 gives full Identity Protection — it only gives a limited CA sign-in risk condition
3. Thinking 'Confirm compromised' only logs the event — it actually sets risk to High and can trigger enforcement immediately
4. Believing self-remediation works without SSPR/MFA registration prerequisites
