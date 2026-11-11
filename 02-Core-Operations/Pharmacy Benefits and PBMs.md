# Pharmacy Benefits and PBMs

## What a PBM does
Pharmacy Benefit Manager = processor and negotiator for drug benefits: builds the pharmacy network, manages the **formulary**, adjudicates drug claims in real time (~seconds at the pharmacy counter), negotiates **rebates** with manufacturers, runs mail-order/specialty pharmacy.

## Real-time pharmacy claim (NCPDP standard, not X12)
Pharmacist enters Rx → NCPDP transaction to PBM → eligibility, formulary tier, DUR (drug-utilization review: interactions, duplicates), copay → response in seconds. 

## Key concepts
- **Formulary tiers**: Tier 1 generics (cheap) → Tier 4/5 specialty.
- **NDC**: 11-digit National Drug Code identifying drug, strength, package. Link to RxNorm for ingredient-level analysis: https://www.nlm.nih.gov/research/umls/rxnorm/
- **AWP/WAC/NADAC**: price benchmarks. NADAC is pharmacy acquisition cost: https://data.medicaid.gov
- **MAC lists**: max allowable cost for generics.
- **Rebates, spread pricing, DIR fees**: money flows that are politically hot.
- **Specialty drugs**: <2% of scripts, 50%+ of spend in many plans.
- **Medicare Part D**: phases (deductible, initial coverage, catastrophic; IRA caps out-of-pocket at $2,000 from 2025, indexed).
- **340B**, biosimilars, GLP-1 coverage debates.

## Medical vs pharmacy benefit
Injectables given in a doctor's office may be billed under the *medical* benefit (HCPCS J-codes) while pills are *pharmacy* benefit. Integrating the two is a classic analytics challenge.

## Data
`rx_claim` (ndc, fill_date, days_supply, qty, ingredient_cost, dispensing_fee, member_paid, plan_paid, prescriber_npi, pharmacy_ncpdp), `formulary`, `drug_reference`.
Metrics: generic dispensing rate (GDR), adherence (PDC ≥ 80%), cost per script, specialty trend.

## Public data
- CMS Part D prescribers: https://data.cms.gov/provider-summary-by-type-of-service/medicare-part-d-prescribers
- FDA NDC directory: https://www.fda.gov/drugs/drug-approvals-and-databases/national-drug-code-directory
