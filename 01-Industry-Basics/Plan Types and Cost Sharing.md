# Plan Types and Cost Sharing

## Plan types
| Type | Needs PCP referral? | Out-of-network covered? | Typical cost | Notes |
|---|---|---|---|---|
| **HMO** | Yes | Emergency only | Lower premium | Care coordinated by Primary Care Physician |
| **PPO** | No | Yes, at higher cost | Higher premium | Flexible |
| **EPO** | No | No (except emergency) | Middle | PPO-like but no OON |
| **POS** | Yes | Yes, costs more | Middle | Hybrid |
| **HDHP + HSA** | Varies | Varies | Low premium, high deductible | Pairs with tax-free Health Savings Account |

## ACA metal tiers (marketplace)
Plan pays on average: Bronze 60%, Silver 70%, Gold 80%, Platinum 90%. Higher metal = higher premium, lower out-of-pocket.

## Worked example: how cost sharing works
Plan: deductible $1,000, coinsurance 20%, OOP max $5,000. Hospital bill: allowed amount $10,000. Nothing paid yet this year.
1. Member pays deductible: $1,000. Remaining $9,000.
2. Coinsurance: member pays 20% × $9,000 = $1,800.
3. Member total = $2,800. Insurer pays $7,200.
4. Later claim: if member's total hits $5,000, insurer pays 100% after.

Same bill if provider is **out of network**: allowed amount may be lower than billed; provider can balance-bill (unless No Surprises Act applies, see [[No Surprises Act]]).

## Accumulators
Systems track running totals of each member's deductible and OOP spend ("accumulators"). Getting them wrong means wrong claim payments, a classic data/engineering bug source. Family plans have individual *and* family accumulators (embedded vs aggregate deductibles).

## Benefit design pieces
- Covered services & exclusions
- Tiered networks, tiered drugs
- Visit limits (e.g., 20 PT visits/year)
- Essential Health Benefits (ACA ten categories: ambulatory, ER, hospitalization, maternity, mental health, Rx, rehab, lab, preventive, pediatric)
- Preventive care = $0 cost-share under ACA

## Medicare in one table
| Part | Covers | Notes |
|---|---|---|
| A | Hospital | Mostly premium-free |
| B | Doctors, outpatient | Monthly premium |
| C (Medicare Advantage) | A+B (+usually D) through private insurer | Insurer paid per-member by CMS; risk adjusted |
| D | Prescription drugs | Private plans |
