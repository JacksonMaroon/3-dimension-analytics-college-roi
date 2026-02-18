# Regression Methods Report Draft

## 1. Research Design
Research question: Which college characteristics are associated with higher median earnings after attendance?  
Unit of analysis: U.S. higher-education institutions.  
Data source: U.S. Department of Education College Scorecard (most recent institution cohort file).  
Modeling sample: 1,675 institutions after dropping rows with missing model variables for the main model.  
Filters/exclusions: Rows missing `MD_EARN_WNE_P10`, `MEDIAN_HH_INC`, `stem_share`, `completion_rate`, or `ADM_RATE` were excluded.

## 2. Model Specification
Model type: OLS linear regression.  
Dependent variable: `MD_EARN_WNE_P10`.  
Baseline model: `MD_EARN_WNE_P10 ~ MEDIAN_HH_INC`.  
Full model: `MD_EARN_WNE_P10 ~ MEDIAN_HH_INC + stem_share + completion_rate + prestige_proxy`.  
Transformations:
- `stem_share` built as sum of STEM program share columns (`PCIP11`, `PCIP14`, `PCIP15`, `PCIP26`, `PCIP27`, `PCIP40`, `PCIP41`).
- `completion_rate` uses `C150_4` with fallback to `C150_L4`.
- `prestige_proxy = 1 - ADM_RATE`.

Model selection logic: baseline gives a simple control model; full model adds school characteristics and a prestige proxy.

## 3. Assumption Testing and Diagnostics
Linearity:
- Visual check used via scatter with fit line for earnings vs STEM share.

Homoscedasticity (Breusch-Pagan on full-model residuals):
- LM stat = 35.09, LM p-value = 4.45e-07
- F stat = 8.93, F p-value = 3.89e-07
- Interpretation: evidence of heteroskedasticity.

Normality (Shapiro-Wilk on full-model residuals):
- W = 0.9154, p-value = 1.31e-29
- Interpretation: residuals are not normally distributed.

Multicollinearity (VIF):
- `MEDIAN_HH_INC`: 1.27
- `stem_share`: 1.11
- `completion_rate`: 1.34
- `prestige_proxy`: 1.17
- Interpretation: multicollinearity is low.

Autocorrelation (Durbin-Watson):
- 1.795
- Interpretation: no strong autocorrelation concern in this cross-sectional setup.

Robust standard errors (HC3):
- `MEDIAN_HH_INC`: coef 0.55, HC3 SE 0.03, p < 0.001
- `stem_share`: coef 31,047.01, HC3 SE 2,531.40, p < 0.001
- `completion_rate`: coef 14,928.09, HC3 SE 2,537.18, p < 0.001
- `prestige_proxy`: coef 8,399.37, HC3 SE 1,607.06, p < 0.001
- Interpretation: key coefficient signs and significance remain stable under robust SE.

## 4. Limitations and Robustness
Main limitations:
- Observational design; causal claims are not identified.
- Missing admission-rate values reduce sample size.
- Potential omitted variables (institution quality dimensions not captured here).

Completed robustness checks:
- HC3 robust standard errors for the full model.
- Alternate prestige measure: replaced `prestige_proxy` with `SAT_AVG`.
  - SAT model sample size: 1,051
  - SAT model R^2: 0.6156
  - `MEDIAN_HH_INC`: coef 0.4382, HC3 SE 0.0340, p < 0.001
  - `stem_share`: coef 27,190.2370, HC3 SE 3,083.7108, p < 0.001
  - `completion_rate`: coef 18,368.8339, HC3 SE 3,646.7416, p < 0.001
  - `SAT_AVG`: coef 21.7617, HC3 SE 5.0364, p < 0.001

Optional additional checks:
- Sensitivity check excluding top 1% of earnings values.
