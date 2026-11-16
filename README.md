# Cookie Cats — A/B Test & Player Behavior Analysis

**Product Analytics | Mobile Gaming | A/B Testing | SQL | Python**

## Project Overview

This project analyzes player behavior in *Cookie Cats*, a mobile puzzle game. The main objective is to evaluate the impact of moving the first game gate from level 30 to level 40 on player retention.

The analysis also explores player engagement patterns and identifies opportunities for further product investigation.

data: https://www.kaggle.com/datasets/yufengsui/mobile-games-ab-testing?utm_source=chatgpt.com

## Business Questions

- Does moving the gate from level 30 to level 40 affect player retention?
- Are the differences in D1 and D7 retention statistically significant?
- How are players distributed across activity segments?
- What product opportunities can be identified from player behavior?

## Dataset

The dataset contains **90,189 players** assigned to two experimental groups:

- `gate_30` — control group
- `gate_40` — test group

Main features:
- `userid` — unique player identifier
- `version` — experiment group
- `sum_gamerounds` — number of game rounds played
- `retention_1` — whether the player returned on day 1
- `retention_7` — whether the player returned on day 7

## Tools & Methods

**Python**
- Pandas and NumPy — data preparation and analysis
- Matplotlib and Seaborn — data visualization
- SciPy and Statsmodels — statistical testing and confidence intervals

**SQL**
- Aggregations and GROUP BY
- CASE WHEN — player segmentation
- CTEs — multi-step queries
- Window functions: RANK() and LAG()

**Analytical methods**
- Exploratory Data Analysis (EDA)
- Data quality checks
- A/B test analysis
- Two-proportion z-tests
- Confidence intervals
- Player segmentation

## Key Findings

### 1. A/B Test

| Metric | gate_30 | gate_40 |
|---|---:|---:|
| Players | 44,700 | 45,489 |
| Average game rounds | 52.46 | 51.30 |
| D1 Retention | 44.82% | 44.23% |
| D7 Retention | 19.02% | 18.20% |

The `gate_30` group demonstrated higher retention:

- D1 difference: +0.59 percentage points; not statistically significant.
- D7 difference: +0.82 percentage points; statistically significant (p = 0.0016).

The D7 result remained significant after Bonferroni correction.

### 2. Player Segmentation

Players were divided into five segments based on the total number of game rounds played.

Key observations:
- 48.54% of players belonged to the Very Low and Low activity segments.
- The Very Low segment accounted for 27.41% of all players.
- D7 retention ranged from 1.27% in the Very Low segment to 79.67% in the Very High segment.

This is a descriptive analysis of the relationship between total activity and retention, not an early churn prediction.

## Product Recommendations

1. Keep `gate_30` as the preferred variant when optimizing for D7 retention, based on the observed experiment results.
2. Investigate the first-session experience and early game progression to better understand low-activity players.
3. Run follow-up experiments focused on onboarding and early-level difficulty.
4. Include revenue, in-app purchases, and progression metrics in future analysis to evaluate the broader business impact.

## Limitations

- The dataset does not include timestamps or detailed event logs.
- Revenue and monetization data are unavailable.
- Player segments are based on total activity over the observation period.
- The analysis cannot establish the exact reasons behind retention differences.

## Repository Contents

- `cookie_cats_analysis.ipynb` — complete analysis, visualizations, statistical tests, and SQL queries.
- `data/` — dataset or instructions for accessing it.
- `images/` — selected charts from the analysis.

## How to Run

1. Open the notebook in Google Colab or Jupyter Notebook.
2. Download or provide the Cookie Cats dataset.
3. Install the required Python libraries if they are not already available.
4. Run the notebook cells in order.

## Final Takeaway

The analysis found a statistically significant D7 retention advantage for the `gate_30` group. The results suggest keeping the gate at level 30 when retention is the primary objective, while further investigation of early player engagement and monetization is needed before making a broader product decision.
