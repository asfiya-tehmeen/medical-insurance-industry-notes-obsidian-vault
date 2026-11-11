# Interview Best Practices and Resources

You're new to the industry, so your edge is: **structured thinking + visible effort + clear communication + a project**. Domain depth comes from [[Interview Questions and Answers]]; this note is the "how to win the interview" playbook.

## The process (typical)
1. Recruiter screen (15-30 min): motivation, salary range, basic fit.
2. Hiring-manager screen: experience, domain interest.
3. Technical: SQL live-coding, Python, data modeling, or case study / take-home.
4. Panel / behavioral: cross-functional (compliance, ops, actuarial).
5. Final / senior leader; reference checks; sometimes background check and HIPAA training later.

## Best practices
### Before
- Research the company 30 min (see [[Target Companies]]); know their lines of business, latest earnings highlights, and one recent news item.
- Re-read the job description; map every bullet to a project or story.
- Prepare a **60-second pitch**: "I'm a [data person] who prepared deeply for health insurance by building [project]. I'm interested in [claims analytics/compliance reporting] because [reason]."
- Prepare 5 STAR stories (details below) and 5 questions to ask.
- Set up a quiet space, test tech, have water, resume, notebook.

### During
- **Clarify before solving**: restate the question, ask about data grain, edge cases ("Is claim_id unique? Are there adjustments/reversals?"). This alone impresses in healthcare data interviews.
- **Think aloud**; state assumptions; start simple, then optimize.
- **SQL**: write the CTE structure first, name things clearly, check fan-out joins, handle NULLs, test with a tiny example mentally, mention performance (indexes, partitions) at the end.
- **Say "I don't know, here's how I'd find out."** Honesty plus method beats bluffing, especially on regulations.
- **Use domain language correctly** but sparingly (PMPM, adjudication, member months).
- **Always add the compliance lens**: PHI, minimum necessary, audit trail, reproducibility.
- **Tie answers to business impact**: cost, accuracy, member experience, audit risk.
- Be concise: 1-2 minute answers; ask "would you like more detail?"

### After
- Thank-you email within 24 hours: reference a specific conversation point + one idea or follow-up.
- Log questions asked and what you'd improve.

## STAR stories (prepare these 5)
Structure: **S**ituation (1 line) · **T**ask · **A**ction (most time, "I") · **R**esult (numbers) · optional **L**earning.
1. Found/fixed a data quality issue (prevented wrong reporting).
2. Disagreement with stakeholder; how you aligned.
3. Delivered under a tight deadline / ambiguity.
4. Learned a new complex domain quickly (use this industry prep, your project).
5. Automated or improved a process (hours saved, error reduction).
Compliance-flavored extra: a time you handled sensitive data or followed a rule even when inconvenient.

## Handling "no industry experience"
- Lead with the **project**: "I built a claims warehouse from synthetic Medicare-style data, with reconciliation, dbt tests, and a HIPAA design doc."
- Show **learning velocity**: certifications/training (HIPAA course, AHIP fundamentals), reading earnings reports, tracking CMS rules.
- Translate prior experience: any regulated, financial, or transactional data work counts (banking, audit, e-commerce reconciliation).
- Offer the **first 90 days plan**.

## Technical prep checklist
- SQL: joins, window functions, CTEs, dedupe, gaps-and-islands, cohorts, running totals. Practice via [[SQL Practice Plan]].
- Python/pandas: [[Python and Coding Problems]].
- Data modeling: star schema for claims, SCD2, member-month table. See [[Core Data Domains]].
- Pipelines: idempotency, reconciliation, late data, monitoring. See [[Healthcare Data Pipelines]].
- Compliance: HIPAA rules, breach steps, de-identification, minimum necessary. See [[HIPAA]].
- Domain: claim lifecycle, 837/835/834, ICD/CPT, PMPM/MLR, HEDIS, risk adjustment.
- Current events: [[Industry Trends (as of Oct 2026)]], [[Deals and MA to Know]].

## Case-study framework (analytics/ops problems)
1. **Clarify objective** and who uses the output.
2. **Define metrics** precisely (numerator, denominator, time window).
3. **Identify data** and limitations (lag, adjustments, missing codes).
4. **Analyze** (segment, trend, compare to benchmark, decompose price x volume x mix).
5. **Recommend** with impact estimate and risks.
6. **Control/monitor** (dashboard, alert, audit evidence).
Example prompts: "Cost per member rose 9%, why?" "Denials spiked last month." "Design a report CMS will audit." "Reduce time to produce HEDIS gap lists."

## Whiteboard/system design framework
Requirements (volume, latency, SLA, compliance) → sources/ingest → storage layers → transformations & quality → serving → security/privacy → monitoring/DR → trade-offs → how you'd evolve it.

## Salary & negotiation
- Research ranges: Levels.fyi, Glassdoor, Payscale, BLS https://www.bls.gov/ooh/, state pay-transparency postings (many states require salary ranges in job ads).
- Don't give a number first if avoidable: "What's the budgeted range?" Then anchor within it.
- Consider total comp: bonus, 401k match, remote policy, certification reimbursement.

## Resources for interview prep
**SQL / coding**
- [[SQL Practice Plan]] (LeetCode, DataLemur, StrataScratch, HackerRank)
- NeetCode roadmap (coding patterns): https://neetcode.io
- Mode SQL tutorial: https://mode.com/sql-tutorial
- Window functions explained visually: https://selectstarsql.com
- SQL interview questions repo (search GitHub "sql-interview-questions")
**Data engineering**
- Data Engineering Zoomcamp: https://github.com/DataTalksClub/data-engineering-zoomcamp
- DE interview guide (Seattle Data Guy, YouTube) and Joe Reis' *Fundamentals of Data Engineering*
- System Design Primer: https://github.com/donnemartin/system-design-primer
- Interview Query: https://www.interviewquery.com
**Behavioral**
- Amazon-style STAR guides (many free); *Cracking the Coding Interview* behavioral chapter; Pramp mock interviews https://www.pramp.com ; interviewing.io https://interviewing.io
- Practice aloud with a friend or record yourself.
**Domain**
- KFF, CMS, HHS sites in [[Learning Resources]]
- Earnings call transcripts (Motley Fool, SEC EDGAR) of UnitedHealth, Elevance, Humana, Centene, CVS
- HIMSS, HFMA, AHIP content
**Compliance**
- HHS OCR resolution agreements to cite real cases: https://www.hhs.gov/hipaa/for-professionals/compliance-enforcement/agreements/index.html
- OIG advisory opinions and enforcement: https://oig.hhs.gov
- IAPP privacy resources: https://iapp.org

## Daily/weekly news routine (15 min/day)
- Morning: skim **Fierce Healthcare**, **Becker's Payer**, **Healthcare Dive**, **STAT**, **Axios Vitals**, **Modern Healthcare**.
- Weekly: **KFF Health News**, **Health Affairs Forefront**, CMS newsroom https://www.cms.gov/newsroom, Federal Register search for "CMS" proposed/final rules.
- Quarterly: earnings season (Jan, Apr, Jul, Oct) - read one earnings release per week.
- Keep a **"news notebook"**: date, headline, why it matters, data/compliance implication. 10 entries make you sound current.

## Red flags to avoid
- Claiming experience you don't have in regulated environments.
- Casually describing PHI handling (e.g., "I'd just download it").
- Joining tables without thinking about duplicates/adjustments.
- Speaking negatively about previous employers.
- Not asking questions.

## Questions that impress
- "How do you reconcile data across claims, eligibility, and finance for regulatory reporting?"
- "What changes is the team making for CMS-0057-F (prior authorization API and metrics)?"
- "How are you governing AI used in utilization management?"
- "What are the biggest data-quality pain points in provider data?"
- "How does the data team partner with compliance during audits?"

## 7-day crash plan before an interview
D1 company research + role mapping · D2 SQL drills (window functions) · D3 domain Q&A review · D4 compliance scenarios ([[Compliance and Domain Case Problems]]) · D5 mock behavioral + STAR · D6 mock technical/case with a friend or Pramp · D7 review news, rest, prepare questions.
