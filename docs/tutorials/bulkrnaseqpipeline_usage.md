---
title: bulk RNASeq Pipeline - usage
permalink: /pages/tutorials/bulkrnaseqpipeline_usage/
layout: single
classes: wide
---

This repository contains scripts used by CCBB for running nfcore RNASEQ(v3.12) Pipeline.  
Reference : https://nf-co.re/rnaseq/3.12.0  

Scripts are available in this location on the workstation : /ccbbcoded/asundaresan/nfcore_rnaseq_v3.12_WS_scripts

### STEP1
First step is to generate the samplesheet that will be used to run the nfcore RNASeq pipeline.  

The following script is used to generate the samplesheet.By default the strandedness is set to "auto".  
The output is named samplesheet.csv  
path_to_script/1.generate_samplesheet_nfcore_rnaseq_v3.12_WS.job  

We need to pass the full path of the folder which has the fastqs as the input parameter for this script  

path_to_script/1.generate_samplesheet_nfcore_rnaseq_v3.12_WS.job path_to_fastqs



### STEP2
Next we will run the nfcore RNASeq pipeline.  

The following script is used to run the pipeline, followed by consolidation of rRNA stats, merging the individual sample FPKM and TPM to one file, DE analysis using DESEQ2, followed by cuffdiff file generation for Advaita, volcano plot generation and creating the summary folder that will be used for dispatch.   
path_to_script/2.run_nfcore2.7.2_rnaseq_v3.12_WS.job  

We need to pass the full path of the folder containing the samplesheet and the genome as parameter for this script.  
Please note that the samplesheet has to be named samplesheet.csv.  
The following genome parameters are configured for use  

| Organism  | Parameter to use |
| --------  | ------- |
| Human   |      HU0    |
| Mouse |        MM0    |
| Rat    |       RN0    |
| C elegans    | CE0    |

path_to_script/2.run_nfcore2.7.2_rnaseq_v3.12_WS.job path_to_samplesheet HU0
