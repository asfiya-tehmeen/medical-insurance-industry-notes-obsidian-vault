# Compliance and Domain Case Problems

Solve these on paper or in notes, then check your answer against [[HIPAA]], [[ACA and Other Key Laws]], [[Compliance Programs Audits and Reporting]].

## HIPAA / privacy scenarios
1. An analyst emails a spreadsheet with member names + diagnoses to a personal Gmail "to work from home". What's violated? What steps follow? (Answer: improper disclosure/likely breach; risk assessment; notify privacy officer; breach clock starts at discovery.)
2. Your vendor wants a claims extract for model training. What do you need? (BAA, minimum necessary, de-identification or limited data set + DUA, security review.)
3. Which of these are PHI? ZIP code alone / member ID + date of service / aggregated count of 3 members in a zip / de-identified file with year-only dates.
4. Design role-based access for: claims adjuster, data scientist, auditor, vendor.
5. A laptop with unencrypted PHI is stolen. Timeline and notifications?
6. Employee looked up their neighbor's claims. Violation? Controls to detect (access audit logs + anomaly alerts)?

## Audit / reporting scenarios
7. CMS asks for a "universe" of all pre-service appeals received Jan-Jun. Which fields and filters? What integrity checks before submitting?
8. Your MLR numbers differ by 0.4% between finance and data warehouse. How do you reconcile? (Definitions, cut-off dates, adjustments, IBNR, risk-adjustment transfers.)
9. A report was late because the eligibility file arrived 2 days late. Write the corrective action plan.
10. Prompt-pay: Find claims paid beyond 30 days by state; interest owed.

## Domain data scenarios
11. Retro-termination: 5,000 members termed backwards 3 months. Which claims are affected and what downstream tables must change?
12. A provider's NPI appears with 3 different TINs. Is that a data error? (Maybe not: providers can bill under multiple groups.)
13. Claims for a newborn arrive under the mother's ID. Explain and design handling.
14. COB: member has two plans; which is primary? (Birthday rule for kids; employer active worker before Medicare in many cases.)
15. Compute patient responsibility given the plan: deductible $500 (met $200), copay $30, coinsurance 20%, allowed $1,000.

## Fraud scenarios
16. A clinic bills 99215 for 90% of visits. Next steps? (Peer comparison, record review, pre-payment edits, SIU referral.)
17. Same member appears at 4 pharmacies, 5 prescribers for opioids in a month. Flag logic?

## Free external practice
- HHS HIPAA training slides/FAQ: https://www.hhs.gov/hipaa/for-professionals/faq/index.html
- HHS OCR resolution agreements (real cases to analyze): https://www.hhs.gov/hipaa/for-professionals/compliance-enforcement/agreements/index.html
- OIG enforcement actions: https://oig.hhs.gov/fraud/enforcement/
- HCCA free resources: https://www.hcca-info.org
- DOJ False Claims Act healthcare settlements: https://www.justice.gov/civil/false-claims-act
- NIST Cybersecurity Framework: https://www.nist.gov/cyberframework
