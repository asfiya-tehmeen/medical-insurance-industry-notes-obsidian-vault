# Datasets and Sandboxes (all free; no real PHI)

| Dataset | What | Link |
|---|---|---|
| **Synthea** | Synthetic patients: CSV/FHIR incl. claims & payer data | https://synthea.mitre.org (data downloads at /downloads) |
| **CMS DE-SynPUF** | Synthetic Medicare claims 2008-2010, beneficiaries, Rx | https://www.cms.gov/data-research/statistics-trends-and-reports/medicare-claims-synthetic-public-use-files |
| **CMS Data portal** | Medicare provider utilization & payment, Part D prescribers, hospital quality | https://data.cms.gov |
| **Medicaid/CHIP data** | Drug utilization, NADAC prices | https://data.medicaid.gov |
| **Open Payments** | Pharma payments to doctors | https://openpaymentsdata.cms.gov |
| **NPPES** | All US provider NPIs (bulk) | https://download.cms.gov/nppes/NPI_Files.html |
| **OIG LEIE** | Excluded providers | https://oig.hhs.gov/exclusions/exclusions_list.asp |
| **HCUP** (some free tools) | Hospital discharge databases | https://hcup-us.ahrq.gov |
| **MEPS** | Household spending/insurance survey | https://meps.ahrq.gov |
| **CDC WONDER / NCHS** | Public health stats | https://wonder.cdc.gov |
| **ACA Marketplace PUFs** | Plans, rates, benefits, networks | https://www.cms.gov/marketplace/resources/data/public-use-files |
| **Transparency in Coverage guide + samples** | Machine-readable rate files | https://github.com/CMSgov/price-transparency-guide |
| **MIMIC-IV** (credentialed, free after training) | ICU clinical data | https://physionet.org/content/mimiciv/ |
| **OMOP / OHDSI** | Common clinical data model + tools | https://www.ohdsi.org ; book https://ohdsi.github.io/TheBookOfOhdsi/ |
| **Kaggle provider fraud** | Labeled claims | https://www.kaggle.com/datasets/rohitrox/healthcare-provider-fraud-detection-analysis |
| **Kaggle insurance charges** | Simple regression | https://www.kaggle.com/datasets/mirichoi0218/insurance |
| **HAPI FHIR public server** | Test FHIR API | https://hapi.fhir.org |
| **CMS Blue Button sandbox** | Medicare claims via FHIR | https://bluebutton.cms.gov |
| **NIH/NLM UMLS, RxNorm, VSAC** | Terminologies, value sets | https://www.nlm.nih.gov/research/umls/ |
| **LOINC** | Lab codes | https://loinc.org |

## Local setup to practice
- DuckDB (single file analytics DB): https://duckdb.org — query CSV/Parquet instantly.
- Postgres via Docker; DBeaver as SQL client.
- Python env: pandas, polars, sqlalchemy, pyspark, dbt-duckdb.
- Free cloud tiers: Snowflake trial, BigQuery sandbox, Databricks Community Edition.
- Never put real PHI into free/untrusted tools.
