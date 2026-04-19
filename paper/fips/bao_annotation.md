(fcb-interop-txmetadata)=
# Metadata for cell-based assays using Bioassay Ontology (BAO)


````{panels_fairplus}
:identifier_text: XXXXX
:identifier_link: 'https://w3id.org/faircookbook/XXXXX'
:difficulty_level: 3 remark Rob: how did you decide on the maturity level  ?
:recipe_type: guidance
:reading_time_minutes: 30
:intended_audience: principal_investigator, data_manager, terminology_manager, data_scientist, ontologist 
:maturity_level: 3
:maturity_indicator: 30
:has_executable_code: nope
:recipe_name: Outlining a metadata profile for cell-based assays
```` 

## Main Objectives:

The main purpose of this recipe is:

> To provide guidance on creating the minimum set of metadata and semantics required to describe cell-based assays of relevance to toxicology (e.g. for connection to AOPs). This for the purpose of "Finding" the data.


### Who is this recipe aimed at?

This document is aimed at anyone interested in the metadata, and specifically the ontology annotations, required to capture variables and experimental factors related to a cell-based assays. General knowledge of cell-based assays would be beneficial. No specific technical knowledge is required.


---

## Cell-based assay data model

### BioAssay Ontology

High-throughput screening (HTS) data can serve the purpose of identificaiton of possible hazards, as it may signify possible interaction of a chemical/nanomaterial etc. with a molecular initiating event (MIE). As HTS data are highly heterogeneous and exponentially growing in public repositories, there is a significant need in proper annotation of these data as to allow for its reuse in combined data analyses.

BioAssay Ontology (BAO) was created to establish common reference metadata terms and definitions required for describing relevant information of low-and high-throughput drug and probe screening assays and results. The main objectives of BAO are to enable effective integration, aggregation, retrieval, and analyses of drug screening data. BAO is a formal OWL-DL ontology and captures deep knowledge about screening assays and their results enabling classifications that enable data analysis and facilitate meaningful retrieval of screening results.


![BAO excerpt showing the root-level classes and some of their relationships (extracted 28/05/2024)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3149580/bin/1471-2105-12-257-1.jpg)
*Visser et al., 2011*

### Minimum metadata vs desirable metadata

A minimum metadata set constitutes metadata items that always need to be supplied with any experimental data. For validation purposes, these should not be omittable. Desirable or recommended metadata items on the other hand should be supplied if available but will not cause a validation failure if absent. 

### Common metadata

Common metadata include any information that is not specific to cell-based assays but also applies to most experiments in the biomedical domain. They include:

- Project level metadata
- Common sample level metadata such as species, tissue, cell type etc.


#### Suggested metadata fields

The following table contains a non-exhaustive list of suggested minimum metadata fields for biological samples. The collection is based on a range of existing metadata standards, including MIAME, MINSEQE, FAANG and HCA. Fields were included if they occurred in at least two of the standards.

|Metadata field|Required?|Definition|Comment|
|--------|--------|--------|--------|
|unique ID|required|Identifier for a sample that is at least unique within the project||
|sample type|required|The type of the collected specimen, eg tissue biopsy, blood draw or throat swab|`ontology field` - e.g. OBI or EFO|
|species|required|The primary species of the specimen, preferably the taxonomic identifier|This may not be the same as the "host" organism, eg in the case of a PDX tissue sample, the host may be a mouse but the tissue may be human. Ontology field - NCBITaxonomy|
|tissue/organism part|required|The tissue from which the sample was taken|`ontology field` - e.g. Uberon|
|disease|required|Any diseases that may affect the sample|This may not necessarily be the same as the host's disease, eg healthy brain tissue might be collected from a host with type II diabetes while cirrhotic liver tissue might be collected from an otherwise healthy individual. Ontology field - e.g. MONDO or DO|
|sex|required|The biological/genetic sex of the sample|`ontology field` - e.g. PATO|
|development stage|required|The developmental stage of the sample|`ontology field` - e.g. Uberon or Hsadpdv; species dependent|
|external accessions|recommended|Accession numbers from any external resources to which the sample was submitted|eg Biosamples, Biostudies|
|strain|recommended|Strain of the species from which the sample was collected, if applicable|`ontology field` - e.g. NCBITaxonomy|
|ancestry/ethnicity|recommended|Ancestry or ethnic group of the individual from which the sample was collected|`ontology field` - e.g. HANCESTRO|
|age |recommended|Age of the organism from which the sample was collected||
|age unit|recommended|Unit of the value of the age field|`ontology field` - e.g. UO|
|BMI|recommended|Body mass index of the individual from which the sample was collected|Only applies to human samples|
|treatment category|recommended|Treatments that the sample might have undergone after collection|`ontology field` - e.g. OBI, NCIt or OGMS|
|cell type|recommended|The cell type(s) known or selected to be present in the sample|`ontology field` - e.g. CL|
|growth conditions|recommended|Features relating to the growth and/or maintenance of the sample||
|genetic variation|recommended|Any relevant genetic differences from the specimen or sample to the expected genomic information for this species, eg abnormal chromosome counts, major translocations or indels||
|sample collection technique|recommended|The technique used to collect the specimen, eg blood draw or surgical resection|`ontology field` - e.g. EFO or OBI|
|phenotype|recommended|Any relevant (usually abnormal) phenotypes of the specimen or sample |`ontology field` - e.g. HP or MP; species dependent|
|cell cycle|recommended|The cell cycle phase of the sample (for synchronized growing cells or a single-cell sample), if known|`ontology field` - e.g. GO|
|cell location|recommended|The cell location from which genetic material was collected (usually either nucleus or mitochondria)|`ontology field` - e.g. GO|


### Assay metadata

Assay-level metadata covers any metadata directly related to the preparation of the biomaterial undergoing the assay and the process of performing the assay. Most, though not all, of this metadata is specific. Examples include:
- Process (wet experiment) metadata
- Technology type
- Instrument metadata
- Other assay-specific metadata
- QC information
- Workflow metadata


#### Suggested metadata fields

The following table contains a non-exhaustive list of suggested minimum metadata fields for assays. The collection is based on BAO. This list can and should be further broken down based on specific technologies used.

|Metadata field|Required?|Definition|Comment|
|--------|--------|--------|--------|
|unique ID|required|Identifier for the assay that is at least unique within the project||
|experiment type|required|The type of experiment performed, eg ATAC-seq or seqFISH|`ontology field` - e.g. EFO or OBI|
|assay kit|required|The assay kit used e.g. Cellomics Cell Viability Kit|`ontology field` - |
|bioassay|
|cell line| 
|pertubation|
|detection method|
|medium|
|biological process|
|endpoint|
|assay name|
|array or sequencing method|required|The array or sequencing technology used - may be the same as `experiment type` or can be a more specific term|`ontology field` - e.g. EFO or OBI|
|biological or technical replicate|required|Information whether the sample on which the assay was performed was biological or technical replicate.|boolean or CV|
|end bias|required|The type of tag or end bias the library has, eg 3 prime tag or 5 prime end bias|standardised field or ontology|
|external accessions|recommended|Accession numbers from external resources to which assay or protocol information was submitted|eg protocols.io, AE|
|instrument model|required|The specific instrument on which the assay was performed. Essential for QC purposes.|`ontology field` - e.g. EFO or OBI|
|assay start time|recommended|The exact time at which the assay was started||
|assay end time|recommended|The exact time at which the assay was completed||
|assay duration|recommended|The duration, in a relevant time unit (eg minutes or hours), of the assay from start to finish||
|array quality|recommended|The overall quality of the array||
|chemical compound|recommended|Any relevant chemical compounds used in the assay|`ontology field` - e.g. ChEBI|
|labeling molecule used|recommended|The type of labeling molecule used in an array-based experiment|`ontology field` - e.g. ChEBI|
|cell quality|recommended|Information about the quality of a single cell such as morphology or percent viability|standardised field or ontology|
|cell barcode|recommended|Information about the cell identifier barcode used to tag individual cells in single cell sequencing||

### Analysis metadata

Analysis-level metadata includes any metadata related to the files that come out of the experiment, from the sequencing or imaging files generated directly by the machine to files generated during the various stages of processing and analysis, as well as details of any analyses performed. It is very important to always capture versions of software and reference genomes used in order to allow accurate replication of results. Analysis metadata includes
- Type of analysis
- File formats
- File location e.g. URL

#### Suggested metadata fields

The following table contains a non-exhaustive list of suggested minimum metadata fields for analyses. This list can and should be further broken down based on the specific analysis type (primary, secondary or teriatry analysis, meta-analysis etc)

|Metadata field|Required?|Definition|Comment|
|--------|--------|--------|--------|
|analysis type|required|The type of analysis performed, eg genome assembly or variant calling  |`ontology field` - e.g. EFO, OBI or EDAM|
|computational method|required|The specific computational method or algorithm used as part of the analysis|`ontology field` - e.g. EFO or EDAM|
|normalisation strategy|required|The approach used to normalise the data|`ontology field` - e.g. EFO or EDAM|
|file format|required|The file format in which the analysis is provided|`ontology field` - e.g. EDAM|
|file storage location|required|The location in which the data files are stored||
|software package|recommended|The software package used for data analysis||
|software version|recommended|The exact version number of the software package ||
|analysis date|recommended|The date on which the analysis was performed||

## Ontologies for cell-based assay data

While it is essential that any assay metadata be annotated with ontology terms wherever possible, there is no absolute set of ontologies that must be used above all others. This table represents an absolute minimum of ontology annotations that should be included in a transcriptomics metadata set for it to be considered as FAIR. Not all fields suggested for ontology annotation in the previous section are repeated here for this reason.

|Data type|Ontology/Entity sources|Type|Notes|
|---|---|---|---|
|Species |NCBI taxonomy Scientific name + ID|Ontology||
|Tissue |Uberon term and Id|Ontology||
|Cell type| CL term and Id|Ontology||
|Disease|MONDO, DO or MeSH|Ontology|no single solution - options vary depending on resource and individual requirements |
|Phenotype/Trait|HPO (human),  MP(other mammals), various others for model organisms (yeast, zebrafish, Xenopus, C. elegans)|Ontology||
|Experiment Type|EFO, OBI|Ontology| e.g. RNASeq, CITESeq etc. - |
|Cell location/cycle| GO|Ontology||
|Developmental stage|HSAPDV/Uberon|Ontology||
|Chemical compound| ChEBI|Ontology||
|Chemical compound| UniChem, SMILE, InChi|Entity||

## Conclusion

Using common metadata standards, in particular the fields listed above as guidance, it is possible to
easily define a comprehensive metadata template to capture all the experimental variables to describe any 
cell-based assay in a FAIR-compliant way. A generic step-by-step guide for designing a metadata
template is provided [here](creating-minimal-metadata-profiles.md)

````{dropdown} **References**
````

### What to read next?

http://bioassayontology.org/bioassayontology/

https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3149580/

https://fairsharing.org/874

````{fairsharing_panel}
````
 
## Authors

````{authors_fairplus}

````


## License
````{license_fairplus}
CC-BY-4.0
````
