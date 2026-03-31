# Quantitative Risk Analytics — R & Python

![Python](https://img.shields.io/badge/Python-3.8%2B-blue) ![R](https://img.shields.io/badge/R-ggplot2-276DC3) ![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange) ![License](https://img.shields.io/badge/License-MIT-green)

## Overview

A comprehensive quantitative risk analytics toolkit implementing core financial risk models: CAPM regression for systematic risk decomposition, parametric Value-at-Risk (VaR) at multiple confidence levels, and Conditional Value-at-Risk (CVaR) computation. Automated reporting is produced with professional-grade ggplot2 visualisations.

## Key Features

- **CAPM Regression** — Estimates alpha and beta for systematic vs idiosyncratic risk decomposition
- **Parametric VaR (95% and 99%)** — Gaussian assumption-based daily loss thresholds
- **CVaR / Expected Shortfall** — Captures tail risk beyond VaR
- **Automated ggplot2 Visualisations** — Return distributions, regression plots, and risk dashboards
- **Statistical Reporting** — Summary statistics and model outputs ready for presentation

## Methodology

### 1. CAPM Regression
The Capital Asset Pricing Model is estimated via OLS regression of asset excess returns against market excess returns (FTSE 100 / S&P 500), yielding alpha (abnormal return) and beta (market sensitivity).

### 2. Parametric VaR
Assuming normally distributed returns, VaR is calculated at 95% and 99% confidence levels:

```
VaR = μ - z * σ
```

Where z is the z-score corresponding to the chosen confidence level.

### 3. CVaR (Expected Shortfall)
CVaR is computed as the expected loss conditional on losses exceeding the VaR threshold, providing a more conservative and coherent risk measure.

### 4. Visualisations
All outputs are rendered using ggplot2 (via rpy2 or R kernel), producing publication-quality charts including return distributions with VaR/CVaR overlays and regression scatter plots.

## Technologies Used

| Tool | Purpose |
|------|---------|
| Python 3.8+ | Core computational language |
| R / rpy2 | Statistical modelling and visualisation |
| ggplot2 | Professional chart generation |
| NumPy / Pandas | Data manipulation |
| SciPy | Statistical distributions |
| yfinance | Market data retrieval |
| Jupyter Notebook | Interactive analysis environment |

## Project Structure

```
├── Quantitative_Risk_Analytics.ipynb   # Main analysis notebook
└── README.md
```

## Getting Started

```bash
# Clone the repository
git clone https://github.com/srhimal149/srhimal149-Quantitative-Risk-Analytics-R.git
cd srhimal149-Quantitative-Risk-Analytics-R

# Install Python dependencies
pip install numpy pandas scipy matplotlib yfinance jupyter rpy2

# Ensure R is installed with ggplot2
Rscript -e "install.packages('ggplot2')"

# Launch Jupyter
jupyter notebook
```

## Author

**Md Saifur Rahman Himal**
MSc FinTech (Distinction Candidate) | Quantitative Finance & Risk Analytics
[LinkedIn](https://www.linkedin.com/in/md-saifur-rahman-himal-70a0941ba) | [GitHub](https://github.com/srhimal149)

## License

MIT License — feel free to use and adapt with attribution.
