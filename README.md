# Heligman–Pollard Mortality Modeling — Male

Python implementation of the eight-parameter **Heligman–Pollard mortality model** using the **GAM 71 Male mortality table**. This repository presents the code used to explore age-specific mortality patterns, estimate model parameters, and construct mortality intervals through Monte Carlo simulation.

This is a **code-only, Male-specific** version of an undergraduate actuarial science thesis notebook. Saved execution outputs have been removed.

## Overview

The notebook covers:

1. **Mortality data preparation** — loading and organizing age-specific mortality probabilities for ages 0–110.
2. **Descriptive analysis and visualization** — examining the GAM 71 Male mortality pattern.
3. **Parameter sensitivity analysis** — exploring the roles of parameters A–H.
4. **Nonlinear Least Squares (NLS) estimation** — estimating the Heligman–Pollard parameters using a Gauss–Newton approach with logarithmic residuals.
5. **Parameter uncertainty** — obtaining the covariance matrix of the estimated parameters.
6. **Monte Carlo simulation** — checking numerical stability and generating parameter realizations.
7. **Mortality intervals** — constructing lower and upper mortality estimates from simulated mortality probabilities.

## Model

The eight-parameter Heligman–Pollard model is represented in this notebook as:

```text
q(x) = A^((x+B)^C)
     + D * exp(-E * (ln(x/F))^2)
     + (G * H^x) / (1 + G * H^x)
```

The components describe childhood mortality, the young-adult accident hump, and increasing mortality at older ages. The implementation includes numerical handling for age zero.

## Repository contents

```text
TA_Heligman_Pollard_Male_GitHub.ipynb   # Main notebook
README.md                               # Project documentation
```

## Requirements

- Python 3
- Jupyter Notebook or Google Colab
- `numpy`
- `pandas`
- `matplotlib`
- `scipy`
- `numba`
- `openpyxl` (to read the Excel input)

Install the packages in a local Python environment with:

```bash
pip install numpy pandas matplotlib scipy numba openpyxl notebook
```

## Input data

The notebook expects an Excel workbook named:

```text
TA26-Mortality Table.xlsx
```

The workbook must contain these columns:

| Column | Description |
| --- | --- |
| `Age` | Age |
| `GAM71-m` | GAM 71 Male mortality probability |

Place the workbook in the notebook's working directory before running the code. **The input workbook is not included in this repository.** Only upload it separately if you have permission to redistribute the data.

## How to run

1. Download or clone the repository.
2. Open `TA_Heligman_Pollard_Male_GitHub.ipynb` in Jupyter Notebook or Google Colab.
3. Install the required Python packages.
4. Supply the Excel input workbook in the notebook's working directory.
5. Run the cells in order, from data preparation through estimation and simulation.

> **Computational note:** The Monte Carlo sections can require substantial processing time and memory resources due to the number of simulations. Review the simulation settings before running them.

## Outputs

When executed with the required data, the notebook includes code to produce parameter estimates, numerical diagnostics, mortality plots, Monte Carlo convergence information, and mortality interval results. **No precomputed notebook outputs are stored in this public version.** Some cells save figures or Excel files when run.

## Scope and limitations

- The repository contains the **Male** mortality modeling workflow only; it does not include the Female workflow or pension participant-level valuation data.
- The GAM 71 mortality table is treated as an external input.
- This GitHub edition was adapted for publication and **has not been re-executed end-to-end after editing**.
- Mortality intervals in this notebook describe uncertainty propagated from estimated model parameters; they should not be interpreted as a guarantee of future mortality outcomes.

## Academic context

This notebook forms part of an undergraduate actuarial science thesis on **mortality interval estimation using the Heligman–Pollard model for pension liability valuation**. The public repository focuses on the computational mortality-modeling workflow rather than the full pension valuation application.

## References

- Heligman, L., & Pollard, J. H. (1980). *The age pattern of mortality*. Journal of the Institute of Actuaries, 107(1), 49–80.
- Sharrow, D. J., Clark, S. J., Collinson, M. A., Kahn, K., & Tollman, S. M. (2013). *The age pattern of increases in mortality affected by HIV: Bayesian fit of the Heligman–Pollard model to data from the Agincourt HDSS field site in rural northeast South Africa*. Demographic Research, 29, 1039–1096.

## Usage

The code is shared for academic learning and reproducibility. Please acknowledge the original mortality-modeling literature if you adapt the methodology. No open-source license is declared in this repository unless a separate `LICENSE` file is added.
