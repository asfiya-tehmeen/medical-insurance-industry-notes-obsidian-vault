# FHIR and Interoperability

## Plain English
**Interoperability** = different healthcare systems can exchange *and understand* each other's data. **FHIR** (Fast Healthcare Interoperability Resources, pronounced "fire") is the modern standard: a web REST API returning JSON "resources".

## Standards timeline
HL7 v2 (pipe-delimited messages, still dominant in hospitals) → CDA/C-CDA (XML documents) → **FHIR** (R4 is the mandated version; R5 exists).

## Key FHIR resources for payers
| Resource | Meaning |
|---|---|
| `Patient`, `Practitioner`, `Organization`, `Location` | People & places |
| `Coverage` | Insurance coverage |
| `Claim` / `ClaimResponse` | Submitted bill / result |
| **`ExplanationOfBenefit` (EOB)** | Adjudicated claim, the core of Patient Access API |
| `Condition`, `Procedure`, `Observation`, `MedicationRequest` | Clinical data |
| `Encounter` | A visit |
| `CoverageEligibilityRequest/Response` | 270/271 equivalent |
| `Bundle` | Package of resources |

Example REST call: `GET https://hapi.fhir.org/baseR4/Patient?family=Smith&_count=5`

Minimal JSON:
```json
{ "resourceType": "Patient", "id": "123",
  "name": [{"family": "Smith", "given": ["Ann"]}],
  "birthDate": "1980-04-02", "gender": "female" }
```

## Payer-relevant rules and implementation guides (IGs)
- **CMS Patient Access API**: members can read claims/EOBs and clinical data via third-party apps (OAuth2/SMART on FHIR). Reference IG: **CARIN Blue Button** (https://hl7.org/fhir/us/carin-bb/).
- **Provider Directory API**: **Da Vinci PDex Plan-Net**.
- **Payer-to-Payer exchange**: PDex.
- **Prior Authorization**: Da Vinci **CRD** (coverage requirements discovery), **DTR** (documentation templates), **PAS** (prior auth support).
- **US Core**: baseline clinical profiles. 
- **Bulk Data ($export)** for large datasets (population-level).
- **SMART on FHIR**: app authorization.
- **USCDI**: minimum data classes for US exchange. **TEFCA**: national exchange framework.

## Data-engineering tasks around FHIR
Mapping internal claims tables → ExplanationOfBenefit JSON; flattening FHIR to tables (e.g., with `fhir-py`, Google FHIR Data Pipes, or SQL-on-FHIR); validating against profiles; consent handling; rate limiting & audit logging; terminology mapping (ICD ↔ SNOMED).

## Hands-on
1. Browse public test server: https://hapi.fhir.org
2. Spec: https://hl7.org/fhir/ (read "Resource Index")
3. Learn: https://www.hl7.org/fhir/overview.html and Firely's tutorials https://fire.ly/resources/ 
4. Python: `pip install fhir.resources requests`; query HAPI, flatten into pandas.
5. Synthetic data with FHIR bundles: https://synthea.mitre.org/downloads
6. CMS Blue Button sandbox: https://bluebutton.cms.gov
7. HL7 v2: sample messages & parsers (`hl7` PyPI package).

## Related
ONC Cures Act rules (info blocking), HTI-1. See [[ACA and Other Key Laws]].
