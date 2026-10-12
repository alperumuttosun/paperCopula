# Code and data for "Statistical Fidelity in Synthetic Country-Year Panels: Structural Failures versus Finite-Sample Artifacts".

Random seeds are fixed, so a rerun reproduces the numbers reported in the paper.

Step 00 (how the panels were built from raw data) is included only to document the data source. Do not run Step 00: the panels it produces are already provided in `data/`.

## Folders

| Folder | Content |
|---|---|
| `code/` | R scripts (steps below) |
| `data/` | `panelv7_<crop>.xlsx`, one country-year panel for each of the 8 crops |
| `figures/` | Figures 1-4 of the paper (PDF) |

## What each step does

| Step | Script | What it does | Run it? |
|---|---|---|---|
| 00 | end of `copulastep1-9.R` | How the panels were built from raw data | No (documentation only) |
| 01 | `copulastep1-9.R` | Loads the panels and computes the real-data reference statistics | Yes |
| 02 | `copulastep1-9.R` | Pooled Gaussian copula (negative control): generates 50 synthetic panels per crop | Yes |
| 03 | `copulastep1-9.R` | Country-conditioned Gaussian AR(1) generator, called CC-AR(1) in the paper: 50 panels per crop | Yes |
| 04 | `copulastep1-9.R` | Moving block bootstrap (MBB): 50 panels per crop | Yes |
| 05 | `copulastep1-9.R` | Temporal holdout: fit on 1961-2014, compare with 2015-2024 | Yes |
| 06 | `copulastep1-9.R` | Confidence intervals over seeds and the master results table | Yes |
| 07 | `copulastep1-9.R` | Does fidelity depend on history length? Noise floor, bias-corrected phi, within-country variance, descriptive statistics | Yes |
| 08 | `copulastep1-9.R` | Holdout as a distribution (CRPS, coverage) and the downstream within-country regression | Yes |
| 09 | `copulastep1-9.R` | Collects all results into `copulapaper_results.xlsx` | Yes |
| 10 | `copulastep_multivar.R` | Fidelity of all four variables (multivariate table), writes `multivar_fidelity_results.xlsx` | Yes |
| 11 | `variance_check.R` | Expected within-country variance ratio of an AR(1) series (finite-sample check) | Yes |

## Paper figures

| Figure | File |
|---|---|
| 1 | `step2_fig1_between_country_pooled.pdf` |
| 2 | `step4_fig1_acf1_three_generators.pdf` |
| 3 | `step8c_fig1_holdout_distribution.pdf` |
| 4 | `step7_fig1_acf_error_by_history_length.pdf` |
