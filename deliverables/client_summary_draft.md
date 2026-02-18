# Client Summary Draft: College ROI Predictors

## Project Context
Client: University Career Office  
Question: Which school characteristics are most associated with higher median earnings after attendance?

## Data and Method
- Data source: U.S. Department of Education College Scorecard (most recent institution cohort file).
- Sample used in modeling: 1,675 institutions.
- Outcome variable: `MD_EARN_WNE_P10` (median earnings after attendance).
- Baseline model: `MEDIAN_HH_INC` only.
- Full model: `MEDIAN_HH_INC`, `stem_share`, `completion_rate`, `prestige_proxy` where `prestige_proxy = 1 - ADM_RATE`.

## Main Findings
- Model fit improved from baseline to full model:
  - Baseline R^2 = 0.3400
  - Full R^2 = 0.5025
  - Gain = +0.1625
- Full model key coefficients:
  - `stem_share`: +31,047.01
  - `completion_rate`: +14,928.09
  - `MEDIAN_HH_INC`: +0.55
  - `prestige_proxy`: +8,399.37

## Practical Interpretation for Career Office
- Institutions with stronger STEM concentration are associated with higher post-attendance earnings.
- Higher completion rates are also associated with stronger earnings outcomes.
- Earnings remain tied to socioeconomic context (`MEDIAN_HH_INC`).
- More selective schools (lower admission rates) are associated with higher earnings via the prestige proxy.

## Limits and Cautions
- Findings are associational, not causal.
- Sample size drops due to missing `ADM_RATE` values.
- Omitted-variable risk remains.

## Next Steps
1. Add one alternate prestige specification (for example `SAT_AVG`) as a robustness check.
2. Prepare one regression-table slide and one implications slide for the client audience.
3. Finalize methods report diagnostics and limitations language.
