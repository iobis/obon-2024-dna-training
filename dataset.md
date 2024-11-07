# Processing an eDNA dataset

## Clone the dataset repository

Go to the dataset repository at <https://github.com/iobis/obon-2024-dna-training> and clone the repository to your own computer.

## Creating your solution

In the solutions folder, copy the file pieter.rmd in the [solutions folder](solutions/pieter.rmd), with your own name. You can now run through the example with your own data, or the dataset provided in the repository. 

## Processing the dataset

We will run through several steps to process a typical processed DNA dataset to Darwin Core.

### What to try

- Determine which core and extension tables you will need.
- Combine the ASV table, the taxonomy table, and the sample metadata into a Darwin Core occurrence table. Keep in kind that any ASV can occur in multiple samples.
- Use the `obistools` package for taxon matching. Optionally fix some of the non matching names manually.
- Use the `obistools` package for checking coordinates.
- Use the `obistools` package for checking dates.
- Use the `obistools` package to check for missing fields.
- Create an ExtendedMeasurementOrFact table. Possible measurements are sequence reads, sample size, and DNA concentration. Note that not all of these have terms in the NERC vocabulary server.
- Create a DNADerivedData table. Some of the information can be found in the metadata file.
- Write the individual tables to the `dwc/<yourname>` directory.
- To generate a Darwin Core Archive from Darwin Core data frames, you can use the <https://github.com/pieterprovoost/r-dwca-writer> package.

## To compare: use the gbif tool

GBIF is developing a new [tool](https://mdt.gbif-uat.org/) to help users process their eDNA datasets to DwC, with a complete [user guide](https://docs.gbif-uat.org/mdt-user-guide/en/). GBIF and OBIS use the same standards with some small differences, therefore this tool can be used also to format data for OBIS, or to even publish to GBIF and OBIS. 

If your node is linked to both an OBIS and GBIF IPT, this is very easy to do. 

You can use a subset of the trial data in the [dataset folder](./dataset/dataset_subset_gbif_tool/)


## Checking your dataset using EMODnet BioCheck

Go to <https://rshiny.lifewatch.be/BioCheck/> and enter the URL of your Darwin Core Archive on GitHub, or upload your file directly.


