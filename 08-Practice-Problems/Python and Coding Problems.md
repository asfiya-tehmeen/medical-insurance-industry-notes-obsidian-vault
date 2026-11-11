# Python and Coding Problems

## Platforms
| Platform | Link | Use for |
|---|---|---|
| LeetCode | https://leetcode.com/problemset/ | Data structures, strings, hashing |
| LeetCode Pandas 30-day | https://leetcode.com/studyplan/introduction-to-pandas/ | pandas data wrangling |
| HackerRank Python | https://www.hackerrank.com/domains/python | Basics |
| Exercism Python | https://exercism.org/tracks/python | Mentored exercises |
| StrataScratch Python | https://platform.stratascratch.com | pandas on business data |
| Kaggle Learn Pandas/Python | https://www.kaggle.com/learn/pandas | Short courses |
| CodeSignal | https://codesignal.com | Used by employers for screening |
| Advent of Code | https://adventofcode.com | Parsing practice (EDI-like!) |
| Python Morsels / Real Python | https://realpython.com | Concepts |

## Problem types actually seen in data/health-IT interviews (and LeetCode names)
**Parsing / strings**
- Valid Parentheses (nested segments), Decode String, Longest Common Prefix
- Implement a delimited-file parser (split on `~`, `*`)
- Luhn check (Credit-card-like: NPI validation; "Check if a number is valid" variants)

**Hashing / grouping**
- Two Sum, Group Anagrams, Top K Frequent Elements (top procedures), Subarray Sum Equals K
- Find duplicate claims: Contains Duplicate I/II

**Intervals / dates (eligibility spans!)**
- Merge Intervals, Insert Interval, Meeting Rooms I/II, Non-overlapping Intervals (overlapping coverage periods)
- Employee Free Time

**Sorting / heaps / sliding window**
- Kth Largest Element, Merge k Sorted Lists, Moving Average from Data Stream, Longest Substring Without Repeating Characters

**Graphs (provider networks, member linkage)**
- Number of Connected Components, Accounts Merge (entity resolution!), Number of Islands

**Design**
- LRU Cache, Design Hit Counter (rate limit APIs), Time Based Key-Value Store (effective-dated fee schedules)

**pandas (LeetCode 30 Days of Pandas)**: Big Countries, Recyclable and Low Fat Products, Duplicate Emails, Employees Earning More Than Managers, Rank Scores, Group Sold Products by Date.

## Mini-coding projects (each ~2-4 hrs)
1. **Eligibility span merger**: given rows (member, start, end), merge overlapping/adjacent spans, find gaps > 30 days.
2. **Deductible accumulator**: process claims in date order and compute member vs plan share for deductible/coinsurance/OOP max.
3. **835 parser**: sum CLP paid amounts, group CAS adjustments by group code.
4. **ICD-10 validator**: regex `^[A-TV-Z][0-9][0-9AB]\.?[0-9A-TV-Z]{0,4}$`, check against CDC list.
5. **PHI de-identifier**: Safe Harbor on a CSV (hash IDs, generalize dates to year, zip to 3 digits with restrictions).
6. **Duplicate/near-duplicate claim finder**.
7. **LEIE matcher**: fuzzy match names + NPI against exclusion list (`rapidfuzz`).
8. **RAF calculator**: ICD-10 → HCC → score with hierarchy.

## Python skills checklist
Lists/dicts/sets, comprehensions, generators, file I/O, csv/json, datetime, regex, pandas (merge, groupby, window, pivot), numpy basics, requests, pytest, typing, logging, virtualenv, SQLAlchemy, argparse, PySpark basics.
