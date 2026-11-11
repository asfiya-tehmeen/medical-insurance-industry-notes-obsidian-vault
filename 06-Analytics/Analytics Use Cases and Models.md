# Analytics Use Cases and Models

| Use case | Question | Techniques |
|---|---|---|
| Cost drivers / trend | Why is PMPM up? | Price-volume-mix decomposition, cohort analysis |
| High-cost claimant prediction | Who will be in top 5% next year? | Gradient boosting on claims history; AUC, lift |
| Risk stratification | Whom should nurses call? | Logistic regression, calibration, fairness checks |
| Readmission prediction | Who comes back in 30 days? | Classification; features from discharge info |
| Fraud / anomaly detection | Which providers look odd? | Peer-group z-scores, isolation forest, graph analysis |
| Churn / retention | Who will disenroll? | Survival analysis |
| Network optimization | Which providers give best value? | Episode grouping, risk-adjusted cost + quality |
| Rx adherence | Who's not taking meds? | PDC calculation, outreach targeting |
| Prior auth automation | Predict approval to auto-approve | Classification + rules, explainability |
| NLP on notes/letters | Extract diagnoses, summarize appeals | Transformers/LLMs with PHI controls |
| Forecasting claims (IBNR) | How much unpaid? | Chain-ladder, completion factors |
| Member experience | Drivers of low NPS | Text analytics, regression |

## Model governance (compliance angle)
- **Fairness / bias**: don't use race proxies carelessly. A well-known study showed a cost-based risk algorithm under-identified Black patients' needs (Obermeyer et al., Science 2019).
- **Explainability**: denial decisions must be justifiable; regulators (and states) scrutinize AI in UM. 
- **Model risk management**: documentation, validation, monitoring drift, human-in-the-loop.
- **Privacy**: minimum necessary, de-identified training data.

## Episode-of-care / grouping software
ETGs, MEGs, Symmetry, 3M APR-DRG, CMS-HCC, Johns Hopkins ACG. You may implement logic from public specs.

## BI skills
Tableau/Power BI dashboards: PMPM trend, utilization per 1,000, top procedures, denial reasons, provider scorecards. Always state definitions + data freshness on the dashboard.

## Statistics worth knowing
Rates and confidence intervals (small denominators!), regression to the mean, risk adjustment, case-mix, survival curves, lift/gains charts, A/B testing for outreach programs.
