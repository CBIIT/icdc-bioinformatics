---
layout: page
title: RNA-Seq Tutorial Overview

---


Differential Gene Expression Analysis using the UBC02 Study
============================================

**RNA sequencing (RNA-Seq)** is a high throughput technique that provides qualitative and quantitative information about RNA biology including transcriptome-wide expression quantification, discovery of novel genes and gene isoforms, and differential expression. 

The goal of this tutorial is to enable you to: 

1. create virtual cancer cohorts using the Integrated Canine Data Commons (ICDC). 
2. analyze differential gene expression (DGE) within the Cancer Genomics Cloud (CGC), the cloud analysis platform for the ICDC.


This example  RNA-Seq analysis uses 6 Binary Alignment Mapping files derived from 6 canine individuals enrolled in the UBC02 study.  3 files are from tumor tissues sequenced from diseased individuals and 3 files are from normal tissues sequenced from healthy individuals.  


**Bioinformatic Pipeline**

| Steps | Description|
| ---|--------|
| 1 | Select RNA-Seq files from the UBC02 study in the ICDC and export to the Cancer Genomics Cloud
| 2 | Run samtools flagstat to get summary stats for each file |
| 3  | Sort bam files by coordinate and name using samtools sort |
| 4 | Run samtools view to inspect bam file headers|
| 5  | Count sequencing reads that map to exons in the canine genome using htseq-count |
| 6  | Download metadata file for bam files and reformat so that "Sample_ID" is the first column |
| 7  | Run the DESeq2 app with appropriate inputs and computational settings to conduct differential expression between tumor and normal samples |
