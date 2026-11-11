# Utilization Management (UM) and Prior Authorization

## Purpose
Make sure care is **medically necessary, appropriate, and cost-effective**. Insurers' most criticized function, and heavily regulated.

## Types of review
- **Prior authorization (pre-service)**: approve before surgery, imaging (MRI), expensive drugs, etc.
- **Concurrent review**: during a hospital stay, is continued stay needed?
- **Retrospective review**: after the fact.
- **Referral management**: HMO specialist referrals.

## Workflow
Provider submits request (fax/portal/X12 278/FHIR) → intake → nurse reviewer applies criteria (MCG, InterQual, plan policies) → if unclear, medical director → **approve / deny / pend for info** → notify provider and member → appeal path (internal, then external independent review).

## Timelines (regulatory)
Standard decisions typically within 14 days (shortening; CMS Interoperability & Prior Authorization rule pushes 7 days standard / 72 hours urgent and API-based PA). Urgent: 72 hours or less. Denial letters must give reasons and appeal rights.

## Metrics
Approval/denial rate, overturn rate on appeal, turnaround time, auto-approval (gold carding), volume by CPT.

## Care management (related)
Nurses/social workers support high-risk members: disease management (diabetes, CHF), transitions of care after discharge, maternity programs. Data teams build **risk stratification** models to target outreach.

## Pharmacy UM
Step therapy (try cheaper drug first), quantity limits, PA for specialty drugs. See [[Pharmacy Benefits and PBMs]].

## Resources
- CMS Interoperability and Prior Authorization final rule: https://www.cms.gov/priorities/key-initiatives/burden-reduction/policies-regulations/interoperability-prior-authorization
- HL7 Da Vinci PAS guide: https://hl7.org/fhir/us/davinci-pas/
- AMA PA research: https://www.ama-assn.org/practice-management/prior-authorization
