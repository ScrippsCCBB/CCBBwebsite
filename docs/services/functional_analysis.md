---
title: Functional Analysis
layout: single
permalink: /pages/services/functional_analysis/
---

{% include_relative pricing.md %}

# CCBB services

## Transcriptomics

* RNA-Seq, UMI-based RNA-Seq, High Throughput RNA-Seq (”Drug-Seq”), smallRNA-Seq (miRNA-Seq)

* Single cell RNA-Seq, immune profiling - V(D)J, Visium Spatial transcriptomics (10x Genomics)

## RNA-Seq

*Requirements*:

1. Read targets reached (e.g. ~ 20 million reads per sample; human genome) for each of your samples in the study

2. Number of sample submitted are less than 20

3. Sample metadata (sample conditions and comparisons to be done) shared with CCBB prior to sequencing

4. 3 or more biological replicates per condition in your experiment

5. Reference genomes considered as standard: human, mouse, rat

### Standard analysis (CCBB effort level - 5 hours; 3-5 business days)

This uses nf-core/rnaseq workflow: Adapter trimming, removal of ribosomal RNA reads, alignment to reference genome using STAR, raw gene counts (FeatureCounts), differential gene expression analyses (DESeq2, R) along with PCA plot, MultiQC summary file with several QC plots/tables). 

### Additional analysis (consult CCBB for effort level and timeline for completion)

This includes analysis for datasets with higher than 20 mil reads/sample needed for differential exon analysis and alternative splicing analysis, outlier removal and re-analysis, multiple sets of standard analysis, analysis for datasets with more than 20 samples, analysis involving non-standard genomes, custom differential gene expression, differential gene expression analysis on publicly available datasets, comparisons/inclusion of older datasets for re-analysis, RNA-Seq short variant discovery (SNPs and INDELS) using GATK pipeline, comprehensive functional analysis using CCBB licensed Advaita’s iPathwayGuide, GSEA or SetRank analysis.


## UMI-based RNA-Seq

*Requirements: Same as for RNA-Seq analysis*

### Standard analysis (CCBB effort level - 5 hours; 3-5 business days)

This uses nf-core/rnaseq workflow: Adapter trimming, removal of ribosomal RNA using SortMeRNA, Alignment to reference genome using STAR, deduplication of the reads based on both mapping and UMI barcode information to address PCR duplicates using the UMI-tools, raw gene counts (featureCounts), differential gene expression analyses (DESeq2, R) along with PCA plot, MultiQC summary file with several QC plots/tables). 

## High Throughput RNA-Seq (”Drug-Seq”)  

### Standard analysis  (CCBB effort level - 2 to 5 hours; 3-5 business days)

Inline-barcode based demux only (for 96 samples) (CCBB effort level 2 hours)
Inline-barcode based demux followed by UMI-based RNA-Seq analyses (described above) to identify significantly differentially expressed genes (CCBB effort level 5 hours)

### Additional analysis (consult CCBB for effort level and timeline for completion)


This includes outlier removal and re-analysis, multiple sets of standard analysis, analysis involving non-standard genomes, custom differential gene expression, differential gene expression analysis on publicly available datasets, comparisons/inclusion of older datasets for re-analysis, comprehensive functional analysis using CCBB licensed Advaita’s iPathwayGuide, GSEA or SetRank analysis.

## SmallRNA-Seq (miRNA-Seq) 

### Standard analysis (CCBB effort level - 5 hours; 3-5 business days)

CCBB services and effort levels similar to RNA-Seq data analysis.


## Single cell transcriptomics (Consult CCBB for the effort level and timeline)
	
### Standard analysis using 10x Genomics single-cell analysis pipelines

* CellPlex

* 3' Gene Expression

* 3' Gene Expression + Antibody/CRISPR Guide Capture

* Antibody Capture only

* 3' Gene Expression + Cell Multiplexing (+ Antibody/CRISPR Guide Capture)

* Fixed RNA Profiling Gene Expression (+ Antibody Capture)

* 5' V(D)J only

* 5' Gene Expression only

* 5' Antibody Capture (+ Gene Expression)

* 5' CRISPR (Feature Barcode) + Gene Expression

* 5' Gene Expression + V(D)J (+ Feature Barcode)

* 5' Gene Expression + V(D)J + Antigen Capture (BEAM) (+ Antibody Capture)

* Multiome ATAC + Gene Expression

### Additional analysis (Consult CCBB for effort level and timeline)

More complex experimental designs and/or downstream analyses like differential expression, cell-type annotations, pseudotime analysis, RNA velocity, comprehensive pathway analysis using Advaita’s iPathwayGuide, specific figures, writing Methods for paper/grant etc. 


## Spatial transcriptomics 

### Visium Spatial Transcriptomics (10x Genomics) 

#### Standard analysis 	using Space Ranger pipelines

Visium spatial gene expression data with brightfield and fluorescence images to align reads, generate Feature Barcode matrices, and perform secondary analysis including clustering and differential gene expression.

### GeoMx Digital Spatial Profiling (Nanostring)

#### Standard analysis 	using GeoMx pipeline 

FASTQ sequencing files from Nanostring GeoMx libraries processed using the GeoMx NGS Pipeline to generate digital count conversion (.dcc) files. Zipped DCC files get uploaded to the GeoMx DSP system for downstream analysis.

# Additional Services

Email to ccbb.at.scripps.edu to set up a consultation meeting for additional service(s)

## Additional services: Consult CCBB to get a quote/estimation of effort in hours. CCBB service hourly charges apply.


* Software development, custom pipeline implementation

* Re-analysis of older dataset

* Analysis for public dataset

* Specific figures/tables for publications; writing methods section or contribution for scientific papers/grant proposals

* Functional Analysis using Advaita/GSEA/SetRank

* Letter of Support for grants

* GEO/SRA submissions





