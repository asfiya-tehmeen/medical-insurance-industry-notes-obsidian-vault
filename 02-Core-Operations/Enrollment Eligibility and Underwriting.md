# Enrollment, Eligibility, and Underwriting

## Enrollment
How a person (or group) gets onto a plan.
- **Open enrollment**: yearly window (ACA: Nov 1-Jan 15 on HealthCare.gov; Medicare: Oct 15-Dec 7; employers set their own).
- **Special enrollment (SEP)**: qualifying life events (marriage, birth, job loss, move).
- **Employer groups**: HR sends a roster; insurer loads it. Standard file: **X12 834** ([[X12 EDI Transactions]]).
- **Effective date / term date**: coverage start/end. Retro-terminations (coverage ended backwards in time) cause claims to be reversed; a frequent data headache.

## Eligibility
"Is this person covered **on this date of service** for this benefit?"
- Providers check with an **X12 270/271** eligibility inquiry/response (real time).
- Core data: member ID, subscriber ID, relationship, plan/product, effective & term dates, PCP assignment, COB info.
- Common issues: duplicate members (same person, two IDs), timing lags between employer and insurer, grace periods for ACA subsidized members (3 months: payer pays month 1, may pend months 2-3).

## Member identity
A **Master Member Index (MMI)** / MDM links records across systems with probabilistic matching (name, DOB, SSN last 4, address). Wrong matches = privacy breach; missed matches = fragmented history.

## Underwriting
Deciding who to cover and at what price.
- **Individual market (post-ACA)**: no denial for pre-existing conditions; rates vary only by age, tobacco, geography, family size.
- **Small group**: community rated (similar rules).
- **Large group / self-funded**: experience-rated; underwriters study past claims and demographics.
- **Medicare Advantage / Medicaid**: bids and rates with government.
- Tools: actuarial models, risk scores, manual underwriting for stop-loss.

## Premium billing
Invoicing groups/individuals, payments, grace periods, cancellations. Subsidy (APTC) reconciliation with CMS is monthly.

## Data tables you'll see
`member`, `member_coverage` (one row per coverage span), `group`, `product`, `plan`, `subscriber_dependent`, `premium_invoice`, `premium_payment`.

## Compliance hooks
Nondiscrimination, ACA rating rules, HIPAA special enrollment, COBRA continuation, MHPAEA parity, enrollment reconciliation with CMS (Medicare/Marketplace).

## Resources
- HealthCare.gov SEP: https://www.healthcare.gov/coverage-outside-open-enrollment/
- Medicare enrollment: https://www.medicare.gov/basics/get-started-with-medicare
- DOL COBRA: https://www.dol.gov/general/topic/health-plans/cobra
