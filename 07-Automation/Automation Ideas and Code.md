# Automation Ideas and Code

## What's worth automating (high ROI in payer/compliance work)
1. **File intake monitoring**: check SFTP for expected 834/837 files; alert if missing/late.
2. **EDI parsing + validation**: parse X12, compare control totals, reject bad files.
3. **Reconciliation reports**: claims in vs out per day; dollars per source vs warehouse.
4. **Exclusion screening**: monthly compare providers/employees to OIG LEIE & SAM.gov.
5. **Directory validation**: check NPIs against NPPES, flag deactivated or mismatched.
6. **Regulatory report generation**: scheduled SQL → Excel/CSV → approvals → archive.
7. **Audit universe pulls**: parameterized queries producing consistent evidence.
8. **PHI scanner**: regex/ML scan of tables, S3 buckets, logs for SSNs, DOBs, MRNs.
9. **Appeal/grievance timeliness alerts**: cases nearing deadline.
10. **Document processing**: OCR + NLP on faxed PA requests, auto-classify and extract.
11. **Data quality tests in CI/CD**: dbt tests on every pull request.
12. **RPA for portal checks** (claim status), though APIs/EDI preferred.
13. **Access reviews**: export user-role matrix, flag stale or excessive access.
14. **LLM assistants** (with BAA/guardrails): summarize policies, draft denial letter checks, Q&A over regulations.

## Code 1: NPI Luhn validation
```python
def valid_npi(npi: str) -> bool:
    if len(npi) != 10 or not npi.isdigit():
        return False
    digits = "80840" + npi          # NPI uses prefix 80840 for Luhn
    total, alt = 0, False
    for ch in reversed(digits):
        d = int(ch)
        if alt:
            d *= 2
            if d > 9: d -= 9
        total += d
        alt = not alt
    return total % 10 == 0

assert valid_npi("1234567893")
```

## Code 2: tiny X12 837 parser
```python
def parse_x12(text: str):
    text = text.strip()
    seg_term = text[105]        # ISA is fixed width; char after ISA16 is the segment terminator
    elem_sep = text[3]
    return [s.split(elem_sep) for s in text.split(seg_term) if s.strip()]

segs = parse_x12(open("sample_837.edi").read())
claims = [s for s in segs if s[0] == "CLM"]
for c in claims:
    print("claim", c[1], "charge", c[2])
total = sum(float(c[2]) for c in claims)
```
Compare `total` to the SE/BHT or file control totals; log mismatches.

## Code 3: missing-file monitor (Airflow style logic)
```python
import datetime as dt, os
expected = [f"MEMBERS_{dt.date.today():%Y%m%d}.834", f"CLAIMS_{dt.date.today():%Y%m%d}.837"]
missing = [f for f in expected if not os.path.exists(f"/inbound/{f}")]
if missing:
    raise RuntimeError(f"Missing files: {missing}")   # Airflow marks task failed -> alert
```

## Code 4: PHI regex scan
```python
import re
PATTERNS = {"ssn": r"\b\d{3}-\d{2}-\d{4}\b", "phone": r"\b\(?\d{3}\)?[-.\s]\d{3}[-.\s]\d{4}\b",
            "dob": r"\b(0[1-9]|1[0-2])/(0[1-9]|[12]\d|3[01])/(19|20)\d{2}\b",
            "email": r"[\w.+-]+@[\w-]+\.[\w.-]+"}
def scan(text): return {k: re.findall(p, text) for k, p in PATTERNS.items() if re.search(p, text)}
```

## Code 5: pandas data-quality report
```python
import pandas as pd
df = pd.read_csv("claims.csv", parse_dates=["dos", "paid_dt"])
checks = {
 "null_member": df.member_id.isna().sum(),
 "paid_gt_allowed": (df.paid > df.allowed).sum(),
 "dos_after_paid": (df.dos > df.paid_dt).sum(),
 "dupe_lines": df.duplicated(["claim_id", "line_no"]).sum(),
}
print(pd.Series(checks))
```

## Tool stack
Python (pandas, requests, pydantic), SQL, Airflow/Prefect, dbt, GitHub Actions, PowerShell/Bash, Power Automate, UiPath (RPA), pytest, Great Expectations, Docker.

## Learn
- Automate the Boring Stuff (free): https://automatetheboringstuff.com
- Airflow tutorial: https://airflow.apache.org/docs/apache-airflow/stable/tutorial/
- OIG LEIE downloadable database: https://oig.hhs.gov/exclusions/exclusions_list.asp
- NPPES downloadable files: https://download.cms.gov/nppes/NPI_Files.html
- SAM.gov exclusions: https://sam.gov
