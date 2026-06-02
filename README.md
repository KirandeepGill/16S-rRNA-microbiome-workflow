## 16S rRNA Amplicon Analysis Pipeline

A reproducible R workflow for 16S rRNA amplicon sequencing analysis, covering taxonomic relative abundance profiling, alpha diversity, and beta diversity with statistical testing and visualization.

## Overview

This pipeline processes 16S rRNA amplicon data stored as a phyloseq object and produces publication-quality figures and diversity statistics. It is demonstrated using the `GlobalPatterns` dataset (publicly available via the phyloseq R package), which contains microbial community samples from diverse environments including soil, ocean, gut, and freshwater.

**Key outputs:**
- Taxonomic relative abundance bar plots (phylum level)
- Alpha diversity estimates (Shannon, Inverse Simpson) with Kruskal-Wallis and Dunn post-hoc testing
- Beta diversity dissimilarity matrix (Bray-Curtis) with PCoA visualization

---
