---
title: RNASeq Pipeline
permalink: /pages/tutorials/rnaseqpipeline/
layout: single
classes: wide
---

![NF Core Pipeline](../assets/images/nfcore_pipeline.png)


**RNA-seq data** is valuable as it allows the measure of RNA expression levels as a transcriptional readout and the study of RNA structures in order to understand how RNA-based mechanisms impact gene regulation and thus disease and phenotypic variation [encodeproject](https://www.encodeproject.org/rna-seq/)

**rRNA databases**:

**Reference build:**

**Steps in data processing:**

| Step                                  | Software/Module       | Input                                                                | Output                                              |
|---------------------------------------|-----------------------|----------------------------------------------------------------------|-----------------------------------------------------|
| Assess Data Quality                   | fastqc                | *.fastq.gz ﬁles                                                      | websummary.html                                     |
| Adapter and Quality Trimming of Reads | TrimGalaore!          | *.fastq.gz ﬁles                                                      | Trimmed *.fastq.gz ﬁles                             |
| Removal of Ribosomal RNA              | SortMeRNA             | Trimmed *.fastq.gz ﬁles; rRNA databases                              | Ribosomal RNA removed and trimmed *.fastq.gz ﬁles   |
| Alignment to the Genome               | STAR                  | Ribosomal RNA removed and trimmed *.fastq.gz ﬁles; reference build   | *.bam ﬁles                                          |
| Sort and index alignment              | SAMTools              | *.bam ﬁles                                                           | Sorted .bam ﬁles and .bai ﬁles                      |
| Duplicate Read Marking                | Picard markDuplicates | Sorted .bam ﬁles and .bai ﬁles                                       | .markDups.bam ﬁles and .markDups.bai ﬁles           |
| Quality control                       | MultiQC               | Output summaries from RSeQC, Qualimap, dupRadar, Preseq, edgeR       | websummary.html                                     |
| Expression quantification             | featureCounts         | .markDups.bam ﬁles and .markDups.bai ﬁles; reference build           | *.featureCounts.txt ﬁles                            |
| Differential Expression               | DESeq2                | *.featureCounts.txt ﬁles; sample metadata (names, groups, contrasts) | deseq2.results.txt ﬁles and *.deseq2.plots.pdf ﬁles |
