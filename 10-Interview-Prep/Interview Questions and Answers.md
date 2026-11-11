# Interview Questions and Answers

## Domain
**Q: Walk me through a claim from visit to payment.** 
A: Provider codes the visit (ICD-10 dx, CPT procedures) and submits an 837 via clearinghouse. Payer validates format, matches member/provider, then adjudicates: eligibility, network status, benefits, prior auth, code edits (NCCI, medical necessity), pricing via contract/fee schedule to get allowed amount, then applies member cost share (deductible/copay/coinsurance) and COB. Result: pay/deny/pend. Payer sends 835 + EOB. Later: appeals, adjustments, recoveries. See [[Claims Lifecycle]].

**Q: What is PMPM and why use it?** Cost ÷ member months; normalizes for membership size so populations/time periods compare.

**Q: MLR?** Claims + quality spend ÷ premium; ACA minimum 80% (small/individual) 85% (large); rebates if below.

**Q: Difference between 834, 837, 835, 270/271?** Enrollment; claim; remittance; eligibility inquiry/response.

**Q: HMO vs PPO?** HMO: network-only (except emergencies), PCP gatekeeper, lower cost. PPO: flexible, out-of-network covered, higher cost.

**Q: Fully insured vs self-funded?** Who bears claim risk; ERISA vs state regulation.

**Q: What is risk adjustment and the compliance risk?** Pay by member health; HCCs from diagnoses; risk of upcoding → RADV audits, FCA liability.

**Q: What are HEDIS measures?** NCQA quality measures: denominator/numerator/exclusions, drive Star ratings.

**Q: Why do incomplete months look cheap?** Claims lag; need completion factors/IBNR.

## Compliance
**Q: What is PHI and who is covered?** Individually identifiable health info held by covered entities/BAs; 18 identifiers; electronic/paper/oral.

**Q: How would you secure a PHI data lake?** Encryption (KMS), private networking, SSO+MFA, RBAC + masking/row-level security, tokenization, audit logs, data classification, BAAs, minimum necessary, retention/disposal, monitoring/alerts, separate de-identified zone, test with synthetic data.

**Q: You found a misdirected file with PHI. What do you do?** Contain (recall/delete, confirm), report immediately to privacy officer (don't self-assess alone), document timeline, risk assessment (4 factors), notifications if required, root cause + corrective action.

**Q: Safe Harbor vs Expert Determination?** Remove 18 identifiers vs statistical expert certifies very small risk.

**Q: How do you prove a regulatory report is accurate?** Documented definitions, lineage, reconciliation to source, independent review, version-controlled code, reproducible runs, evidence package, sign-offs.

## Data engineering / SQL
**Q: Dedupe claim versions?** `row_number() over (partition by claim_id, line_no order by version desc)`.
**Q: Design an idempotent daily load.** Landing + file registry (hash), staging, MERGE on natural key, transaction, reconciliation, alerts.
**Q: How do you handle late-arriving claims?** Partition by load date, recompute trailing N months, keep as-of snapshots for reproducibility.
**Q: SCD2 for member coverage?** Effective/end dates, current flag, close old row and insert new in one transaction.
**Q: A dashboard shows PMPM doubled. Debug?** Check join fan-out, member-month denominator, duplicate loads, new line of business, retro adjustments, definition changes, data freshness.
**Q: How do you test data quality?** Row counts, uniqueness, nulls, referential integrity, ranges, anomaly/drift, freshness; automated in pipeline with alerts.
**Q: Batch vs streaming?** Batch for most claims/enrollment; streaming for eligibility checks, fraud scoring.

## Behavioral (STAR format: Situation, Task, Action, Result)
Prepare 5 stories: (1) found data error and fixed it, (2) disagreed with stakeholder, (3) tight deadline, (4) learned new thing fast (this industry!), (5) improved a process through automation. Quantify results.

## Questions to ask them
- Which lines of business and which core claims platform?
- How do you handle data quality ownership and regulatory reporting?
- What's the biggest compliance audit risk right now?
- How does the data team partner with compliance and actuarial?
- What does success look like in 6 months?
