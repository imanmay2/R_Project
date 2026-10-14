# HumanFactor: Statistical Analysis of Sleep, Lifestyle and Academic Performance

BMAT202P Probability and Statistics Lab — mini-project, implemented in R (Jupyter Notebook, IRkernel).

**Status: first milestone (~30–40% of the complete project).** Experiments 1–3 of the 11-experiment BMAT202P syllabus are completed; Experiment 4 (multiple linear regression) has a preliminary Phase-1 model only; Experiments 5–11 are mapped and planned, not implemented. See `notebooks/HumanFactor_Analysis.ipynb` for the full analysis and `outputs/tables/experiment_coverage_matrix.csv` for the honest status of every experiment.

## Dataset

- File: `data/raw/student_lifestyle_dataset.csv` (preserved unmodified)
- Source: Kaggle — secondary data, not personally collected
- 2000 students, 8 columns: `Student_ID`, `Study_Hours_Per_Day`, `Extracurricular_Hours_Per_Day`, `Sleep_Hours_Per_Day`, `Social_Hours_Per_Day`, `Physical_Activity_Hours_Per_Day`, `GPA`, `Stress_Level`

## Directory structure

```
HumanFactor/
├── data/
│   ├── raw/           original Kaggle CSV (never modified)
│   ├── processed/      type-corrected and cleaned CSVs produced by the notebook
│   └── auxiliary/      reserved for a future auxiliary dataset (Experiments 5-11, if required)
├── notebooks/
│   └── HumanFactor_Analysis.ipynb   the executed R notebook (this milestone)
├── outputs/
│   ├── figures/        11 saved PNG plots
│   ├── tables/         7 saved CSV result tables
│   └── statistical_results/  reserved for Experiments 5-11
├── report/
│   └── Mini_Thesis_Outline.md
├── presentation/
│   └── Demo_Presentation_Outline.md
└── README.md
```

## Environment

Created as a dedicated conda environment `humanfactor` (R 4.5.3 + IRkernel + tidyverse, janitor, psych, corrplot, GGally, gridExtra, knitr, kableExtra, scales, jupyterlab).

To re-run:
```
conda activate humanfactor
cd notebooks
jupyter nbconvert --to notebook --execute --inplace HumanFactor_Analysis.ipynb
```

## Key results from this milestone (actual, computed)

- `Study_Hours_Per_Day` has the strongest linear association with `GPA` among all lifestyle variables (Pearson r ≈ 0.73).
- Simple linear regression `GPA ~ Study_Hours_Per_Day`: R² ≈ 0.54.
- Preliminary multiple regression `GPA ~ all 5 lifestyle-hour variables`: Multiple R² ≈ 0.541, Adjusted R² ≈ 0.540 — only a marginal improvement over the single-predictor model, consistent with the five hour-variables being mechanically constrained to sum to 24 hours/day (documented in the notebook's Data Quality Assessment and Limitations sections).

No causal claims are made anywhere in this project — the dataset is observational and cross-sectional.

## Next phase

Finalize Experiment 4 (multicollinearity diagnostics, model refinement) and implement Experiments 5–11 following the plan in `outputs/tables/experiment_coverage_matrix.csv`, sourcing a legitimate auxiliary dataset where the main dataset cannot support a required design (Binomial, Poisson, paired t-test, RBD, Latin Square).
