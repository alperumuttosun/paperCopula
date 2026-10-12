
# Synthetic country-year crop-yield panels: code, data and results

Code and data for "Statistical Fidelity in Synthetic Country-Year Panels: Structural Failures versus Finite-Sample Artifacts".

## You do not need to run the code

The full pipeline takes a long time. All numbers in the paper are already in the Excel files in `results/`, and the figures are in `figures/`. Open the Excel files to check any table or number. Step 00 (data construction) is included only to document how the panels were built; please do not run it.

## Folders

| Folder | Content |
|---|---|
| `code/` | R scripts (steps below) |
| `data/` | `panelv7_<crop>.xlsx`, one country-year panel for each of the 8 crops |
| `results/` | `copulapaper_results.xlsx` (all results, Steps 01-09), `multivar_fidelity_results.xlsx` (Step 10) |
| `figures/` | Figures 1-4 of the paper (PDF) |

## What each step does

| Step | Script | What it does |
|---|---|---|
| 00 | end of `copulastep1-9.R` | How the panels were built from raw data (documentation only, do not run) |
| 01 | `copulastep1-9.R` | Loads the panels and computes the real-data reference statistics |
| 02 | `copulastep1-9.R` | Pooled Gaussian copula (negative control): generates 50 synthetic panels per crop |
| 03 | `copulastep1-9.R` | Country-conditioned Gaussian AR(1) generator, called CC-AR(1) in the paper: 50 panels per crop |
| 04 | `copulastep1-9.R` | Moving block bootstrap (MBB): 50 panels per crop |
| 05 | `copulastep1-9.R` | Temporal holdout: fit on 1961-2014, compare with 2015-2024 |
| 06 | `copulastep1-9.R` | Confidence intervals over seeds and the master results table |
| 07 | `copulastep1-9.R` | Does fidelity depend on history length? Noise floor, bias-corrected phi, within-country variance, descriptive statistics |
| 08 | `copulastep1-9.R` | Holdout as a distribution (CRPS, coverage) and the downstream within-country regression |
| 09 | `copulastep1-9.R` | Collects all results into `copulapaper_results.xlsx` |
| 10 | `copulastep_multivar.R` | Fidelity of all four variables (multivariate table), writes `multivar_fidelity_results.xlsx` |
| 11 | `variance_check.R` | Expected within-country variance ratio of an AR(1) series (finite-sample check) |

## Paper figures

| Figure | File |
|---|---|
| 1 | `step2_fig1_between_country_pooled.pdf` |
| 2 | `step4_fig1_acf1_three_generators.pdf` |
| 3 | `step8c_fig1_holdout_distribution.pdf` |
| 4 | `step7_fig1_acf_error_by_history_length.pdf` |

## If you still want to run it

Requires R with the packages `readxl` and `writexl`. Put the `data/` files in one folder and set `base_dir1` at the top of each script to that folder. Run `copulastep1-9.R` in one R session (Steps 01-09 depend on each other). Random seeds are fixed, so a rerun reproduces the same numbers.
