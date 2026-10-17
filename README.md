# Astrocytic Calcium Imaging and Behavior — Analysis Code

*This repository contains the analysis code for the Cell Reports (2026) manuscript by Paniccia et al. on two-photon astrocytic calcium imaging and behavior during Pavlovian sucrose conditioning. The DOI will be added once it is available.*

## Overview

The code in this repository was used to analyze two-photon calcium imaging of astrocytes and the accompanying mouse behavior (licking) from Pavlovian conditioning experiments. The analyses include auROC-based responses to cues, delta lick rate, signal-detection-theory (SDT) behavioral metrics, cell tracking across days, spatial mapping and cross-correlation of ROIs, and population decoding. Anthropic and OpenAI models were used in code preparation.

## Quick Start

1. Create a Python environment and install the packages listed in `requirements.txt`.
2. Obtain the data (see [What's Not Included](#whats-not-included)) and arrange it as described in `data/README.md`.
3. Set `DATA_ROOT`, either with the `PANICCIA_DATA_ROOT` environment variable or by editing the first code cell of each notebook.
4. Open a notebook in Jupyter and run it top to bottom.

| Notebook | What it does |
|----------------------------------------------------------|-------------------------------------------------------------------------------|
| `notebooks/01_pavlovian_imaging_master.ipynb` | Main imaging analysis: auROC, CS+/CS- discrimination, cell tracking, spatial mapping, cross-correlations, decoding |
| `notebooks/02_imaging_behavior_delta_lickrate_sdt.ipynb` | Delta lick rate and SDT behavioral metrics for the imaging cohort, with independent t-tests between phases |
| `notebooks/03_cbx_auroc_delta_lickrate.ipynb` | auROC and delta lick rate exported to CSV, plus SDT metrics, for the CBX and saline cohorts across acquisition, reversal and omission |

## Repository Structure

```
.
├── notebooks/      ← Jupyter notebooks for the analyses
├── data/           ← Expected data layout (data not included)
├── requirements.txt
└── CHANGELOG.md
```

## Data

The data are not included in this repository. `data/README.md` describes the folder layout each notebook expects. Inputs are MATLAB event logs (`.mat`), extracted signals (`.npy`), ImageJ `RoiSet.zip` files and cell-tracking CSVs. Results and intermediate files are written back under `DATA_ROOT`.

## Required Packages

Python 3 with the packages in `requirements.txt`: numpy, pandas, scipy, scikit-learn, statsmodels, matplotlib, seaborn, joblib, tqdm, shapely, roifile, tensortools, tensorflow, torch, ipython and jupyter.

## What's Not Included

| Excluded | Reason | Available |
|------------------------------------------|---------------------------|-----------|
| Raw and processed imaging and behavior data (`.mat`, `.npy`, ImageJ ROI sets, cell-tracking CSVs) | Data size | On request |
| Generated figures, result tables and intermediate files | Recreated by running the notebooks | n/a |

---

## Citation

If using this code, please cite:

> Paniccia JE et al. *Cell Reports* (2026). DOI to be added.

---

*Last updated: October 2026*
