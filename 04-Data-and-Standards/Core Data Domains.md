# Core Data Domains (what data a payer holds)

| Domain | Contents | Grain (one row = ?) | Source |
|---|---|---|---|
| Member / Eligibility | demographics, coverage spans | member x coverage period | 834 files, enrollment system |
| Provider | NPI, specialties, locations, networks, contracts | provider x location x network | credentialing, directories, NPPES |
| Medical claims | header + lines + diagnoses | claim line | 837 via clearinghouse |
| Pharmacy claims | fills | fill | PBM / NCPDP |
| Lab results | test, value | result | labs (LOINC codes) |
| Authorizations | PA requests, decisions | auth | UM system / 278 |
| Care management | cases, assessments, outreach | case / contact | CM platform |
| Risk & Quality | HCCs, HEDIS flags | member x measure x year | derived |
| Financial | premiums, payments, reserves | invoice / payment | finance |
| Appeals/Grievances/Calls | cases | case | CRM |
| Reference | ICD, CPT, NDC, DRG, place of service, revenue codes, taxonomy | code | standards bodies |

## Typical warehouse model
```
dim_member    dim_provider    dim_date    dim_diagnosis   dim_procedure   dim_plan
        \          |            |             |               |            /
                         fact_claim_line
                         fact_rx_claim        fact_enrollment_month (member-month)
```
**Member-month table** (one row per member per month enrolled) is the denominator for almost every metric (PMPM, utilization per 1,000). Build it early and correctly.

## Key data challenges
- Versions & adjustments of claims (reversals, replacements).
- Retro-eligibility changes.
- Run-out / lag: recent months look artificially cheap (incomplete claims).
- Member and provider identity resolution.
- Date semantics: service date vs received date vs paid date vs incurred month.
- Free-text/unstructured: clinical notes, PA letters, faxes (OCR/NLP).
- Multiple source systems with different code versions.
- PHI everywhere.

## Common key fields
member_id, subscriber_id, claim_id (+ line number + version), npi (rendering/billing/referring), tin, dx codes (principal vs secondary), procedure codes + modifiers, place of service, revenue code, DRG, admission/discharge dates, billed/allowed/paid/member_cost, claim_status, adjustment reason codes.

## Standard "unit" definitions to memorize
- Incurred date = service date. Paid date = when paid.
- Allowed = billed minus contractual write-off. Paid = allowed minus member liability (minus COB).
- Admissions per 1,000 = admissions ÷ member-months × 12,000.
