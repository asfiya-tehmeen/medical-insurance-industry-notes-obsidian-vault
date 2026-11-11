# X12 EDI Transactions

EDI = computers exchanging standardized text files. Healthcare uses **ASC X12 version 5010** (mandated by HIPAA).

| Transaction | Name | Direction | Purpose |
|---|---|---|---|
| **837P / 837I / 837D** | Claim (professional/institutional/dental) | Provider → Payer | Submit a bill |
| **835** | Remittance advice (ERA) | Payer → Provider | Explain payment |
| **834** | Benefit enrollment & maintenance | Employer → Payer | Add/change/terminate members |
| **820** | Premium payment | Employer → Payer | Pay premiums |
| **270 / 271** | Eligibility inquiry / response | Provider ↔ Payer | Is the member covered? |
| **276 / 277** | Claim status request / response | Provider ↔ Payer | Where is my claim? |
| **278** | Prior auth / referral | Provider ↔ Payer | Request/decision |
| **999 / TA1** | Acknowledgements | Receiver → Sender | File accepted/rejected |
| **277CA** | Claim acknowledgement | Payer → Provider | Claim-level accept/reject |

## File anatomy
Text with delimiters: `~` ends a segment, `*` separates elements, `:` separates sub-elements.
```
ISA*00*          *00*          *ZZ*SENDER         *ZZ*RECEIVER       *260101*1200*^*00501*000000001*0*P*:~
GS*HC*SENDER*RECEIVER*20260101*1200*1*X*005010X222A1~
ST*837*0001*005010X222A1~
BHT*0019*00*0123*20260101*1200*CH~
NM1*41*2*CLINIC NAME*****46*ABC123~        <- submitter
NM1*85*2*BILLING PROVIDER*****XX*1234567893~ <- billing provider NPI
...
CLM*CLAIM123*200***11:B:1*Y*A*Y*Y~         <- claim: id, total charge, place of service 11
HI*ABK:E119~                               <- diagnosis (ABK = ICD-10 principal)
LX*1~                                      <- service line 1
SV1*HC:99213*200*UN*1***1~                 <- procedure 99213, $200, 1 unit
DTP*472*D8*20251215~                       <- date of service
SE*..*0001~ GE*..~ IEA*..~
```
**Loops** group segments hierarchically: 2000A billing provider → 2000B subscriber → 2000C patient → 2300 claim → 2400 service line. 

## Structure of 835
`BPR` payment amount/method, `TRN` trace number, `CLP` claim payment (status, billed, paid, patient responsibility), `CAS` adjustments (group code CO=contractual, PR=patient responsibility, OA=other + CARC + amount), `SVC` line detail.

## Quirks you'll meet
- Companion guides: each payer adds its own rules on top of the standard.
- Claim frequency code: 1 original, 7 replacement, 8 void.
- Huge files, bad data, partial rejections; need robust parsers and reconciliation (file → claim → line counts and $ totals).
- Newer API-based approaches (FHIR) gradually coexist.

## Tools
- Python: `pyx12`, `hl7apy` (HL7 v2), `fhir.resources`, or custom parser (split on `~` and `*`).
- X12 official: https://x12.org
- CMS/CAQH CORE operating rules: https://www.caqh.org/core
- Free 5010 guides summary: https://www.cms.gov/medicare/regulations-guidance/electronic-data-interchange/5010
- WPC (Washington Publishing Co.) implementation guides are paid; many payers publish free companion guides.
- Sample 837s: search GitHub "837 sample edi" and pyx12 test data: https://github.com/azoner/pyx12
