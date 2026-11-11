# SQL Practice Plan (with links)

## Platforms
| Platform | Best for | Link |
|---|---|---|
| LeetCode Database | Interview-style SQL (Easy→Hard) | https://leetcode.com/problemset/database/ |
| DataLemur | Real company SQL questions, **includes health/insurance-flavored ones** | https://datalemur.com |
| StrataScratch | Company questions with data; filter by SQL/Python | https://platform.stratascratch.com |
| HackerRank SQL | Basics → advanced, certificate | https://www.hackerrank.com/domains/sql |
| SQLZoo | Gentle beginner tutorials | https://sqlzoo.net |
| PG Exercises | PostgreSQL window functions/joins | https://pgexercises.com |
| Mode SQL Tutorial | Learn analytic SQL | https://mode.com/sql-tutorial |
| Kaggle Learn: Intro/Advanced SQL | Free short courses | https://www.kaggle.com/learn/intro-to-sql |
| SQL Murder Mystery | Fun beginner | https://mystery.knightlab.com |
| SQLBolt | Interactive lessons | https://sqlbolt.com |
| Advanced SQL puzzles (Itzik) | gaps/islands | https://www.sqlservercentral.com |

## Specific LeetCode problems (search by title)
Easy/Medium to know cold:
- Combine Two Tables, Second Highest Salary, Nth Highest Salary
- Rank Scores, Consecutive Numbers (gaps-and-islands)
- Department Top Three Salaries
- Duplicate Emails, Delete Duplicate Emails (dedupe claims!)
- Rising Temperature (day-over-day compare → claim trends)
- Trips and Users (cancellation rate → denial rate)
- Human Traffic of Stadium (islands → continuous enrollment)
- Last Person to Fit in the Bus (running totals → accumulators/deductible)
- Product Sales Analysis, Customers Who Bought All Products
- Patients With a Condition (literally medical!)
- Immediate Food Delivery II, Game Play Analysis I–IV (retention/cohorts → churn)
- Active Users, Monthly Transactions I/II
- Median Employee Salary, Find Median Given Frequency (percentiles for cost)
- Hard: Hopper Company Queries, Get Highest Answer Rate Question, Department Highest Salary

## DataLemur healthcare-flavored (search names)
"Patient Support Analysis (UnitedHealth)", "Cards Issued Difference" style questions, "Average Duration of Calls (UnitedHealth)", "Doctors..." sets. Use the site's Company filter → UnitedHealth Group, CVS Health, Cigna, Elevance.

## Domain problems you can create on your own data
Use claims-like datasets (below). Tasks:
1. PMPM by plan and month. 2. Top 10 CPT by paid. 3. 30-day readmission rate. 4. Members with ≥3 ER visits in 90 days. 5. Provider peers' % of high-level E/M. 6. Dedupe latest claim version. 7. Continuous enrollment check. 8. Deductible accumulator running total. 9. Denial rate by reason and provider. 10. Cohort retention of members by start month.

## Datasets
See [[Datasets and Sandboxes]].

## 6-week SQL ladder
W1 SELECT/WHERE/GROUP BY/JOIN (SQLBolt, SQLZoo) → W2 LeetCode easy (20) → W3 CTE, subquery, CASE, dates → W4 window functions (PG Exercises, LeetCode medium 20) → W5 gaps/islands, percentiles, performance (indexes, explain plans) → W6 domain tasks above + timed DataLemur.
