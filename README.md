# GenomeAnalysis_KineticModel
Genome-wide analysis of sequence-based data and a kinetic model of gene activation, applied to zygotic genome activation.

Code for genome-wide bioinformatics analysis of sequencing-based data and a
three-state kinetic model relating transcriptional cluster association to gene
activation in zebrafish embryos.

## Overview

This repository integrates genome-wide sequencing data (ChIP-seq, ATAC-seq, BS-seq,
RNA-seq, Hi-C) to characterize how genes interact
with RNA Polymerase II (Pol II) transcriptional clusters during early zebrafish
development. It also implements a three-state Markov model of gene activation,
used to compare candidate regulatory scenarios against the sequencing-based data.

## Contents

The main analysis is documented in the Jupyter notebook
`analysing_zga_genome.ipynb`, organized into the following stages:

- **Gene annotation** — reference dataframe of zebrafish genes (NCBI RefSeq).
- **RNA-seq** — per-gene expression values.
- **Sequence-based data** Signal tracks, coverage, Hi-C interaction and derived quantities for the zebrafish genome, around ~4 hpf. Includes analysis of: Pol II Ser5P, H3K27ac, H3K4me3, ATAC-seq, BS-seq,
  Nanog, Pou5f3, Sox19b, Pol II Ser5P, ROSE super-enhancers and optionally other regulatory elements.
- **Visualization** — Visualize correlations and patterns using genome-wide heatmaps, gene-specific/grouped signal plots,
  RNA expression, and Hi-C data.
- **Three-state kinetic model** — a continuous-time Markov model
  (Inactive ↔ Cluster associated ↔ Transcribing), parameter screening, and comparison against
  the sequencing-based data via pattern similarity.
- **Comparison with imaging-based data** — correlating gene–cluster distance
  (from oligopaint microscopy) with the sequencing-based signals.

## Key packages

Beyond the standard pandas / numpy / matplotlib / scipy stack:

| Package | Used for |
|---|---|
| [`hicstraw`](https://github.com/aidenlab/straw) | Reading Hi-C contact matrices |
| [`pyBigWig`](https://github.com/deeptools/pyBigWig) | Reading bigWig genome track files |
| `scikit-image` (`skimage`) | Structural similarity metrics |
| `scikit-learn` |regression models |
| `statsmodels` | OLS/WLS regression |
| `seaborn` | Statistical plotting |

## Data sources

Resources and public sequencing datasets used in this analysis:

- **Gene annotation** (NCBI RefSeq, danRer11/GRZc11): O'Leary et al., *Nucleic
  Acids Research* 44(D1):D733–D745, 2016; Sayers et al., *Nucleic Acids Research*
  51(D1):D29–D38, 2023; Wheeler et al., *Nucleic Acids Research* 35(suppl_1):D5–D12,
  2007.
- **RNA-seq**: White et al., *eLife* 6:e30860, 2017.
- **ChIP-seq — Pol II Ser5P, H3K27ac, H3K4me3**: Bogdanović et al., *Genome
  Research* 22(10):2043–2053, 2012.
- **ChIP-seq — Nanog, Sox19b, Pou5f3**: Miao et al., *Molecular Cell*
  82(5):986–1002, 2022; Nanog additionally Xu et al., *Developmental Cell*
  22(3):625–638, 2012.
- **ATAC-seq**: Marlétaz et al., *Nature* 564(7734):64–70, 2018.
- **BS-seq**: Potok et al., *Cell* 153(4):759–772, 2013.
- **Hi-C**: Wike et al., *Genome Research* 31(6):981–994, 2021.
- **Super-enhancers (ROSE)**: Lovén et al., *Cell* 153(2):320–334, 2013; Whyte
  et al., *Cell* 153(2):307–319, 2013.
- **PADREs/DANIO-CODE**: Baranašić et al., *Nature Genetics* 54(7):1037–1050, 2022
- **cCREs (SPATAC-seq)**: "Mapping the chromatin accessibility landscape of
  zebrafish embryogenesis at single-cell resolution by SPATAC-seq," *Nature Cell
  Biology*, 2024.
- **CpG islands**: Gardiner-Garden & Frommer, *Journal of Molecular Biology*
  196(2):261–282, 1987.
- **Genome-build liftover**: Zhao et al., *Bioinformatics* 30(7):1006–1007, 2014.
