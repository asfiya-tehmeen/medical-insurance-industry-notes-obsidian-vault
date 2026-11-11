# Industry Trends: What's Going On Right Now (as of 28 Oct 2026)

Confidence tags: **[Verified]** = found in a 2026 source during research (linked). **[Background]** = from my general knowledge, so double-check before quoting in an interview.
Rule: in an interview, say *"as of [month], reporting says..."* instead of stating shaky facts as certain.

## 1. Insurers are squeezed by medical costs
- High utilization and cost trend have pressured margins across big payers for ~2 years. **[Verified]**
- UnitedHealth Q3 2026 (Oct 13): medical care ratio 88.4% (vs 89.9% a year earlier); raised 2026 EPS guidance to ≥ $20.50; said commercial cost trend is above 11%, driven by **No Surprises Act costs and high-cost specialty drugs**; called 2026 a trough year for core Medicaid margins. [CNBC](https://www.cnbc.com/2026/10/13/unitedhealth-group-unh-earnings-q3-2026.html), [Motley Fool transcript](https://www.fool.com/earnings/call-transcripts/2026/10/13/unitedhealth-unh-q3-2026-earnings-call-transcript/)
- Centene Q3 2026 (Oct 27): raised guidance to > $5.20 adjusted EPS; Medicare Advantage expected to reach breakeven in 2026; managing Medicaid membership changes as states implement **work requirements / eligibility terminations under the "One Big Beautiful Bill Act"**. [Centene 8-K](https://www.sec.gov/Archives/edgar/data/0001071739/000107173926000194/a20261027ex991pressrelease.htm)
- Upcoming: CVS Health reports **Nov 4**, Humana **Nov 6**. CVS exited the individual ACA exchange business in 2026. **[Verified]** Read these earnings releases; they're free and a great interview talking point.
- **Why you care:** cost pressure = demand for payment integrity, fraud analytics, utilization analytics, and automation (do more with fewer people).
- **Check yourself:** status of ACA enhanced premium subsidies (they were set to expire after 2025; I did not verify what happened) and the CMS 2027 Medicare Advantage rate notice.

## 2. Prior authorization reform: CMS-0057-F (the biggest data/compliance driver)
- Since **Jan 1, 2026**: impacted payers must decide standard PA requests in **7 calendar days**, expedited in **72 hours**, and give a specific denial reason. **[Verified]**
- Starting **March 2026**: payers publicly report PA metrics (approval/denial rates, turnaround). **[Verified]**
- By **Jan 1, 2027**: FHIR APIs (Provider Access, Payer-to-Payer, Prior Authorization) due. **[Verified]**
- CMS proposed extending electronic PA to **drugs**; compliance would be about Oct 2027 if finalized. **[Verified]** [Healthcare Dive](https://www.healthcaredive.com/news/cms-proposes-drug-prior-authorizations-electronic-deadlines/817287/)
- **Jobs this creates:** FHIR engineers, metrics reporting analysts, compliance testers, API security. See [[FHIR and Interoperability]].
- Source summary: [Becker's: policies taking effect 2026](https://www.beckerspayer.com/policy-updates/notable-health-insurance-policies-taking-effect-in-2026/)

## 3. AI in claims, prior auth, and the backlash
- CMS **WISeR pilot** (started Jan 1, 2026): uses AI/ML to help review prior authorization in *traditional* Medicare in 6 states (NJ, OH, OK, TX, AZ, WA) through 2031. Critics worry about incentives to deny. **[Verified]** [US News](https://www.usnews.com/news/health-news/articles/2026-02-10/medicare-is-experimenting-with-having-artificial-intelligence-review-claims-but-there-are-risks), [Undark](https://undark.org/2026/07/15/medicare-prior-authorization-ai/)
- **States are regulating AI denials**: e.g., Washington and Alabama enacted 2026 laws; Washington bars relying *solely* on AI to deny/delay/limit care in PA. **[Verified]** [Holland & Knight](https://www.hklaw.com/en/insights/publications/2026/05/states-continue-efforts-to-regulate-ai-in-healthcare)
- Scrutiny of AI-assisted blanket denials in Medicare Advantage. [Nature npj Digital Medicine](https://www.nature.com/articles/s41746-026-02387-x)
- **Interview angle:** "human in the loop", explainability, audit trails, bias testing, model governance. Mention you'd log every automated decision with reasons.
- Also: generative AI for call summaries, appeals letters, coding/CDI, document intake, with PHI guardrails and BAAs.

## 4. PBM reform and scrutiny of vertical integration
- **Congress passed PBM reform in the Consolidated Appropriations Act, 2026 (Feb 3, 2026)**: 100% rebate pass-through (employer plans), delinking/spread-pricing bans in Part D, transparency; more provisions phase in 2028-29. **[Verified, secondary sources]** [Mintz, Fall 2026 update](https://www.mintz.com/insights-center/viewpoints/2026-10-01-pbm-policy-and-legislative-update-fall-2026)
- **FTC vs. the Big 3 PBMs** (Express Scripts, Caremark, OptumRx; ~80% of prescriptions): Express Scripts settled Feb 2026, Caremark also settled; Optum was reported as still pending. **Verify current status on ftc.gov.** [Duane Morris](https://www.duanemorris.com/alerts/pharmacy_benefit_manager_reaches_settlement_ftc_requiring_changes_drug_pricing_practices_0726.html), [Health Affairs](https://www.healthaffairs.org/doi/full/10.1377/forefront.20260826.262379)
- A federal judge blocked a first-in-nation state law banning PBM ownership of pharmacies. **[Verified]**
- **Why you care:** new reporting and data-pass-through requirements = data work.

## 5. Cybersecurity and resilience (Change Healthcare legacy)
- The **Feb 2024 ransomware attack on Change Healthcare (UnitedHealth subsidiary)** disrupted claims, eligibility, and PA nationwide; UnitedHealth said it may have affected about one-third of Americans' data; 94% of hospitals reported financial impact (AHA survey). **[Verified]** [Healthcare Dive](https://www.healthcaredive.com/news/change-healthcare-cyberattack-aftermath-cybersecurity-netspi/713617/)
- Fallout: proposed HIPAA Security Rule overhaul (mandatory encryption, MFA, network segmentation, asset inventory, 72-hr restore) **[Background: proposed Jan 2025; check final status]**, vendor concentration risk, third-party risk management, business continuity.
- **Interview angle:** "single point of failure", downstream vendor oversight, backup/restore testing, incident response.

## 6. Interoperability and data-sharing
- TEFCA national exchange network, USCDI versions, ONC/ASTP HTI rules, information-blocking enforcement **[Background]**.
- Payer-to-payer exchange and Patient Access APIs (already required) pushing payers to have clean, FHIR-mappable claims data.
- **CAQH is moving from nonprofit to ownership by leading insurers** **[Verified]** (see [[Deals and MA to Know]]).

## 7. Medicare Advantage: tougher oversight, margin repair
- Plans cut benefits/exited counties to repair margins; providers increasingly refusing MA contracts **[Verified, Nature piece]**.
- RADV audits being expanded by CMS **[Background: CMS announced in 2025 plans to audit all MA contracts annually; verify]**; DOJ False Claims Act scrutiny of coding intensity. See [[Risk Adjustment]].
- Star Ratings pressure remains. See [[Quality HEDIS and Star Ratings]].

## 8. Medicaid changes
- Work requirements, more frequent eligibility redeterminations, state budget stress (via the One Big Beautiful Bill Act). **[Verified at headline level]** Expect enrollment volatility, acuity shifts, and heavy eligibility-data work.

## 9. Price transparency enforcement
- Transparency in Coverage machine-readable files and hospital price files; enforcement/standards updates ongoing **[Background]**. Great portfolio material (big JSON files).

## 10. Provider consolidation and vertical integration
- Hospital M&A is at its highest pace since 2019 in Q2 2026 (Kaufman Hall), with large deals such as Sutter-Allina, Rush-Endeavor, HealthPartners-Essentia. **[Verified]** [Chief Healthcare Executive](https://www.chiefhealthcareexecutive.com/view/hospital-mergers-in-2026-exceed-last-year-and-more-deals-are-likely)
- Payers own providers (Optum, CenterWell, CVS/Oak Street) which raises antitrust/data-sharing issues.

## 11. Other themes to know by name
Value-based care and risk-bearing providers; GLP-1 (Ozempic/Wegovy) coverage costs; specialty drugs/biosimilars; site-of-care shifts and 340B; behavioral health access and parity enforcement (MHPAEA); telehealth flexibilities; ICHRA (employers giving money to buy individual plans); employer cost trend 8-9%+ **[Background]**; workforce shortages; consumer privacy laws (state health-data laws); AI regulation; payment integrity and "downcoding" controversy; digital front door and member experience.

## Staying current (15 min/day)
See [[Interview Best Practices and Resources]] for the news routine and sources.
