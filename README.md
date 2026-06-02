## 16S rRNA Amplicon Analysis Pipeline

A reproducible R workflow for 16S rRNA amplicon sequencing analysis, covering taxonomic relative abundance profiling, alpha diversity, and beta diversity with statistical testing and visualization.

## Overview

This pipeline processes 16S rRNA amplicon data stored as a phyloseq object and produces publication-quality figures and diversity statistics. It is demonstrated using the publicly available GlobalPatterns dataset, which contains microbial community samples from diverse environments including soil, ocean, gut, and freshwater.

**Key outputs:**
- Taxonomic relative abundance bar plots (phylum level)
- Alpha diversity estimates (Shannon, Inverse Simpson) with Kruskal-Wallis and Dunn post-hoc testing
- Beta diversity dissimilarity matrix (Bray-Curtis) with PCoA visualization

## Pipeline Overview

```
Raw phyloseq object
        │
        ▼
1. Quality filtering (prune zero-count taxa, filter low-abundance taxa)
        │
        ▼
2. Relative abundance transformation
        │
        ├──────────────────────────┐
        ▼                          ▼
3a. Alpha Diversity            3b. Taxa Relative Abundance
    Shannon / Inv. Simpson         Agglomerate to Phylum level
    Kruskal-Wallis test            Stacked bar plots
    Dunn post-hoc test
        │
        ▼
4. Beta Diversity
   Bray-Curtis dissimilarity matrix
   PCoA dimensionality reduction
   PCoA scatter plot by sample type
```

## Scripts

| Script | Description |
|--------|-------------|
| `scripts/Diversity_Alpha_Beta.R` | Calculates alpha diversity (Shannon, Inverse Simpson), runs Kruskal-Wallis and Dunn post-hoc tests, computes Bray-Curtis dissimilarity, and generates PCoA plots |
| `scripts/Taxa_RelativeAbundance.R` | Agglomerates taxa to phylum level, transforms counts to relative abundance, and produces stacked bar charts |

---

## Dependencies

Requires R (≥ 4.1.0). Install the following packages before running the scripts:

```r
# CRAN packages
install.packages(c("ggplot2", "dplyr", "reshape2", "knitr", "dunn.test"))

# Bioconductor packages
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install(c("phyloseq", "microbiome"))

# Additional packages
install.packages("vegan")
install.packages("ecodist")
```
## Dataset

**GlobalPatterns** — a widely used benchmark dataset included in the phyloseq R package.

- **Reference:** McMurdie & Holmes (2013). *phyloseq: An R Package for Reproducible Interactive Analysis and Graphics of Microbiome Census Data.* PLoS ONE 8(4): e61217. [https://doi.org/10.1371/journal.pone.0061217](https://doi.org/10.1371/journal.pone.0061217)
- **Samples:** 26 samples across 9 environment types (Soil, Ocean, Freshwater, Human gut, Mock, etc.)
- **Taxa:** ~19,000 OTUs across Bacteria, Archaea, and Eukaryota



## Methods Summary

### Alpha Diversity
Alpha diversity (within-sample diversity) was calculated using the Shannon index and Inverse Simpson index via the microbiome package in R. Differences across sample types were tested using the Kruskal-Wallis test (non-parametric). For significant results, pairwise comparisons were performed using the Dunn test with Benjamini-Hochberg correction for multiple testing.

### Beta Diversity
Beta diversity (between-sample diversity) was assessed using Bray-Curtis dissimilarity computed via the vegan package on phylum-level relative abundance data. Dimensionality reduction was performed using Principal Coordinates Analysis (PCoA) via the ecodist package, and results were visualized with ggplot2.



## Repository Structure

```
16s-rRNA-analysis/
├── scripts/
│   ├── Diversity_Alpha_Beta.R
│   └── Taxa_RelativeAbundance.R
├── figures/               
│   ├── shannon_diversity.png
│   ├── pcoa_bray_curtis.png
│   └── taxa_relative_abundance.png             
├── .gitignore
└── README.md
```

---


