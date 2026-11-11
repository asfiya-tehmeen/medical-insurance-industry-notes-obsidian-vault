# SQL for Claims Analytics (with worked patterns)

Assume tables: `member_month(member_id, month, plan_id)`, `claim_line(claim_id, line_no, member_id, provider_npi, dos, cpt, dx1, billed, allowed, paid, status)`, `claim_header(claim_id, member_id, admit_dt, disch_dt, claim_type)`.

## 1. PMPM by month
```sql
select m.month,
       sum(c.paid) / count(distinct m.member_id) as pmpm
from member_month m
left join claim_line c
  on c.member_id = m.member_id
 and date_trunc('month', c.dos) = m.month
 and c.status = 'PAID'
group by m.month order by m.month;
```
Careful: joining one row per member-month to many claim lines is fine for summing paid, but `count(distinct member_id)` per month equals member months only if each member has one row per month. Better: aggregate claims first, then join.

## 2. Aggregate first (avoid fan-out)
```sql
with c as (select member_id, date_trunc('month', dos) month, sum(paid) paid
           from claim_line where status='PAID' group by 1,2)
select m.month, sum(coalesce(c.paid,0)) / count(*) pmpm
from member_month m left join c using (member_id, month)
group by m.month;
```

## 3. Top 1% cost members
```sql
select * from (
  select member_id, sum(paid) tot,
         ntile(100) over (order by sum(paid) desc) pct
  from claim_line group by member_id) t
where pct = 1;
```

## 4. 30-day readmissions
```sql
with stays as (
  select member_id, admit_dt, disch_dt,
         lead(admit_dt) over (partition by member_id order by admit_dt) next_admit
  from claim_header where claim_type='INPATIENT')
select count(*) filter (where next_admit - disch_dt <= 30) * 1.0 / count(*) readmit_rate
from stays;
```

## 5. Latest claim version only
See [[Healthcare Data Pipelines]]: `row_number()` pattern.

## 6. Duplicate claim detection
```sql
select member_id, provider_npi, dos, cpt, count(*) n
from claim_line group by 1,2,3,4 having count(*) > 1;
```

## 7. Continuous enrollment (HEDIS-style: no gap >45 days in 12 months)
Use gaps-and-islands: `month - row_number() over (partition by member_id order by month) * interval '1 month'` as a grouping key to find consecutive-month islands.

## 8. Outlier providers (upcoding)
```sql
select provider_npi,
       avg((cpt='99215')::int) pct_99215,
       count(*) visits
from claim_line where cpt in ('99212','99213','99214','99215')
group by 1 having count(*) > 100
order by pct_99215 desc;
```

## 9. Denial analysis
```sql
select denial_code, count(*) n, sum(billed) billed_amt,
       round(100.0*count(*)/sum(count(*)) over (),1) pct
from claim_line where status='DENIED' group by 1 order by n desc;
```

## 10. Cohorts
Diabetics: members with ≥2 outpatient claims with dx like 'E11%' or ≥1 inpatient in 12 months (typical rule-based cohort definition, stated explicitly).

## Skills that matter
Window functions, CTEs, conditional aggregation, date logic, self-joins, deduplication, gaps-and-islands, percentiles, careful fan-out handling. Practice list in [[SQL Practice Plan]].
