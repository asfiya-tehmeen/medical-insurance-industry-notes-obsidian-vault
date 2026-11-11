# Medical Code Sets

Code sets are dictionaries so everyone describes care the same way.

| Code set | What it describes | Owner | Example |
|---|---|---|---|
| **ICD-10-CM** | Diagnoses ("what's wrong") | CDC/WHO | E11.9 Type 2 diabetes w/o complications; I10 hypertension |
| **ICD-10-PCS** | Inpatient hospital procedures | CMS | 0FT44ZZ |
| **CPT** | Physician procedures/services | AMA (licensed, paid) | 99213 office visit; 93000 EKG |
| **HCPCS Level II** | Supplies, drugs, DME, ambulance | CMS | J1745 infliximab; E0601 CPAP |
| **Modifiers** | Tweak a procedure code | | -25 separate E/M, -59 distinct service, -LT/RT |
| **NDC** | Drug products | FDA | 11 digits |
| **RxNorm** | Normalized drug names/ingredients | NLM | |
| **LOINC** | Lab tests and observations | Regenstrief | 4548-4 HbA1c |
| **SNOMED CT** | Clinical concepts (EHR) | SNOMED Intl | |
| **DRG (MS-DRG, APR-DRG)** | Inpatient stay grouping for payment | CMS / 3M | 470 joint replacement |
| **Revenue codes** | Hospital billing categories | NUBC | 0450 ER |
| **Place of Service (POS)** | Where service happened | CMS | 11 office, 21 inpatient, 23 ER |
| **Type of Bill** | Institutional claim type | NUBC | 111 inpatient |
| **Taxonomy codes** | Provider specialty | NUCC | 207Q00000X Family Med |
| **CARC/RARC** | Why claim adjusted/denied | X12 | CARC 45 charge exceeds fee schedule; 50 not medically necessary; 96 non-covered |
| **NPI** | Provider ID (10 digits, Luhn check) | CMS | |

## ICD-10 structure
`E11.65` -> category E11 (type 2 diabetes mellitus), `.65` = with hyperglycemia. Up to 7 chars. About 70,000+ diagnosis codes; updated every Oct 1. CPT updates Jan 1. Always join codes using **effective dates** because codes are added/retired yearly.

## Why it matters
- Payment is driven by procedure/DRG codes.
- Risk scores by diagnosis codes.
- Quality measures defined by value sets of codes (VSAC: https://vsac.nlm.nih.gov).
- Medical necessity edits check dx-procedure pairs.
- Mapping across versions (ICD-9 to ICD-10 GEMs) is a legacy data problem.

## Free tools
- ICD-10-CM browser: https://icd10cmtool.cdc.gov
- CMS code files: https://www.cms.gov/medicare/coding-billing/icd-10-codes
- HCPCS: https://www.cms.gov/medicare/coding-billing/healthcare-common-procedure-system
- UMLS / RxNorm / LOINC downloads: https://www.nlm.nih.gov/research/umls/
- LOINC: https://loinc.org
- NPI lookup: https://npiregistry.cms.hhs.gov
- NUCC taxonomy: https://nucc.org
- MS-DRG definitions manual: https://www.cms.gov/medicare/payment/prospective-payment-systems/acute-inpatient-pps/ms-drg-classifications-and-software
- Practice coding: https://www.aapc.org (certs: CPC, CRC for risk adjustment)
