## 16S rRNA Amplicon Analysis Pipeline

A reproducible R workflow for 16S rRNA amplicon sequencing analysis, covering taxonomic relative abundance profiling, alpha diversity, and beta diversity with statistical testing and visualization.

This pipeline processes 16S rRNA amplicon data stored as a **phyloseq object** and produces publication-quality figures and diversity statistics. It is demonstrated using the `GlobalPatterns` dataset (publicly available via the phyloseq R package), which contains microbial community samples from diverse environments including soil, ocean, gut, and freshwater.
This project creates a workflow for 16S rRNA analysis uses a publicly available dataset.To calculate the relative abundance of the taxa in the samples and their alpha and beta diversity. Using a Phyloseq object from the R library, the R scripts are used to get the taxa abundance and to calculate the between sample and within sample diversity and visualization using ggplot2.
