# HIPAA (Health Insurance Portability and Accountability Act, 1996)

The single most important law for a data person here. It has several "rules".

## 1. Privacy Rule
Controls how **PHI** can be used/disclosed.
- **Covered entities**: health plans, providers, clearinghouses. **Business associates (BAs)**: vendors handling PHI for them (you, if you work at a vendor!). Both need a **Business Associate Agreement (BAA)**.
- **PHI** = health info + any of 18 identifiers (name, address, dates, phone, SSN, MRN, member ID, IP, biometrics, photos...) tied to an individual. Applies to past, present, future health condition, care, or payment.
- **TPO**: Treatment, Payment, Healthcare Operations are permitted uses without authorization. Anything else (marketing, sale of PHI) generally needs written authorization.
- **Minimum necessary**: use only the data needed for the task. (Real-life analytics: don't pull SSNs if not needed.)
- **Patient rights**: access copy of records (30 days), amendment, accounting of disclosures, restrictions, confidential communications.
- **De-identification**: (a) **Safe Harbor**: remove all 18 identifiers; (b) **Expert Determination**. Limited data set with data use agreement allows dates/zip for research/operations.

## 2. Security Rule (electronic PHI, ePHI)
Required safeguards:
- **Administrative**: risk analysis (required!), workforce training, access management, incident procedures, contingency plan.
- **Physical**: facility access, workstation and device controls.
- **Technical**: unique user IDs, access controls (RBAC), audit logs, integrity checks, transmission security (TLS), encryption at rest ("addressable" but effectively expected), automatic logoff.
"Addressable" ≠ optional: implement or document an equivalent.

## 3. Breach Notification Rule
Unauthorized acquisition/use/disclosure of unsecured PHI = presumed breach unless a 4-factor risk assessment shows low probability of compromise. Notify individuals within 60 days; HHS (500+ people: within 60 days & media; fewer: annual); BAs notify the covered entity. Encrypted data is "secured" (safe harbor). Breach portal ("wall of shame"): https://ocrportal.hhs.gov/ocr/breach/

## 4. Transactions & Code Sets Rule
Mandates standard electronic formats (X12 5010, NCPDP, ICD-10, CPT) and operating rules. See [[X12 EDI Transactions]]. Also unique identifiers (NPI).

## 5. Enforcement
OCR investigates; civil penalties are tiered by culpability (currently up to ~$2M per violation category per year, adjusted annually); DOJ for criminal. State AGs can enforce too. Frequent findings: no risk analysis, lost unencrypted laptops, improper access by employees (snooping), late breach reports.

## Data-engineer checklist
- Inventory where PHI lands (raw, staging, marts, logs, notebooks, backups, test data).
- Encrypt at rest + in transit; manage keys centrally.
- Role-based access + column/row masking; least privilege.
- Audit logs retained (6 years documentation requirement).
- Never use real PHI in dev/test; use synthetic or masked data.
- Tokenize/hash IDs for analytics; separate re-identification keys.
- BAA with every cloud/SaaS vendor touching PHI (AWS, Azure, GCP, Snowflake, Databricks all offer BAAs).
- Retention and secure disposal policies.
- Incident runbook: who to call, timelines.

## Resources
- HHS HIPAA home: https://www.hhs.gov/hipaa/index.html
- Summary of Security Rule: https://www.hhs.gov/hipaa/for-professionals/security/index.html
- De-identification guidance: https://www.hhs.gov/hipaa/for-professionals/privacy/special-topics/de-identification/index.html
- NIST SP 800-66 (implementing Security Rule): https://csrc.nist.gov/publications/detail/sp/800-66/rev-2/final
