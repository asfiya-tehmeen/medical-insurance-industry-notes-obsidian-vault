# Portfolio Projects (build 2-3, put on GitHub)

## Project A: Claims Warehouse (Data Engineering)
- Data: Synthea CSV export (https://synthea.mitre.org) or CMS SynPUF.
- Build: Postgres/DuckDB + dbt + Airflow. Layers raw → staging → marts (`fact_claim_line`, `dim_member`, `member_month`).
- Add: dbt tests, data-quality report, lineage diagram, README with HIPAA considerations section.
- Deliver: PMPM and utilization dashboard.

## Project B: EDI 837/835 Parser + Reconciler (Automation + domain)
- Parse sample files, load to tables, reconcile billed vs paid, report top denial CARC codes.
- Add pytest tests, CLI, logging, Docker.

## Project C: Provider Fraud Detection (Analytics/ML)
- Data: Kaggle provider fraud dataset (see [[Data Engineering and Analytics Problems]]).
- Peer-group outliers, features per provider, gradient boosting, SHAP explanations, precision@k, discussion of false positives and compliance.

## Project D: HEDIS-style Measures
- Implement 2-3 measures (diabetes HbA1c testing, breast cancer screening, readmissions) from public specs on Synthea data. Show denominator/numerator/exclusion SQL and gap list.

## Project E: Compliance Control Monitor
- Automated checks: missing files, schema drift, PHI scanner, LEIE screening. Output HTML/Excel evidence pack.

## Project F: FHIR Patient Access Mini-API
- Flask/FastAPI service exposing `ExplanationOfBenefit` from your claims tables in FHIR JSON; validate with HL7 validator.

## Project G: Price Transparency Explorer
- Process payer machine-readable files for one plan; compare negotiated rates vs Medicare fee schedule.

## How to present
README with problem, architecture diagram, data sources, results, decisions/trade-offs, privacy/compliance notes, how to run. Short 2-min Loom walkthrough. Link from LinkedIn/resume.
