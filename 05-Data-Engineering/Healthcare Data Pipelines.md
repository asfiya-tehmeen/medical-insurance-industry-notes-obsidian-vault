# Healthcare Data Pipelines

## Typical architecture
```
Sources: 837/835/834 files, PBM feeds, APIs (FHIR), vendor flat files, core admin DB (Facets/QNXT)
   -> Ingestion (SFTP, AWS Transfer, Kafka/CDC, Fivetran, Airflow)
   -> Raw/Landing zone (immutable, encrypted)         [bronze]
   -> Standardize/clean/parse                          [silver]
   -> Business models: claims_fact, member_month, etc. [gold / marts]
   -> Consumers: BI (Tableau/Power BI), actuarial, regulatory reports, ML, APIs
```
Platforms: Snowflake, Databricks, BigQuery, Redshift, Azure Synapse. Tools: Airflow, dbt, Spark, Python, SQL, Terraform, Git, Great Expectations/Soda, Collibra/Alation (catalog).

## Design patterns that matter here
1. **Immutable raw layer**: keep original files for audit/replay.
2. **Idempotent loads**: rerunning a file doesn't double-count. Use file hash + load log.
3. **Slowly changing dimensions (SCD2)** for member coverage and provider attributes.
4. **Claim versioning**: keep every version; build a "current claim" view using latest version per claim_id/line (window function `ROW_NUMBER() OVER (PARTITION BY claim_id, line_no ORDER BY version DESC)`).
5. **Reconciliation / control totals**: records and dollars at each hop; log them.
6. **Late-arriving data**: partition by received date but model by service month; recompute trailing months.
7. **Effective-dated reference tables** (codes, fee schedules).
8. **Data contracts** with vendors: schema, SLAs, file naming.
9. **Orchestrated, monitored**: alerting on late/missing files (a missing eligibility file silently denies claims!).
10. **Environments**: dev with synthetic/masked data only.

## Data quality checks (starter list)
- Row counts vs control file; duplicates on natural key
- Nulls in required fields (member_id, dos, procedure)
- Valid values (ICD format/active on DOS, NPI Luhn check, state codes)
- Referential integrity (claim member exists in eligibility)
- Date logic (service ≤ paid; admit ≤ discharge; DOS within coverage)
- Amount logic (paid ≤ allowed ≤ billed; line sum = header total)
- Distribution drift (sudden spike in a code or denial rate)
- Freshness (latest file date)
Tools: Great Expectations https://docs.greatexpectations.io, dbt tests https://docs.getdbt.com/docs/build/data-tests, Soda https://docs.soda.io

## Security & privacy patterns
Encryption at rest/in transit, KMS key rotation, VPC/private link, SSO + MFA, RBAC and ABAC, dynamic masking policies (Snowflake), row-level security, tokenization of SSN/member ID, audit logging, data classification tags, minimum necessary views, de-identified analytic zone. See [[HIPAA]].

## Master data / entity resolution
Link member records across systems: deterministic (exact SSN+DOB) and probabilistic (Fellegi-Sunter; Python `splink` https://moj-analytical-services.github.io/splink/). Provider matching on NPI/TIN/address normalization.

## Streaming vs batch
Mostly batch (daily/weekly). Real-time for eligibility checks, PA decisions, pharmacy adjudication, fraud scoring pre-pay.

## Example dbt-style SQL: current claim lines
```sql
with ranked as (
  select *, row_number() over (
      partition by claim_id, line_no order by claim_version desc, load_ts desc) rn
  from silver.claim_line
)
select * from ranked where rn = 1 and claim_status <> 'VOID';
```

## Learn
- Data Engineering Zoomcamp (free): https://github.com/DataTalksClub/data-engineering-zoomcamp
- dbt Learn: https://learn.getdbt.com
- Airflow docs: https://airflow.apache.org/docs/
- Snowflake free trial & tutorials: https://docs.snowflake.com/en/user-guide/tutorials
- Book: *Fundamentals of Data Engineering* (Reis & Housley); *Designing Data-Intensive Applications* (Kleppmann)
- Kimball dimensional modeling: https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/kimball-techniques/dimensional-modeling-techniques/
