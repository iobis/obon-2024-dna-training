# The DNADerivedData extension

The [DNADerivedData extension](https://rs.gbif.org/extension/gbif/1.0/dna_derived_data_2022-02-23.xml) was created to extend occurrence data with sequencing related metadata, mostly consisting of terms from the GGBN Data Standard, GSC MIxS (Minimum Information about any (X) Sequence), and MIQE (The Minimum Information for Publication of Quantitative Real-Time PCR Experiments).

Guidelines for using the extension and publishing DNA-derived data in general are available at [Publishing DNA-derived data through biodiversity data platforms](https://docs.gbif.org/publishing-dna-derived-data/en/). The guide handles metabarcoding and metagenomis, which are sequence derived, and qPCR/ddPCR data which are not sequence derived.

![dna guide](images/dna_guide.png)

## Dataset categories

1. DNA derived occurrences
2. Enriched occurrences
3. Targeted species detection
4. Name references (OTUs/ASVs/BINs)
5. Metadata only 

![](https://docs.gbif.org/publishing-dna-derived-data/img/web/ct/eDNA-categories.en.svg)
From https://docs.gbif.org/publishing-dna-derived-data/en/

## Processing workflow

![](https://docs.gbif.org/publishing-dna-derived-data/img/web/outline-of-bioinformatic-processing.en.svg)
From https://docs.gbif.org/publishing-dna-derived-data/en/

## Data mapping

See [Mapping (meta)barcoding data](https://docs.gbif.org/publishing-dna-derived-data/en/#mapping-metabarcoding-edna-and-barcoding-data) and [Mapping qPCR/ddPCR data](https://docs.gbif.org/publishing-dna-derived-data/en/#mapping-ddpcr-qpcr-data).

## OBIS specificities
### Unclassified sequences

For OBIS we recommend that unclassified sequences are annotated as `scientificName` = `incertae sedis` and `scientificNameID` = `urn:lsid:marinespecies.org:taxname:12`.  This will ensure correct interpretation by both GBIF and OBIS.

Additionally, it is recommended that sequence identifiers from the used reference databases (e.g. Barcode index numbers: BINs from BOLD) be added in the `taxonConceptID` field of the occurrence core table. In this way OBIS will retain its taxonomic backbone based on WoRMS, while enabling linking to disparate reference sequence databases. Names from reference databases which are not strictly scientific names, can be added as verbatimIdentification.

## Examples
### eDNA/metabarcoding
#### Occurrence

| Term | Example |
|---|---|
| basisOfRecord | MaterialSample |
| organismQuantity | 120 |
| organismQuantityType | DNA sequence reads |
| sampleSizeValue | 1109573 |
| sampleSizeUnit | DNA sequence reads |
| associatedSequences | https://www.ebi.ac.uk/ena/browser/view/ERR2752143 |
| identificationRemarks | RDP annotation confidence (at lowest specified taxon): 0.96, against reference database: MIDORI. |
| | Identification based on the RDP classifier at the confidence level 0.8: taxonomy Eukaryota;Chordata;Actinopteri;Albuliformes;Albulidae;Albula;Albula_glossodonta, confidences 1;1;1;1;1;1;0.92. Confirmation with VSEARCH against the 16S_ncbi_euk_1_50000_pga database at 0.97 similarity: hits KF681807,X99179,AY857934,NC_082992, identities 100,97.9,97.9,97.5, taxonomy Albula_glossodonta,Albula_vulpes,Albula_vulpes,Albula_vulpes, consensus Eukaryota;Chordata;Actinopteri;Albuliformes;Albulidae;Albula;Albula_vulpes. |
| identificationReferences | https://github.com/terrimporter/CO1Classifier |
| verbatimIdentification | Nitzschia_sp._BOLD:AAO7110 |
| scientificName | Nitzschia |
| taxonConceptID | BOLD:AAO7110 |

| Term | Example |
|---|---|
| verbatimIdentification | phototrophic eukaryote |
| taxonConceptID | NCBI:txid1899546 |
| scientificName | incertae sedis |
| scientificNameID | urn:lsid:marinespecies.org:taxname:12 |

#### DNADerivedData

| Term | Example |
|---|---|
| DNA_sequence | TCTATCCTCAATTAT AGGTCATAATTCAC CATCAGTAGATTTAG GAATTTTCTCTATTC ATATTGCAGGTGTAT CATCAATTATAGGAT CAATTAATTTTATTG TAACAATTTTAAATA TACATACAAAAACT CATTCATTAAACTTT TTACCATTATTTTCA TGATCAGTTCTAGTT ACAGCAATTCTCCTT TTATTATCATTA |
| target_gene | 16S rRNA |
| target_subfragment | V6 |
| pcr_primer_forward | GGACTACHVGGGTWTCTAAT |
| pcr_primer_reverse | GGACTACHVGGGTWTCTAAT |
| pcr_primer_name_forward | jgLCO1490 |
| pcr_primer_name_reverse | jgHCO2198 |
| seq_meth | Illumina HiSeq 1500 |
| otu_class_appr | dada2; 1.14.0; ASV |
| otu_db | MIDORI Reference 2 |
| otu_seq_comp_appr | RDP classifier 2.14 |

### qPCR

#### DNADerivedData

| Term | Example |
|---|---|
| target_gene | 16S rRNA |
| target_subfragment | V6 |
| pcr_primer_forward | GGACTACHVGGGTWTCTAAT |
| pcr_primer_reverse | GGACTACHVGGGTW TCTAAT |
| pcr_primer_name_forward | jgLCO1490 |
| pcr_primer_name_reverse | jgHCO2198 |
| annealingTemp | 60 |
| annealingTempUnit | degrees celsius |
| pcr_cond | initial denaturation:94_3; annealing:50_1;elon gation:72_1.5;final elongation:72_10;35 |
| probeReporter | FAM |
| probeQuencher | NFQ-MGB |
| thresholdQuantificationCycle | 0.3 |
| baselineValue | 15 |
| pcr_primer_lod | 51 |
| pcr_primer_loq | 184 |
| concentration | 67.5 |
| concentrationUnit | ng/μl |
