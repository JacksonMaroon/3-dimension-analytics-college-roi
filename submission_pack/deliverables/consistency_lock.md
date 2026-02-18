# Consistency Lock (Use This Verbatim)

## Research Question
Which school characteristics are associated with higher median earnings after attendance?

## Main Model Spec
- Baseline: `MD_EARN_WNE_P10 ~ MEDIAN_HH_INC`
- Full: `MD_EARN_WNE_P10 ~ MEDIAN_HH_INC + stem_share + completion_rate + prestige_proxy`
- Prestige proxy: `1 - ADM_RATE`

## Main Model Fit
- Baseline R^2: 0.3400
- Full R^2: 0.5025
- Main sample size: 1,675

## Practical Terms (Full Model)
- +10pp STEM share -> +$3,105
- +10pp completion rate -> +$1,493
- +10pp admission rate -> -$840
- +$10,000 median household income -> +$5,481

## Robustness Check
- Replace prestige proxy with `SAT_AVG`
- SAT model sample: 1,051
- SAT model R^2: 0.6156
- `SAT_AVG` coefficient remains positive and statistically significant

## Language Rules
Use: "we find evidence", "is associated with", "we find no evidence".
Avoid: "proves", "causes", absolute null claims.
