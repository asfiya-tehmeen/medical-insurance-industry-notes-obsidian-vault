# Fraud, Waste, Abuse (FWA) and Payment Integrity

## Definitions (simple)
- **Fraud**: intentional deception for gain (billing for services never performed).
- **Waste**: careless overuse of resources (unnecessary tests).
- **Abuse**: practices inconsistent with sound standards (billing a higher-paying code out of habit).
Estimates: a few percent of spend (tens of billions per year), hence a major analytics area.

## Common schemes
Phantom billing, **upcoding** (99215 instead of 99213), **unbundling** (billing parts of a package separately), duplicate billing, kickbacks, identity theft of members, pill mills, DME fraud, ABA/therapy over-billing, lab "add-on" tests, ghost providers.

## Payment integrity layers
1. **Pre-pay** edits (stop bad claims before paying): NCCI edits, duplicates, frequency limits, MUEs (medically unlikely edits).
2. **Post-pay review**: analytics find outliers; recoup overpayments.
3. **SIU investigations**: refer to state agencies, OIG, DOJ.
4. **Subrogation / COB recovery**: collect from other payers.

## Analytics ideas (great portfolio topics)
- Provider outliers vs peers (z-score of avg E/M level; % of 99215)
- Impossible days (more than 24 hrs of services in a day)
- Geographic impossibilities (member in two states same day)
- Network graphs (providers sharing patients/addresses/owners)
- Rule-based + ML anomaly detection (isolation forest)
- Opioid prescribing patterns (MME, multiple prescribers/pharmacies)

## Laws & agencies
**False Claims Act**, **Anti-Kickback Statute**, **Stark Law**, **HHS-OIG** (maintains the **LEIE** exclusion list: https://oig.hhs.gov/exclusions/), CMS program integrity contractors (UPIC, RAC), state Medicaid Fraud Control Units. Plans must screen providers against LEIE/SAM monthly.

## Compliance program requirements (Medicare Advantage/Part D)
Seven elements: policies, compliance officer & committee, training, effective lines of communication, enforcement/discipline, monitoring/auditing, prompt response and corrective action. First-tier/downstream/related entities (FDRs) must be overseen.

## Resources
- HHS-OIG: https://oig.hhs.gov
- NHCAA: https://www.nhcaa.org
- CMS Program Integrity: https://www.cms.gov/medicare/medicaid-coordination/fraud-prevention
