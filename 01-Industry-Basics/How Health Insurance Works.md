# How Health Insurance Works

## The core idea: pooling risk
Medical costs are unpredictable. One person might cost $0 this year and $500,000 next. A big group, though, is predictable. So everyone pays a small amount into a pool, and the pool pays for whoever gets sick. The insurer runs the pool.

## The four parties (the "four-party model")
1. **Member** pays premiums, gets care.
2. **Provider** delivers care, sends bills.
3. **Payer** (insurer) collects premiums, pays claims, manages the network.
4. **Purchaser / Plan sponsor** (usually employer or government) chooses and funds the plan.

Add-ons: PBMs (drugs), clearinghouses (claim routing), brokers (sell plans), TPAs (administer), regulators (CMS, state DOIs).

## How an insurer makes money
- Revenue: premiums (or admin fees in ASO).
- Costs: medical claims (80-90%), admin, sales, taxes, margin.
- Profit = premiums - claims - admin. So **controlling claim cost and pricing correctly** are the whole game.
- ACA requires the **Medical Loss Ratio** to be at least 80% (individual/small group) or 85% (large group): insurers must spend that share of premiums on care or refund the difference.

## Who buys insurance (lines of business)
| Line | Who | Who pays | Regulator |
|---|---|---|---|
| Employer group (commercial) | Employees | Employer + employee | State DOI / DOL (ERISA) |
| Individual / ACA marketplace | Self-employed, uninsured | Person (often with subsidies) | State + CMS |
| Medicare Advantage | 65+/disabled | Government pays insurer a fixed amount | CMS |
| Medicaid managed care | Low income | State/federal pays insurer | State + CMS |
| Medicare Supplement (Medigap) | Medicare enrollees | Person | State |
| Part D (drugs) | Medicare enrollees | Gov + person | CMS |

## Fully insured vs self-funded
- **Fully insured**: employer pays premium; insurer carries risk. Regulated by states.
- **Self-funded (ASO)**: employer pays claims itself; insurer/TPA handles admin and often provides network. Regulated federally under ERISA. About 60%+ of covered workers are in self-funded plans, so lots of "insurer" data work is really administration for someone else's money.

## The member journey
Enroll → get ID card → find in-network doctor → visit → provider submits claim → insurer adjudicates → EOB sent → member pays share → (maybe) appeal.

## Why this matters for data jobs
Each arrow above creates a dataset: enrollment/eligibility, provider directory, claims, pharmacy claims, authorizations, appeals, payments. See [[Claims Lifecycle]] and [[Core Data Domains]].

## Resources
- KFF "Health Insurance 101": https://www.kff.org/health-policy-101-health-insurance/
- HealthCare.gov glossary: https://www.healthcare.gov/glossary/
- CMS National Health Expenditure data: https://www.cms.gov/data-research/statistics-trends-and-reports/national-health-expenditure-data
