# Data Engineering and Analytics Problems

## Hands-on practice sites
| Resource | Link | What |
|---|---|---|
| DE Zoomcamp (free course + homework) | https://github.com/DataTalksClub/data-engineering-zoomcamp | Docker, Airflow, dbt, Spark, Kafka, BigQuery |
| StrataScratch | https://platform.stratascratch.com | Analytics case-style questions |
| DataLemur | https://datalemur.com | SQL + product analytics |
| Interview Query | https://www.interviewquery.com | DE/DS interview questions |
| Kaggle | https://www.kaggle.com/competitions | Datasets & notebooks |
| DataExpert.io free materials | https://www.dataexpert.io | DE roadmap |
| Analytics Vidhya hackathons | https://datahack.analyticsvidhya.com | Healthcare hackathons appear (e.g., "Healthcare Analytics") |
| Databricks Academy (free) | https://www.databricks.com/learn/training/home | Spark/Lakehouse |
| Snowflake Quickstarts | https://quickstarts.snowflake.com | Guided labs |
| dbt tutorials | https://docs.getdbt.com/guides | Build models/tests |
| Great Expectations tutorials | https://docs.greatexpectations.io | Data quality |

## Healthcare-specific datasets to attempt problems on
- Kaggle "Medical Cost Personal Datasets": https://www.kaggle.com/datasets/mirichoi0218/insurance (regression on charges)
- Kaggle "Healthcare Provider Fraud Detection Analysis": https://www.kaggle.com/datasets/rohitrox/healthcare-provider-fraud-detection-analysis (inpatient/outpatient/beneficiary claims, labeled fraud providers; excellent portfolio project)
- Kaggle "Diabetes 130-US hospitals" readmission data: https://www.kaggle.com/datasets/brandao/diabetes
- More in [[Datasets and Sandboxes]]

## 12 problem statements to solve (with expected output)
**Data engineering**
1. Ingest daily CSV claims into Postgres idempotently (no duplicates on rerun). Add a load-log table.
2. Build SCD Type 2 table for member coverage changes from 834-style change records.
3. Parse 100 sample 837 files into claim_header/claim_line tables; reconcile totals.
4. Orchestrate steps 1-3 with Airflow; add failure alerts and retries.
5. Add dbt tests: unique(claim_id,line_no), not_null(member_id), relationships(member), accepted_values(status).
6. Process a 5GB "Transparency in Coverage" JSON with streaming (ijson) or Spark into a rates table; query median negotiated rate per CPT. Files: https://github.com/CMSgov/price-transparency-guide
**Analytics**
7. PMPM, MLR, utilization/1000 dashboard (Tableau Public/Power BI/Streamlit).
8. Price-volume-mix decomposition of cost trend year over year.
9. Identify top 20 outlier providers for E/M upcoding with peer comparison.
10. Predict 12-month high-cost claimants; evaluate with AUC and lift; check fairness by age/gender.
11. HEDIS-style measure: diabetes HbA1c testing rate with denominator/numerator/exclusions logic.
12. 30-day readmission analysis from CMS SynPUF or Synthea.

## Designing systems (whiteboard)
- Design a claims ingestion platform handling 10M claims/day with audit lineage.
- Design a near-real-time eligibility service.
- Design a PHI-safe analytics sandbox for 200 analysts.
- Design a FHIR Patient Access API backed by a claims warehouse.
Prep: https://github.com/donnemartin/system-design-primer ; book *Designing Data-Intensive Applications*.

## Certification-style practice
- Databricks Data Engineer Associate, Snowflake SnowPro Core, AWS Data Engineer Associate, dbt Analytics Engineering cert: https://www.getdbt.com/dbt-certification
