# Risk Adjustment

## Why it exists
If payments were flat, insurers would try to enroll only healthy people. **Risk adjustment** pays more for sicker members and less for healthier, leveling the playing field.

## Models
- **CMS-HCC** (Medicare Advantage): diagnoses from the prior year map to **HCCs** (e.g., diabetes with complications, CHF), each with a coefficient; add demographic factors → **RAF score**. Average member ≈ 1.0. Payment ≈ base rate × RAF.
- **HHS-HCC** (ACA marketplace): similar, used for transfers between plans in a market.
- **RxHCC** (Part D), **CDPS+Rx** (Medicaid in many states).
- **Hierarchies**: if a member has both "diabetes with complications" and "diabetes without", only the more severe counts.

## Data flow
Providers submit claims/encounters with diagnoses → plan submits diagnoses to CMS (**EDS/RAPS**, now **encounter data**, MAO-004 reports) → CMS computes risk scores → payments. Plans also run **chart reviews** to find missed diagnoses (and to *delete* unsupported ones).

## Programs
- **Retrospective chart review** and **prospective in-home assessments** to capture conditions.
- **Gap closure**: nudging providers to document chronic conditions each year (conditions must be recaptured annually).

## Compliance: RADV audits
CMS audits whether submitted diagnoses are supported by the medical record (**Risk Adjustment Data Validation**). Unsupported codes → repayment. DOJ False Claims Act cases target upcoding (e.g., big settlements involving major MA plans). This is a premium area for compliance + data analytics.

## What data people do
- Build RAF calculators (map ICD-10 → HCC with CMS mapping tables).
- Detect conditions documented once but never re-captured (suspecting gaps) or suspicious spikes.
- Reconcile what the plan submitted vs what CMS accepted (MOR/MMR files).

## Resources
- CMS risk adjustment: https://www.cms.gov/medicare/payment/medicare-advantage-rates-statistics/risk-adjustment
- HHS-operated RA (ACA): https://www.cms.gov/marketplace/resources/data/risk-adjustment-data
- Mapping files: search "CMS-HCC midyear final ICD-10 mappings" on cms.gov
