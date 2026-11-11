# Claims Lifecycle (the heart of the industry)

## Big picture
```
Visit -> Provider codes it -> Claim built (837) -> Clearinghouse edits
 -> Payer receives -> Front-end edits (reject?) -> Adjudication engine
 -> Pay / Deny / Pend -> 835 remittance + EOB -> Provider posts payment
 -> Member bill -> Appeals / Reprocessing / Recoveries
```

## Steps in detail
1. **Service**: member sees provider. Provider records diagnoses (ICD-10) and procedures (CPT/HCPCS).
2. **Claim creation**: professional claim (CMS-1500 / 837P) or institutional (UB-04 / 837I) or dental (837D).
3. **Clearinghouse scrub**: syntax and basic edits. 999/277CA acknowledgements come back.
4. **Intake at payer**: file loaded, duplicates checked, member and provider matched.
5. **Adjudication** (automated rules, ~80-90% auto-adjudicated):
   - Eligibility on date of service?
   - Provider contracted/in-network? Credentialed?
   - Benefit covered? Limits reached?
   - Prior auth required and present? ([[Utilization Management and Prior Auth]])
   - Code edits: valid ICD/CPT combos, modifiers, bundling (NCCI), medical necessity, duplicate, age/gender
   - Pricing: apply contract/fee schedule to get **allowed amount**
   - Member liability: deductible, copay, coinsurance, accumulators
   - COB: other insurance primary?
6. **Outcome**: **Paid**, **Denied** (with reason codes CARC/RARC), **Pended** (manual review), **Adjusted**.
7. **Payment & remittance**: electronic funds transfer + **835 ERA**; member gets **EOB**.
8. **Post-payment**: appeals, corrections (replacement/void claims, frequency code 7/8), overpayment recovery, audits, subrogation.

## Claim line vs header
A claim has one **header** (patient, provider, totals, diagnoses) and many **service lines** (each procedure with date, units, charge). Payment is decided at line level. Many analytics bugs come from joining header and lines carelessly and double counting dollars.

## Statuses
Received → In process → Pended → Finalized (paid/denied) → Adjusted/Reversed → Appealed.

## Key concepts
- **Clean claim rate**, **auto-adjudication rate**, **turnaround time** (prompt-pay laws set deadlines, often 30-45 days).
- **Denial reasons**: eligibility, no auth, not covered, duplicate, timely filing, coordination of benefits, medical necessity.
- **Timely filing**: provider must submit within window (e.g., 90-180 days).
- **Adjustments**: later changes create new records with reversed + new amounts, so a "claim" can have many versions. Always reason about **latest version** vs **all versions**.
- **Encounter data**: claim-like records for capitated services or from managed-care plans reported to the state/CMS.

## Common data tables
`claim_header`, `claim_line`, `claim_diagnosis`, `claim_adjustment`, `claim_status_history`, `payment`, `remittance`, `denial_reason`, `provider`, `member`.

## Example mini-claim (professional)
| Field | Value |
|---|---|
| Member | M123 |
| Provider NPI | 1234567893 |
| Dx | E11.9 (type 2 diabetes) |
| Line 1 | CPT 99213 (office visit), billed $200 |
| Allowed | $90 |
| Copay | $25 |
| Plan paid | $65 |
| Write-off by provider (contractual adj) | $110 |

## Resources
- CMS claims processing manual: https://www.cms.gov/medicare/regulations-guidance/manuals/internet-only-manuals-ioms
- CMS NCCI edits: https://www.cms.gov/medicare/coding-billing/national-correct-coding-initiative-ncci-edits
- X12 code lists (CARC/RARC): https://x12.org/codes
