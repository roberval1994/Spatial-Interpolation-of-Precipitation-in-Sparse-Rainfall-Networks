# Spatial Interpolation of Precipitation in Sparse Rainfall Networks

**A Comparative Evaluation of IDW, Kriging, and Splines in South American Contexts**

🌐 **Language / Idioma:** **English** | [Português](README.pt-BR.md)

---

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-research-blueviolet.svg)]()

> Part of the PhD research in Operational Research at **UNIFESP / ITA**.
> See the research overview: [PhD-Research-Operational-Research](https://github.com/roberval1994).

## Overview

This project provides a reproducible comparison of three classical spatial
interpolation methods — **Inverse Distance Weighting (IDW)**, **Ordinary Kriging**,
and **Splines** — applied to the estimation of precipitation fields in regions with
**sparse rain-gauge coverage**, a common and challenging scenario across South America.

The goal is to quantify how each method behaves when stations are few and unevenly
distributed, and to provide practical guidance on method selection under data scarcity.

## Motivation

Reliable precipitation surfaces are a prerequisite for hydrological modelling, flood
risk assessment, and water-resource management. In many South American basins the
monitoring network is sparse, which amplifies interpolation error and makes the choice
of method consequential. This study evaluates that choice systematically.

## Methods

| Method | Family | Key property |
|---|---|---|
| **IDW** | Deterministic | Simple, no assumptions on spatial structure |
| **Ordinary Kriging** | Geostatistical | Models spatial autocorrelation via the variogram, provides uncertainty |
| **Splines** | Deterministic (smoothing) | Smooth surfaces, sensitive to tension parameters |

Evaluation uses **leave-one-out / k-fold cross-validation** with the following metrics:
**MAE**, **RMSE**, and bias. Variogram parameters (nugget, sill, range) are fitted and
reported per dataset.

## Repository structure

```
.
├── notebooks/
│   ├── interpolation_test.ipynb              # Core comparison IDW vs Kriging vs Splines
│   ├── Interpolation_Month.ipynb             # Monthly aggregation experiments
│   └── analise_estatistica_complementar.ipynb# Complementary statistical analysis
├── data/                                     # Rain-gauge datasets (see Data section)
├── outputs/                                  # Figures, variograms, metric tables
├── requirements.txt
├── LICENSE
├── README.md                                 # English (this file)
└── README.pt-BR.md                           # Portuguese
```

## Data

The study uses rainfall station data from several South American sources, organised by
region (São José dos Campos, Rio de Janeiro, São Paulo, Uruguay, among others). Each
dataset contains station coordinates and precipitation records used as the ground truth
for cross-validation.

> Data files are included in `data/`. Large archives are provided compressed.

## Getting started

```bash
# 1. Clone
git clone https://github.com/roberval1994/Spatial-Interpolation-of-Precipitation-in-Sparse-Rainfall-Networks.git
cd Spatial-Interpolation-of-Precipitation-in-Sparse-Rainfall-Networks

# 2. Create an environment and install dependencies
python -m venv .venv
# Windows
.venv\Scripts\activate
# Linux / macOS
# source .venv/bin/activate
pip install -r requirements.txt

# 3. Launch Jupyter
jupyter notebook
```

## Key results

- Systematic cross-validated comparison of IDW, Kriging, and Splines under sparse-network conditions.
- Fitted variogram models per dataset (nugget, sill, range).
- Sensitivity analysis of the search radius / number of neighbours.

See the `outputs/` folder for generated figures and metric tables.

## Tech stack

`Python` · `NumPy` · `pandas` · `SciPy` · `scikit-learn` · `PyKrige` · `GeoPandas` · `Matplotlib`

## Citation

If you use this work, please cite:

```bibtex
@misc{moreirafilho_spatial_interpolation,
  author       = {Moreira Filho, Roberval Gon{\c c}alves},
  title        = {Spatial Interpolation of Precipitation in Sparse Rainfall
                  Networks: A Comparative Evaluation of IDW, Kriging, and Splines
                  in South American Contexts},
  year         = {2026},
  howpublished  = {\url{https://github.com/roberval1994/Spatial-Interpolation-of-Precipitation-in-Sparse-Rainfall-Networks}}
}
```

## Author

**Roberval Gonçalves Moreira Filho**
Data Scientist | Operational Research Analyst — PhD candidate, UNIFESP/ITA

[![Email](https://img.shields.io/badge/Email-roberval.researcher.or%40outlook.com-red)](mailto:roberval.researcher.or@outlook.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-robervalOr-blue)](https://www.linkedin.com/in/robervalOr)
[![GitHub](https://img.shields.io/badge/GitHub-roberval1994-black)](https://github.com/roberval1994)

## License

Released under the MIT License. See [LICENSE](LICENSE).
