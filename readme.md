# Parent-of-Origin Rare Variant Gene-Based Burden Tests

**Author:** Martin Quintas (University of Zurich / University of Lausanne)  
**Supervisors:** Prof. Dr. Mark D. Robinson (UZH), Dr. Robin Hofmeister (UNIL), Prof. Dr. Zoltán Kutalik (UNIL)  
**Date:** March 2026  

## Project Overview

This repository contains the code and summary information for the Master's Thesis project in Biostatistics (STA495): *Parent-of-Origin Rare Variant Gene-Based Burden Tests*. 

Standard Genome-Wide Association Studies (GWAS) predominantly evaluate additive genetic effects, operating under the assumption of parental symmetry. This project investigates **parent-of-origin effects (POEs)** of rare, high-impact mutations (Loss-of-Function and missense) by leveraging Whole Exome Sequencing (WES) data and parent-of-origin-aware gene-based burden tests. 

For a comprehensive explanation of the theoretical background, methodology, and a full discussion of the results, please refer to the complete thesis document: **MSc_Report.pdf**.

## Methodology

This project leverages data from approximately 110,000 phased individuals within the **UK Biobank (UKB)**. The analytical pipeline consists of several key steps:

1. **Phasing:** A surrogate-parent phasing pipeline (incorporating Identity-By-Descent segments) was used to resolve maternal and paternal haplotypes for individuals lacking direct parental data in the cohort.
2. **Variant Annotation:** Genetic variants were annotated using Ensembl VEP, LOFTEE, and UTRannotator to group them by predicted functional impact (Loss-of-Function and Missense).
3. **Burden Testing:** Independent gene-based burden associations were performed for each parental haplotype across 62 complex traits using the **REGENIE** whole-genome regression framework.
4. **Differential Analysis:** A differential Z-score statistic was derived to compare maternal and paternal effect sizes ($\beta_{mat}$ vs $\beta_{pat}$) to identify significant POEs.

### Discovery Strategies
The analysis followed a three-tiered discovery strategy to optimize statistical power:
*   **Strategy 1:** Targeted validation of 74 known gene-complex trait signals.
*   **Strategy 2:** Hypothesis-driven screen of 249 known imprinted genes.
*   **Strategy 3:** Agnostic exome-wide discovery scan across 18,788 genes.

## Key Findings

Our results confirm the presence of parent-specific genetic architecture across a broad spectrum of human traits, predominantly concentrated within metabolic, liver-related, and hormonal phenotypes.

*   **Validation:** Successfully replicated established POE signals, notably at the *KCNQ1* locus associated with standing height, observing a bipolar effect for rare LoF variants.
*   **Imprinted Gene Screen:** Identified a bipolar association between *SLC4A7* LoF variants and Lipoprotein A levels, as well as a suggestive POE at the *NAPRT* locus for Apolipoprotein B.
*   **Exome-Wide Discovery:** Discovered robust evidence of parental asymmetry at novel candidate loci, such as the *CPZ* locus, which demonstrated a distinct maternal-specific influence on a cluster of lipid and liver-related traits (e.g., total cholesterol, LDL, alkaline phosphatase).

*For a detailed breakdown of all significant and suggestive associations, including Manhattan and QQ plots, please see Chapter 3 of MSc_Report.pdf.*

## Reproducibility & Code Structure

Due to the sensitive nature and licensing restrictions of the UK Biobank WES data, the raw genomic datasets cannot be shared publicly. All primary analyses were executed on the UK Biobank Research Analysis Platform (RAP) powered by DNAnexus.

The repository includes:
*   **REGENIE Scripts:** Example bash scripts demonstrating the implementation of REGENIE Step 1 (whole-genome regression model fitting) and Step 2 (parent-of-origin burden testing).
*   **Data Visualization:** R scripts utilizing `ggplot2` and `data.table` to generate Manhattan plots, QQ plots, and boxplots for data visualization and downstream processing.
*   **Full Thesis Report:** **MSc_Report.pdf**

## Acknowledgements

This work was supported by the Statistical Genetics Group from the Department of Computational Biology at the University of Lausanne, with special thanks to Dr. Robin Hofmeister and Prof. Zoltán Kutalik, as well as Prof. Mark Robinson of the University of Zurich.