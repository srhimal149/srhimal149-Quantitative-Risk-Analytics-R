# Quantitative Risk Analytics — R

![R](https://img.shields.io/badge/R-IRkernel-276DC3) ![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange) ![License](https://img.shields.io/badge/License-MIT-green)

## Overview

A quantitative risk analytics project implemented entirely in **R** (via IRkernel in Jupyter). It applies CAPM regression, parametric and historical VaR, and CVaR to **ASC.L** (ASOS) and **AV.L** (Aviva) benchmarked against the **FTSE 100**, with automated ggplot2 visualisations throughout.

Data is sourced via `quantmod` from Yahoo Finance (Jul 2024 – May 2025, ~259 trading days).

---

## What's Inside

### Section 1: Setup & Library Imports
Installs and loads: `quantmod`, `PerformanceAnalytics`, `ggplot2`, `tidyverse`, `quadprog`

### Section 2: Data Download
Downloads adjusted close prices for **ASC.L** (ASOS) and **AV.L** (Aviva) plus **FTSE** benchmark using `getSymbols()` from `quantmod`.

### Section 3: Return & Excess Return Calculation
- Computes daily returns using `mutate()` with lagged prices
- - Calculates excess returns using `rf_annual = 0.045` (4.5% risk-free rate)
  - - Produces a clean tibble with 7 columns (date, raw returns, excess returns) × 259 rows
   
    - ### Section 4: CAPM Model Implementation
    - Full CAPM theory markdown with formula:
    - ```
      E(Ri) = Rf + βi(E(Rm) - Rf)
      Ri - Rf = αi + βi(Rm - Rf) + εi
      ```
      OLS regression via `lm()` for each stock:
      - `beta_asc = coef(lm(ASC_excess ~ Market_excess))[2]`
      - - `beta_av = coef(lm(AV_excess ~ Market_excess))[2]`
        - - Computes CAPM-implied expected returns for ASC and AV
         
          - ### Section 5: Parametric VaR (95% & 99%)
          - Uses the Gaussian assumption:
          - ```
            VaR = μ - z * σ
            ```
            Computed for both stocks at 95% and 99% confidence.

            ### Section 6: CVaR / Expected Shortfall
            Computes the mean of returns below the VaR threshold for each confidence level.

            ### Section 7: ggplot2 Visualisations
            - Return distribution histograms with VaR/CVaR overlaid
            - - CAPM regression scatter plots
              - - Correlation plots
               
                - ---

                ## Technologies Used

                | Tool | Purpose |
                |------|---------|
                | R (IRkernel) | Core language — pure R notebook |
                | quantmod | Yahoo Finance data download |
                | ggplot2 | Professional visualisations |
                | tidyverse (dplyr, tibble) | Data wrangling |
                | PerformanceAnalytics | Risk metric utilities |
                | Jupyter Notebook | Interactive execution via IRkernel |

                > **Note:** This notebook runs R natively via IRkernel, not Python with rpy2. You need R and the IRkernel installed to execute it.
                >
                > ## Getting Started
                >
                > ```r
                > # In R, install required packages
                > install.packages(c("quantmod", "PerformanceAnalytics", "ggplot2", "tidyverse"))
                >
                > # Install IRkernel for Jupyter
                > install.packages("IRkernel")
                > IRkernel::installspec()
                > ```
                >
                > Then launch Jupyter and select the R kernel to run the notebook.
                >
                > ```bash
                > git clone https://github.com/srhimal149/srhimal149-Quantitative-Risk-Analytics-R.git
                > jupyter notebook
                > ```
                >
                > ## Author
                >
                > **Md Saifur Rahman Himal**
                > MSc FinTech (Distinction Candidate) | Quantitative Finance & Risk Analytics
                > [LinkedIn](https://www.linkedin.com/in/md-saifur-rahman-himal-70a0941ba) | [GitHub](https://github.com/srhimal149)
                >
                > ## License
                >
                > MIT License
