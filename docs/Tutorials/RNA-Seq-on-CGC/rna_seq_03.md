---
layout: page
title: Building a Cohort within the ICDC

---


Building a Cohort within the ICDC
============================================

The [Integrated Canine Data Commons](https:https://caninecommons.cancer.gov/#/) is a cloud-based repository of spontaneously-arising canine cancer data from pet dogs established to further research on human cancers by enabling comparative analysis with canine cancer.
All files available through the ICDC are open-access and can be exported into the CGC by any user. For this tutorial, we will conduct an example RNA-Seq analysis using 6 Binary Alignment Mapping files derived from 6 canine individuals enrolled in the UBC02 study.  3 files are from tumor tissues sequenced from diseased individuals and 3 files are from normal tissues sequenced from healthy individuals. 

## Step 1: Filter cases using faceted search
The ICDC has a comprehensive menu of faceted values that can be used to filter data by cases, sample, and files. For example, data can be filtered by the disease diagnosis, the sample pathology, or file format. Specific cases of interest can be found entering the case IDs or uploading a list of case IDs. For this tutorial we will filter by the UBC02 study and select cases that were associated with multiple studies.
* Navigate to the [ICDC Explore Dashboard](https://caninecommons-qa.cancer.gov/#/explore)
* Expand the <span class="highlight_facet">Study</span> facet and select <span class="highlight_facetvalue">UBC02</span>
* Expand the <span class="highlight_facet">Study Participation</span> facet and select <span class="highlight_facetvalue">Multiple Study</span>

![ICDC Explore Dashboard](./rna-seq-images/icdc-explore-dashboard.png "ICDC Explore Dashboard")


## Step 2: Add files to the Cart
The ICDC Dashboard makes it very simple to load files of interest into the "My Files" Cart page. After applying desired filters, either click on the Add Assoicated Files for All button to add files for every case listed in the Dashboard table or select cases of interest by clicking on the checkboxes and then click on the Add Files for Selected Cases button. For this tutorial we will select a total of 6 cases. 
* From within the Dashboard table click on the checkbox corresponding to 3 healthy controls and 3 diseased canines
* Click on the <span class="highlight_button">Add Files for Selected Cases</span> button

![ICDC Dashboard Table](./rna-seq-images/icdc-dashboard-table.png "Dashboard Table")


## Step 3: Export files from the Cart to the Cancer Genomics Cloud
The ICDC "My Files" Cart page enables users to view files of interest in JBrowse a next generation genome browser, export these files into the CGC, or download a file manifest containing metadata describing each to their local computer. For this tutorial, we will be exporting our files directly in the CGC.
* Click on the <span class="highlight_icon">My Files</span> icon in the top right of the navigation bar
* Check to make sure there are 12 files in the cart
* Expand the dropdown menu of the <span class="highlight_button">Available Export Options</span> button
* Click on <span class="highlight_button">Export to Cancer Genomics Cloud</span>
* Follow the prompt to login to the CGC or create an account if one does not yet exist
* Select a <span class="highlight_button">Destination project</span> from the dropdown menu or create a new project
* Select the <span class="highlight_icon">checkbox</span> to agree to the CGC terms
* Click on the <span class="highlight_button">Import data</span> button

![ICDC My Files Cart Page](./rna-seq-images/icdc-loaded-cart.png "My Files Cart page")