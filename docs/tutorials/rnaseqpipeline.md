---
title: RNASeq Pipeline
layout: default
parent: Services and Guidelines
grand_parent: Main Page
has_children: false
---

<figure>
<img src="../docs/assets/images/nfcore_pipeline.png"
alt="NF Core Pipeline" />
<figcaption aria-hidden="true">NF Core Pipeline</figcaption>
</figure>

**RNA-seq data** is valuable as it allows the measure of RNA expression
levels as a transcriptional readout and the study of RNA structures in
order to understand how RNA-based mechanisms impact gene regulation and
thus disease and phenotypic variation
(<https://www.encodeproject.org/rna-seq/>)

**rRNA databases**:
<https://github.com/biocore/sortmerna/tree/master/data/rRNA_databases>

**Reference build:**
<https://support.illumina.com/sequencing/sequencing_so>&lt;ware/igenome.html

**Steps in data processing:**

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 12%" />
<col style="width: 37%" />
<col style="width: 29%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Step</th>
<th style="text-align: left;">Software/Module</th>
<th style="text-align: left;">Input</th>
<th style="text-align: left;">Output</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">Assess Data Quality</td>
<td style="text-align: left;">fastqc</td>
<td style="text-align: left;">*.fastq.gz ﬁles</td>
<td style="text-align: left;">websummary.html</td>
</tr>
<tr class="even">
<td style="text-align: left;">Adapter and Quality Trimming of Reads</td>
<td style="text-align: left;">TrimGalaore!</td>
<td style="text-align: left;">*.fastq.gz ﬁles</td>
<td style="text-align: left;">Trimmed *.fastq.gz ﬁles</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Removal of Ribosomal RNA</td>
<td style="text-align: left;">SortMeRNA</td>
<td style="text-align: left;">Trimmed *.fastq.gz ﬁles; rRNA
databases</td>
<td style="text-align: left;">Ribosomal RNA removed and trimmed
*.fastq.gz ﬁles</td>
</tr>
<tr class="even">
<td style="text-align: left;">Alignment to the Genome</td>
<td style="text-align: left;">STAR</td>
<td style="text-align: left;">Ribosomal RNA removed and trimmed
*.fastq.gz ﬁles; reference build</td>
<td style="text-align: left;">*.bam ﬁles</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Sort and index alignment</td>
<td style="text-align: left;">SAMTools</td>
<td style="text-align: left;">*.bam ﬁles</td>
<td style="text-align: left;">Sorted <em>.bam ﬁles and </em>.bai
ﬁles</td>
</tr>
<tr class="even">
<td style="text-align: left;">Duplicate Read Marking</td>
<td style="text-align: left;">Picard markDuplicates</td>
<td style="text-align: left;">Sorted <em>.bam ﬁles and </em>.bai
ﬁles</td>
<td style="text-align: left;"><em>.markDups.bam ﬁles and
</em>.markDups.bai ﬁles</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Quality control</td>
<td style="text-align: left;">MultiQC</td>
<td style="text-align: left;">Output summaries from RSeQC, Qualimap,
dupRadar, Preseq, edgeR</td>
<td style="text-align: left;">websummary.html</td>
</tr>
<tr class="even">
<td style="text-align: left;">Expression quantification</td>
<td style="text-align: left;">featureCounts</td>
<td style="text-align: left;"><em>.markDups.bam ﬁles and
</em>.markDups.bai ﬁles; reference build</td>
<td style="text-align: left;">*.featureCounts.txt ﬁles</td>
</tr>
<tr class="odd">
<td style="text-align: left;">Differential Expression</td>
<td style="text-align: left;">DESeq2</td>
<td style="text-align: left;">*.featureCounts.txt ﬁles; sample metadata
(names, groups, contrasts)</td>
<td style="text-align: left;">* deseq2.results.txt ﬁles and
*.deseq2.plots.pdf ﬁles</td>
</tr>
</tbody>
</table>
