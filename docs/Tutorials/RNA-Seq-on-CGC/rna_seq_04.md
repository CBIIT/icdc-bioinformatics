---
layout: page
title: Analysis within the Cancer Genomics Cloud

---


Analysis within the Cancer Genomics Cloud
============================================
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