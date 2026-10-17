# Concrete Strength Analysis

Project 1. Authors: Yuan Fan, Ezra Lin, Rong Bao.

## Structure

```text
concrete_strength_analysis/
├── README.md
├── Project 1 Section 1.Rmd
├── concrete+compressive+strength/
│   ├── Concrete_Data.xls
│   ├── Concrete_Readme.txt
│   └── README.md
└── projects_results/
```

`Project 1 Section 1.Rmd` is the only analysis code file.

## Environment

The analysis requires R, readxl, and knitr, along with standard R packages. Rendering a Word document additionally requires rmarkdown and Pandoc. The included results were generated with R 4.6.1, readxl 1.5.0.1, and knitr 1.51; see `projects_results/sessionInfo.txt` for the recorded environment. Package versions are not pinned by a lockfile.

Install missing packages if needed:

```r
install.packages(c("readxl", "knitr", "rmarkdown"))
```

## Run in order

1. Clone or download this repository, then open an R session with the repository root as its working directory. This is the folder containing `README.md` and `Project 1 Section 1.Rmd`.
2. Confirm the working directory and input file in the **R console**:

```r
getwd()
file.exists("Project 1 Section 1.Rmd")
file.exists("concrete+compressive+strength/Concrete_Data.xls")
```

Both `file.exists()` checks should return `TRUE`. If needed, use `setwd()` with the location where you cloned or downloaded the repository. Replace the example path below with your own local path:

```r
setwd("/path/to/concrete_strength_analysis")
```

Opening the `.Rmd` file alone does not necessarily change an existing R session's working directory.

With this working directory, the relative input path `concrete+compressive+strength/Concrete_Data.xls` and output directory `projects_results` both resolve inside this project.

3. Install any missing packages using the command in **Environment** above.
4. Open `Project 1 Section 1.Rmd`, run the setup chunk, then run sections 1.1 through 1.7 in order. Wait for each section to finish before starting the next; section 1.6 (Q6) performs up to one million updates for each of eight models.

All exports use the relative directory `projects_results`. Running again overwrites matching result files. Q7 reassigns variables, so restart from data preparation when rerunning earlier experiments.

To run the entire document and render a Word report instead, execute this command from the repository root (Pandoc must be available):

```r
rmarkdown::render("Project 1 Section 1.Rmd", output_dir = "projects_results")
```

Rendering executes all code chunks, including the tutorial examples, and overwrites matching analysis outputs.

## Included results

The `projects_results/` directory contains 18 files from a completed Q1–Q7 analysis run:

| Files | Purpose |
| --- | --- |
| Figure1_Scaling.png | Raw versus standardized GD loss |
| Figure2_Transformations.png | Raw, standardized, and logarithmic GD loss |
| Q3_GD_Results.csv | Raw and standardized GD settings and final metrics |
| Q3_Loss_History.csv | Raw and standardized loss sequences |
| Q3_Q5_GD_Results.csv | All three multivariate GD configurations and scores |
| Q3_Q5_Loss_History.csv | All three multivariate loss sequences |
| Q4_Scaling_Optimal_Results.csv | Optimal raw and standardized training scores |
| Q4_Fitted_Difference.csv | Maximum fitted-value difference |
| Q5_Model_Performance.csv | Train/test MSE and R² for optimal models |
| Optimal_Model_Coefficients.csv | Estimates, standard errors, t statistics, p-values |
| Q6_2_Coefficients.csv | Univariate versus multivariate slopes |
| Q6_Training_Results.csv | Univariate GD diagnostics |
| Q6_Optimal_Univariate_Results.csv | Optimal univariate training scores |
| Q7_P_Values.csv | Three configurations' p-values |
| Training_Feature_Correlations.csv | Training predictor correlations |
| Training_Scaling_Parameters.csv | Training means and standard deviations |
| sessionInfo.txt | Recorded analysis environment |
| Run_Plots.pdf | Plots captured by the execution session |

`Run_Plots.pdf` was captured by the execution session's PDF graphics device, rather than an export statement in the R Markdown. The named PNG and CSV outputs are exported by the R Markdown itself.

## Data and methods

The prescribed split uses original observations 501–630 for testing and the remaining 900 for training. Training-only means and standard deviations scale the features. Custom full-batch gradient descent minimizes MSE; optimal least-squares models and inference use `lm()`. See the R Markdown for all learning rates, iteration budgets, transformations, and export steps.

Dataset attribution and reuse information are provided in `concrete+compressive+strength/Concrete_Readme.txt`. Retain this file with the dataset. No code license has been selected.
