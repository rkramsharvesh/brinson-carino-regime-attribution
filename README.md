# Regime-Conditioned Performance Attribution

**Paper:** Quality Selection Earns Defensive Alpha: Regime-Conditioned Brinson Attribution Evidence  
**Author:** Ram Sharvesh Ramasamy Kumar

## Overview

This project develops a regime-conditioned Brinson-Carino attribution framework
that decomposes allocation and selection effects across market regimes identified
by a Hidden Markov Model. The allocation signal uses STREV-residualized industry
momentum across twelve Fama-French industries. The selection signal applies a
value-weighted within-industry gross profitability screen following Novy-Marx (2013).

The principal finding is that the defensive quality premium operates through the
Brinson selection channel rather than the allocation channel. Within-industry
GP/Assets screening generates +18,047 basis points of out-of-sample selection
alpha (2004-2024), concentrated in Transitional and Bear regime months.
Momentum-based allocation contributes near-zero alpha in the same period,
consistent with Ehsani and Linnainmaa (2022).

### The Full writeup and findings are available on my Substack page 
https://ramsharvesh.substack.com/p/quality-selection-earns-defensive

## Repository Structure

```
notebooks/
    Notebook_1_Data_Loading.ipynb     # Data ingestion and cleaning
    Notebook_2_Diagnostics.ipynb      # Eight pre-implementation diagnostic checks
    Notebook_3_Research.ipynb         # Full attribution pipeline and results
outputs/
    regime_posteriors_monthly.parquet # Cached HMM posteriors (2+ hour computation)
```

## Data Requirements

This project uses licensed data that cannot be redistributed. You will need:

- CRSP Monthly Stock File via WRDS (CIZ V2 format, 1990-2024)
- Compustat Annual Fundamentals via WRDS (1989-2026)
- CRSP-Compustat Linking Table via WRDS
- Ken French Data Library (FF12 returns, FF5 factors, STREV factor) — free
- FRED (VIX daily, NBER recession indicator) — fetched automatically in code

Once you have the data files, update the ROOT variable in Notebook 1 Cell 1 to
point to your local folder.

## How to Run

Run the notebooks in order. Notebooks 1 and 2 only need to run once.
Notebook 3 produces all tables and figures in the paper.

The walk-forward HMM in Notebook 3 Cell 8 takes over two hours on a standard CPU.
The results are cached to outputs/regime_posteriors_monthly.parquet. If this file
exists, the cell loads it in under a second and skips the computation entirely. The
cached file is included in this repository.

## Dependencies

```bash
pip install pandas numpy hmmlearn scikit-learn matplotlib seaborn scipy statsmodels
```

## Citation

If you use this code or methodology, please cite the accompanying paper.
