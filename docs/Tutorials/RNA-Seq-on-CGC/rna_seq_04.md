---
layout: page
title: Analysis within the Cancer Genomics Cloud (CGC)

---


Analysis within the Cancer Genomics Cloud (CGC)
============================================
The Seven Bridges Cancer Genomics Cloud (CGC) is powered by Velsera and funded by the National Cancer Institute. The CGC is a cloud-based technology that enables analysis, storage, and computation of large cancer datasets. The CGC interoperates with the ICDC making it easier than ever to move from data acquisition to data analysis.


## Step 1: Copy apps into project
The CGC has over 900 public apps that can be easily copied into a project to enable reproducible bioinformatics. For this tutorial, we will copy several apps into our project.
* Click on <span class="highlight_text">Public Apps</span> from the top navigation bar to expand the dropdown menu
* Select Workflows and Tools
* Click the <span class="highlight_button">Browse apps</span> button
* Use the search bar to find each tool listed below
    - Sambamba Flagstat
    - Samtools View
    - Samtools Sort
    - HTSeq-count
    - DESeq2

* For each tool, click the <span class="highlight_button">Copy</span> button and then Select the appropriate project from the dropdown menu and then click the Copy button once more
* Click on <span class="highlight_text">Projects</span> from the main navigation bar to expand the dropdown menu and select the appropriate project name to return to the project
* Click on <span class="highlight_text">Apps</span> from the menu bar to ensure all tools were effectively copied into the project
![Tools loaded](./rna-seq-images/cgc-apps-loaded.png "Tools loaded")


## Step 2: Inspect summary stats for each file with Sambamba Flagstat
Before conducting RNA-Seq it is important to ensure the quality of the BAM files that are intended to be used as inputs. The percentage of mapped reads can have a large impact on a downstream analysis and could signal an issue with the mapping aligner that was used to generate the BAM file.
* Click on Sambamba Flagstat
* Click on the <span class="highlight_button">Run</span> button from the top right-hand side
* Click on the toggle to turn Batching On
* Select File from the Batch by dropdown menu
* Click on Input alignments
* Select all bam files by clicking on the respective checkboxes
* Click on the <span class="highlight_button">Save Selection</span> button on the top right-hand side
* Click on the <span class="highlight_button">Run</span> button on the top right-hand side 
![Samtools Flagstat](./rna-seq-images/cgc-flagstat-results.png "Samtools Flagstat")


## Step 3: Inspect bam file headers with Samtools View
Before conducting RNA-Seq it is important to determine which reference genome was used to generate the BAM files and how the BAM file is sorted.
* Click on <span class="highlight_text">Apps</span> from the menu bar
* Click on Samtools View
* Click on the <span class="highlight_button">Run</span> button from the top right-hand side
* Under App Settings scroll down to <span class="highlight_text">Output the header only</span> and select True from the dropdown menu
* Click on the toggle to turn Batching On
* Select File from the Batch by dropdown menu 
* Click on Select file(s) dropdown menu associated with the Input BAM/SAM/CRAM file
* Select all bam files by clicking on the respective checkboxes
* Click on the <span class="highlight_button">Save selection</span> button on the top right-hand side
* Click on the <span class="highlight_button">Run</span> button on the top right-hand side


## Step 4: Load the appropriate reference annotation file
In order to count gene features across exons the HTSeq-count tool will need a Gene Transfer Format (GTF) file that contains information about each gene from a particular reference genome. In this case, the original BAM files were mapped to the NCBI reference genome canFam3. 
* Download the GTF file located here https://hgdownload.soe.ucsc.edu/goldenPath/canFam3/bigZips/genes/
* Click on canFam3.ncbiRefSeq.gtf.gz
* Locate this file on your local computer and open to unzip
* Navigate back to the CGC and add this file to the project


## Step 5: Count sequencing reads with htseq-count
Binary Alignment Mapping files or BAM files are simply compressed binary representation of sequence data mapped to a particular reference genome. Although these files are not human readable, we can use tools such as HTSeq to count sequencing reads that overlap exons for each gene in a reference genome. 
* Click on <span class="highlight_text">Apps</span> from the secondary menu bar
* Click HTSeq-count
* Click on the <span class="highlight_button">Run</span> button from the top right-hand side
* Under App Settings select name from the Order dropdown menu
* Under App Settings select ignore from the secondary alignments dropdown menu
* Under App Settings select ignore from the supplementary alignments dropdown menu
* Click on the toggle to turn Batching On
* Select File from the Batch by dropdown menu 
* Click on the <span class="highlight_button">Select file(s)</span> button associated with Aligned reads
* Select all name sorted bam files from the name_sorted folder
* Click on the <span class="highlight_button">Select file(s)</span> button associated with Reference annotation file
* Select canFam3.ncbiRefSeq.gtf.gz
![HTSeq-count](./rna-seq-images/cgc-htseq-results.png "HTSeq-count")

## Step 5: Create a csv file with phenotype data for all samples for DESeq2
Before conducting differential expression a file must be derived to tell DESeq2 how the samples relate to one another. For this tutorial, we can easily generate this file using our exported file manifest from the ICDC.
* Click on <span class="highlight_text">Files</span> from the menu bar
* In the search box type .csv and hit enter
* Click on the file manifest which will be named with a series of letters and numbers with a .csv file extension
* Click on the <span class="highlight_button">Download</span> button to initiate a download to your local machine
![File Manifest](./rna-seq-images/cgc-download-manifest.png "File Manifest")
* Open this file in Excel or any similar application
* Move the sample_id column so that it is the first column in the file
* Delete all rows pertaining to the Index Files with a file_format of bai
* Save the file as phenotype_filtered.csv
* The file created should be formatted similar to the file shown below
![phenotype_filtered.csv](./rna-seq-images/cgc-phenotype_filtered.png "phenotype_filtered.csv")
* Click on the <span class="highlight_button">Add files</span> button to expand the dropdown menu and select Your Computer
* Click on the <span class="highlight_button">Browse files</span> button to add the file created named phenotype_filtered.csv
* Click on the green <span class="highlight_button">Start upload</span> button

## Step 6: Conduct differential expression with DESeq2
The DESeq2 package can determine differential expression between sample groups using the raw count table derived by HTSeq and fitting the negative binomial generalized linear model for each gene and then using the Wald test for significance testing. Count outliers are detected using Cook’s distance and can be removed from further analysis. The Wald test p-values from the subset of genes that pass independent filtering can then be adjusted for multiple testing using the Benjamin-Hochburg procedure.

* Click on <span class="highlight_text">Apps</span> from the menu bar
* Click DESeq2 
* Click on the <span class="highlight_button">Run</span> button from the top right-hand side
* Under App Settings enter Urinary_Bladder_Cancer_DGE as the Analysis title
* Under App Settings enter diagnosis as the Covariate of interest
* Under App Settings enter 0.01 as the FDR cutoff
* Under App Settings enter Healthy Control as the Factor level - reference
* Under App Settings enter Bladder Cancer as the Factor level - test
* Under App Settings select htseq from the dropdown menu of Quantification tool
* Under App Settings select True from the dropdown menu of log2 fold change shrinkage
* Under Inputs click on the Select file(s) button associated with Expression data
    * Select the counts.tsv files from the Counts folder
* Under Inputs click on the Select file(s) button associated with Gene annotation
    * Select canFam3.ncbiRefSeq.gtf
* Under Inputs click on the Select file(s) button associated with Phenotype data
    * Select phenotype_filtered.csv

![DESeq2 Parameters](./rna-seq-images/cgc-deseq2-parameters.png "DESeq2 Parameters")

* Click on the <span class="highlight_button">Run</span> button in the upper right-hand corner
* When the task has completed successfully inspect the results that should be the same as shown below
![PCA Plot](./rna-seq-images/cgc-pca-plot.png "PCA Plot")
![Cluster Dendrogram](./rna-seq-images/cgc-cluster-dendrogram.png "Cluster Dendrogram")
![Boxplot](./rna-seq-images/cgc-boxplot.png "Boxplot")
![Summary](./rna-seq-images/cgc-analysis-summary.png "Summary")







