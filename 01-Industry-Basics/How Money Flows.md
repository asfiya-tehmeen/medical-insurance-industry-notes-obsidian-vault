# How Money Flows

```
Employer / Gov / Individual --premium--> PAYER --claim payments--> PROVIDER
                                           |  \--rebates/fees--> PBM <--> Drug makers, Pharmacies
Member --copay/deductible--> PROVIDER      \--admin fees--> TPA/vendors, brokers commissions
```

## Payment models (how providers get paid)
- **Fee-for-service**: each service has a price. Encourages volume.
- **DRG / case rate**: hospital gets one fixed amount per stay type (Medicare inpatient uses MS-DRGs).
- **Per diem**: fixed per day in hospital.
- **Capitation**: fixed per member per month, whatever care is used.
- **Value-based / pay-for-performance**: bonuses for quality or cost savings (ACOs, bundled payments, shared savings).

## Fee schedules
Payer and provider contract prices per code. Medicare publishes the **Physician Fee Schedule** (RVU-based) and many commercial contracts are "% of Medicare".

## Medicare Advantage payments
CMS pays the plan a monthly **capitation** per member = base rate × **risk score** (HCC/RAF). Sicker members → higher payment. This creates incentives to document diagnoses thoroughly (and the compliance risk of over-coding, a major audit area; see [[Risk Adjustment]]).

## Reserves and IBNR
Claims arrive weeks/months after service. Insurers estimate **IBNR** (incurred but not reported) so financials aren't misleading. Actuaries use *claims lag triangles*. Data folks build the completion-factor tables.

## Reinsurance / stop-loss
Insurance for the insurer (or self-funded employer) against huge claims (e.g., > $500k per person). Needs accurate large-claimant reporting.

## Drug money (PBM)
Drug maker sets list price → PBM negotiates rebates for formulary placement → pharmacy paid by PBM/plan → member pays copay. Spread pricing and rebates are controversial and regulated more each year.

## Resources
- KFF employer survey: https://www.kff.org/health-costs/
- CMS Physician Fee Schedule: https://www.cms.gov/medicare/payment/fee-schedules/physician
- CMS payment systems: https://www.cms.gov/medicare/payment/prospective-payment-systems
