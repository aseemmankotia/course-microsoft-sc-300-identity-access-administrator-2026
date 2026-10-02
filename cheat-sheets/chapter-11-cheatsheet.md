## Chapter 11 Cheat Sheet — Exam Simulation & Time Management

### Exam Format Numbers
| Item | Value |
|---|---|
| Question count | ~40-60 |
| Total time | ~120 minutes |
| Case study share of time | ~20% |
| Case study share of questions | ~15% |
| Target pace, standalone question | ~2 min |
| Target pace, case study block | budget extra time for exhibit read, then ~1-1.5 min/question within it |

### SC-300 Domain Weights (official skills measured)
| Domain | Weight |
|---|---|
| Implement identities in Microsoft Entra ID | 25-30% |
| Implement authentication and access management | 25-30% |
| Implement access management for applications | 10-15% |
| Plan and implement identity governance | 25-30% |

### Case Study Handling
1. Skim all exhibits/tabs ONCE before answering any question in that set.
2. Answer every question for that case study using the shared context — do not reopen exhibits per question.
3. Flag only the questions you are unsure of; do not flag the whole case study.
4. Do not revisit a case study section after moving to the next section if the exam UI locks it — check whether navigation back is allowed before leaving.

### Domain Cue → Feature Signal Words
| Scenario phrase | Likely feature |
|---|---|
| "elevate to [admin role] for X hours", "approval to activate" | Privileged Identity Management |
| "catalog", "self-service request", "external/guest access to resources" | Entitlement Management access packages |
| "recertify", "periodic review", "still needs access?" | Access Reviews |
| "risk level", "impossible travel", "leaked credentials" | Identity Protection + Conditional Access risk policy |
| "block/require MFA at sign-in based on device/location/app" | Conditional Access policy |
| "auto-assign group by attribute" | Dynamic groups (no expiration) |

### Elimination Checklist
- Does the option satisfy **every** constraint stated (not just the general topic area)?
- Is the option real but designed for a **different actor** (privileged admin vs external guest vs end user)?
- Is the option real but **missing a required capability** (e.g., no expiration, no approval step)?
- Is the option deprecated or portal-legacy (e.g., per-user MFA vs Conditional Access)?

### Final Review (last 5-10 minutes)
1. Answer any fully blank question immediately — guess is better than zero.
2. Revisit flagged items in order of confidence (lowest confidence first).
3. Skip re-reading full case studies unless directly tied to a flagged question.
4. Submit only after all flags are cleared or time forces submission.
