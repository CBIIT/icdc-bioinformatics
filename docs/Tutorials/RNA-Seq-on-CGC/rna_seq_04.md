---
layout: page
title: Analysis within the Cancer Genomics Cloud

---


Analysis within the Cancer Genomics Cloud
============================================


## Step 1: Copy tools into project
* Click on Public Apps from the top navigation bar to expand the dropdown menu
* Select Workflows and Tools
* Click the Browse buttons app
* Use the search bar to find each tool listed below
** Sambamba Flagstat
** Samtools View
** Samtools Sort
** HTSeq-count
** DESeq2
* For each tool, click the Copy button and then Select the appropriate project from the dropdown menu and then click the Copy button once more
* Click on Projects from the main navigation bar to expand the dropdown menu and select the appropriate project name to return to the project
* Click on Apps from the secondary navigation bar to ensure all tools were effectively copied into the project
![Tools loaded](./rna-seq-images/cgc-flagstat-results.png "Tools loaded")

## Step 2: Inspect summary stats for each file with Sambamba Flagstat
* Click on Sambamba Flagstat
* Click on the Run button from the top right-hand side
* Click on the toggle to turn Batching On
* Select File from the Batch by dropdown menu
* Click on Input alignments
* Select all bam files by clicking on the respective checkboxes
* Click on the Save selection button on the top right-hand side
* Click on the Run button on the top right-hand side 
![Samtools Flagstat](./rna-seq-images/cgc-flagstat-results.png "Samtools Flagstat")
## Step 3: Inspect bam file headers with Samtools View
* Click on Apps from the secondary navigation menu 
* Click on Samtools View
* Click on the Run button from the top right-hand side
* Under App Settings scroll down to Output the header only and select True from the dropdown menu
* Click on the toggle to turn Batching On
* Select File from the Batch by dropdown menu 
* Click on Select file(s) dropdown menu associated with the Input BAM/SAM/CRAM file
* Select all bam files by clicking on the respective checkboxes
* Click on the Save selection button on the top right-hand side
* Click on the Run button on the top right-hand side 
## Step 4: Count sequencing reads with htseq-count
* Click on Apps from the secondary navigation menu 
* Click on HTSeq-count
* Click on the Run button from the top right-hand side
* Under App Settings select name from the Order dropdown menu
* Under App Settings select ignore from the secondary alignments dropdown menu
* Under App Settings select ignore from the supplementary alignments dropdown menu
![HTSeq-count](./rna-seq-images/cgc-flagstat-results.png "HTSeq-count")
## Step 5: Generate metadata file for DESeq2
## Step 6: Conduct differential expression with DESeq2