---
layout: page
title: RNA-Seq Tutorial Overview

---


Differential Gene Expression Analysis on the Cancer Genomics Cloud (CGC)
============================================

**RNA sequencing (RNA-Seq)** is a high throughput technique that provides qualitative and quantitative information about RNA biology including transcriptome-wide expression quantification, discovery of novel genes and gene isoforms, and differential expression. 

!!! tip "Tutorial Goal"
    1. Create virtual cancer cohorts using the Integrated Canine Data Commons (ICDC). 
    2. Conduct differential gene expression (DGE) within the Cancer Genomics Cloud (CGC), the cloud analysis platform that interoperates with the ICDC.

!!! note
    This example RNA-Seq analysis uses 6 Binary Alignment Mapping (BAM) files derived from 6 canine individuals enrolled in the UBC02 study.  3 files are from tumor tissues sequenced from diseased individuals and 3 files are from normal tissues sequenced from healthy individuals.  


**Table of Contents**

| Lesson Name | Description|
| ---|--------|
| [Overview of RNA-Seq](./rna_seq_02.md) | History of RNA-Seq
| [Building a Cohort on the ICDC](./rna_seq_03.md) | Build cohort on the ICDC and export files to the CGC |
| [Navigating the CGC](./rna_seq_04.md)  |  Set up project, inspect files, and copy tools into project |
| [Analyzing sample files](./rna_seq_05.md) |  Run samtools, htseq-count, and DESeq2|
