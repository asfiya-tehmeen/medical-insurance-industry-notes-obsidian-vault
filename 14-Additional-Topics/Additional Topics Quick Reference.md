# Additional Topics Quick Reference (gaps from the first pass)

Short, plain-English primers. Each is something interviewers casually assume you know.

## Business & product
- **Value-based care (VBC)**: pay for outcomes, not volume. Models: ACO (accountable care org), bundled payments, capitation, shared savings. Data need: member attribution, quality + cost scoring. Medicare examples: MSSP, ACO REACH.
- **ICHRA**: employer gives tax-free money; employees buy individual plans. Growing; shifts group business to individual market.
- **Medigap vs Medicare Advantage**: Medigap supplements Original Medicare (no network); MA replaces it (network, extra benefits).
- **Dual-eligibles / D-SNP**: people on both Medicare and Medicaid; special plans (D-SNP, FIDE-SNP) with extra integration/compliance rules.
- **Dental, vision, supplemental (accident, critical illness)**: smaller lines, different regulation.
- **Stop-loss**: insurance for self-funded employers; "lasering" high-risk individuals.
- **Workers' comp / auto medical**: other payers; subrogation links.
- **Telehealth & digital health**: payment parity flexibility is policy-dependent.
- **Behavioral health & parity (MHPAEA)**: payers must prove no stricter limits than medical care.
- **SDOH (social determinants)**: Z-codes (ICD-10 Z55-Z65), food/housing benefits, community referrals.
- **GLP-1 drugs**: massive cost driver; coverage rules and utilization management.
- **Specialty drugs / biosimilars / 340B**: cost drivers and contested programs.
- **Site-of-care steerage & facility fees**: shifting care to cheaper settings.
- **Employer benefits cycle**: renewals, RFPs, brokers, consultants (Mercer, WTW, Aon).

## Finance & actuarial basics
- **Rate filing**: states review premium increases. **Experience period**, trend, credibility, risk margin.
- **Reserves/IBNR**: unpaid claim estimates (completion factors).
- **Risk corridors / reinsurance / stop-loss**: mitigation of unexpected cost.
- **Medicare bids**: MA plans bid vs CMS benchmarks; rebate dollars fund extra benefits.
- **Capitation rate setting** (Medicaid): actuarially sound rates reviewed by CMS.
- Free learning: SOA https://www.soa.org ; Actuarial Society "Health Actuarial" intro materials; book *Health Insurance Rate Review* (state DOI sites).

## Operations & tech
- **Core admin systems**: Facets, QNXT, HealthRules, Amisys, plus claims scrubbers/pricers. Many are decades old; migrations are common.
- **Master data management**: member and provider golden records.
- **Credentialing vs enrollment vs contracting**: separate processes with separate data.
- **CAQH ProView**: provider-entered credentialing data.
- **Digital front door**: portal/app/ID cards/price estimator; Epic-payer integration.
- **EHR basics (Epic, Oracle Health)**: where clinical data comes from; HL7 v2 / CCDA / FHIR feeds into payers (ADT alerts for admissions).
- **ADT feeds**: admit/discharge/transfer notifications used for care transitions and readmission prevention.
- **Document AI**: OCR of faxes, medical records; LLM summarization (with PHI guardrails).
- **Cloud & security**: Snowflake/Databricks/Azure/AWS with BAAs; zero trust; SIEM; DLP.
- **Master test data**: synthetic data management (Synthea).
- **Legacy mainframe & COBOL** still present; data engineers often extract from DB2/Oracle/SQL Server.

## Compliance extras
- **Section 1557** (nondiscrimination, language access); **ADA accessibility** (WCAG for portals).
- **Medicare marketing rules (TPMO)**: call recording, disclaimers, agent oversight; big enforcement area.
- **FDR oversight**: first-tier, downstream, related entities (vendors) monitoring in MA/Part D.
- **OFAC/exclusion screening** (OIG LEIE, SAM.gov) monthly.
- **Conflict of interest**, gifts, anti-kickback training.
- **Records retention**: HIPAA documentation 6 years; Medicare 10 years for many records.
- **State consumer privacy & health-data laws** (e.g., Washington My Health My Data, California CCPA/CPRA, Texas, etc.).
- **Third-party risk management (TPRM)**: security questionnaires, SOC 2 reports, fourth-party risk.
- **Incident response & breach reporting**: HIPAA + state laws + contractual notification windows.
- **AI governance**: NIST AI RMF https://www.nist.gov/itl/ai-risk-management-framework ; state AI-in-insurance laws; NAIC AI model bulletin https://content.naic.org (search "AI model bulletin").
- **SOC 2 / HITRUST / ISO 27001** certification processes.

## Data-specific extras
- **Data governance roles**: data owner, steward, custodian; data dictionary; business glossary; critical data elements (CDEs) for regulatory reports.
- **Lineage & metadata tools**: Collibra, Alation, Atlan, OpenLineage.
- **Observability**: Monte Carlo, Soda, Great Expectations; SLAs/SLOs for data.
- **Data products & data mesh**: domain ownership; controversial but frequently mentioned.
- **Lakehouse / Iceberg / Delta**: open table formats.
- **Semantic layers / metrics layers**: dbt Semantic Layer, Cube, LookML.
- **Privacy tech**: tokenization, differential privacy basics, k-anonymity, synthetic data.
- **Vector search / RAG** over policies and medical necessity guidelines (with citations and access controls).
- **OMOP CDM**: standard clinical data model used in research; mapping claims to OMOP. https://ohdsi.github.io/TheBookOfOhdsi/
- **Time series & forecasting** for membership/claims.
- **Graph databases** for fraud rings/provider networks.

## Fast facts to memorize
- US health spending ≈ 17-18% of GDP (CMS NHE).
- ~90% of Americans insured; sources: employer ~half, Medicaid/CHIP ~20%, Medicare ~18%, individual ~7-8%. **[Background; confirm at census.gov/KFF]**
- MLR floors: 80% individual & small group, 85% large group.
- HIPAA breach notice: 60 days. Prior-auth decisions: 7 days / 72 hours (CMS-0057-F, 2026).
- ICD-10 updates Oct 1; CPT Jan 1; HEDIS technical specs annual (NCQA).
- Medicare open enrollment: Oct 15-Dec 7. ACA open enrollment generally Nov 1 - Jan 15 (varies by state exchange).
