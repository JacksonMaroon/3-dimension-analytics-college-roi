# Group 3: 3 Dimension Analytics Working Idea

## Project Focus

We are studying return on investment (ROI) of college by identifying which institutional characteristics are most predictive of post-college earnings.

## Research Question

Across U.S. colleges, what school characteristics best predict median earnings after attendance?

## Working Hypothesis

- The strongest predictor of median earnings after attendance will be STEM share.
- Schools with higher STEM share will have higher median earnings 10 years later.
- School status (for example private institutions and high-prestige institutions) and location will also be major contributors.

## Theory

- **Human capital theory**: completing a degree and gaining in-demand skills (especially STEM) should increase worker productivity and wages.
- **Labor market signaling theory**: institutional prestige can signal ability to employers and boost wages independent of other factors.

## Client

A university career office that wants to understand which aspects of college experience or university characteristics are linked to higher salaries after graduation.

Potential value to client:
- Improve student recruitment messaging
- Support data-driven strategic decisions
- Potentially improve alumni outcomes and long-term donations

## Controls

We plan to control for family income, since prior research suggests it is among the strongest predictors of post-graduation income.

## Data Source

- U.S. Department of Education **College Scorecard**
- https://collegescorecard.ed.gov/data/

## Project Setup (Python/Jupyter)

1. Put this file in `data/raw/`:
   - `Most-Recent-Cohorts-Institution.csv`
2. Open notebook:
   - `notebooks/01_college_roi_baseline.ipynb`
3. Run top to bottom.

The notebook will:
- build a simple `stem_share` variable from selected `PCIP*` fields
- run a baseline model with family-income controls and location
- run a full model adding STEM share, control/type, and completion rate

## Variables Used (First Pass)

- Outcome: `MD_EARN_WNE_P10`
- Family-income controls: `MEDIAN_HH_INC`, `PCTPELL`
- Location: `REGION`, `LOCALE`, `STABBR`
- School status/type: `CONTROL`
- Completion: `C150_4`, `C150_L4`
- STEM mix (for `stem_share`): `PCIP11`, `PCIP14`, `PCIP15`, `PCIP26`, `PCIP27`, `PCIP40`, `PCIP41`

## Current Next Steps

1. Identify exact Scorecard variables for outcome, predictors, and controls.
2. Build baseline model with family income control.
3. Add STEM share, school type/status, and location variables.
4. Compare effect sizes to identify strongest predictors.
5. Summarize findings for career office decision-making.
