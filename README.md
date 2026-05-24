# Shutgun Metagenomics NGS Tools for Pathogen Detection
By: Sumeyye Taskin                                                                                                                                                              
Supervised by: Dr.Josep Quer                                                                                                                                                                       
Universitat Autònoma de Barcelona (UAB) and Vall d'Hebron Institut de Recerca (VHIR). Grup Malalties Hepàtiques-Hepatitis viral.                                                

Repository content                                                                                                                                                              
Readme:
Information about repository and folders content.                                                                                                                               

Scripts                                                                                                                                                                         

Bioinformatics pipeline
This folder contains all scripts used for the analysis of fastQ files from metagenomics samples (Guillain-Barré syndrome).                                                      ## Repository Structure
 
```
metagenomic-ngs-pipeline/
│
├── upstream/                  # Scripts for raw read processing
│   ├── 01_fastqc.sh           # Initial quality control (FastQC + MultiQC)
│   ├── 02_trimmomatic.sh      # Trimming low quality and short sequences
│   ├── 03_bowtie2_human.sh    # Removal of human host sequences
│   ├── 04_kraken2_reads.sh    # Taxonomic classification at read level
│   ├── 05_megahit.sh          # De novo assembly (reads → contigs)
│   └── 06_kraken2_contigs.sh  # Taxonomic classification of assembled contigs
│
├── downstream/                # Scripts for results interpretation
│   ├── 01_decontam.R          # Contaminant removal using DECONTAM
│   ├── 02_taxonomy_analysis.R # Subsetting and interpreting Kraken2 tables
│   └── 03_graphs.R            # Visualization of results
│
├── confirmation/              # Pathogen confirmation steps
│   └── bowtie2_alignment.sh   # Read mapping to specific pathogen genomes
│
└── README.md
```
 
---

## Pipeline
 
### Upstream Analysis
 
| Step | Tool | Description |
|------|------|-------------|
| 1 | FastQC + MultiQC | Initial quality report of raw reads |
| 2 | Trimmomatic | Remove low-quality reads and short sequences |
| 3 | Bowtie2 | Remove human host sequences |
| 4 | Kraken2 | Taxonomic classification at read level |
| 5 | MEGAHIT | De novo assembly of reads into contigs |
| 6 | Kraken2 / BLAST | Taxonomic classification of assembled contigs |
 
### Downstream Analysis
 
| Step | Tool | Description |
|------|------|-------------|
| 1 | DECONTAM (R) | Identify and remove contaminants using negative controls |
| 2 | Custom R script | Subset and interpret Kraken2 classification tables |
| 3 | Custom R script | Generate figures and graphs |

### Pathogen Confirmation
 
If a relevant virus or pathogen is detected, confirmation is done by aligning reads to the specific reference genome:
- Reference genomes downloaded from **NCBI RefSeq**
- Alignment performed with **Bowtie2** via [Galaxy Europe](https://usegalaxy.eu/)
---
 


