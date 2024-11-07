# OBIS training for eDNA data sharing 🐠

Training documents for the OBON projects meeting in November 2024. 

This training is meant for eDNA data providers interested in the formatting and addition of eDNA data to the OBIS database. The training runs through simple steps in adding eDNA data. In addition, we will try out how to access and work with eDNA data already in OBIS. 

## Example dataset

The example eDNA dataset is available at in the [dataset folder](dataset). We are going to process this dataset to a darwin core archive, including all of the information available in this folder. As is typically the case for amplicon data, the data is provided in multiple tables:

1. An otu table
2. A taxonomy table
3. A sample information table
4. A fasta file for the sequences


An example [R markdown solution](pieter.Rmd) to the data cleaning exercise is also available. To start with your own work, you can clone the repository to your computer, and copy the solution "pieter.Rmd", to a file with your own name.


## Contents

- [The DNADerivedData extension](dna.md)
- [Download the repository to work with the dataset](dataset.md)
- [Process the eDNA data to Darwin Core](pieter.Rmd)
- [Access and work with eDNA data from OBIS](dna_access_pacman.Rmd)


# Preparing for training

To prepare for training (in case no internet available), clone this repository to your computer. Make sure that the following libraries are installed:

```

if (!requireNamespace("pacman", quietly = TRUE)) install.packages("pacman")
pacman::p_load(robis, dplyr, ggplot2, tidyr, knitr, ggtree, mapview, sf, RColorBrewer, rmarkdown, readxl, rmarkdown, lubridate, purrr, leaflet, Biostrings, dwcawriter) 
remotes::install_github("pieterprovoost/r-dwca-writer")

```