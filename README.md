# Genome-Resolved Metatranscriptomic Analysis of Anaerobic Aggregate Specialization in Aerobic Granular Sludge (AGS)
# Demonstration is based on https://www.sciencedirect.com/science/article/pii/S2666498425000389?via%3Dihub#mmc1

## Overview

This project investigates functional specialization across different aggregate sizes in aerobic granular sludge (AGS) using genome-resolved metagenomics and metatranscriptomics.

The analysis focuses on anaerobic-stage microbial activity in:

- Flocs (FL)
- Small granules (SG)
- Large granules (LG)

The goal is to explore how microbial community structure and transcriptional activity differ across aggregate niches, with particular emphasis on:

- phosphorus metabolism
- polyphosphate-accumulating organisms (PAOs)
- nitrogen cycling
- functional differentiation between aggregate types

This project was developed as a demonstration of microbiome multi-omics analysis workflows relevant to biofloc and wastewater microbial ecology research.

---

# Dataset

Source:
NCBI SRA BioProject: SRP483748

## Metagenomes (DNA)

| Sample | SRR |
|---|---|
| FL metagenome | SRR27548873 |
| SG metagenome | SRR27548884 |
| LG metagenome | SRR27548885 |

## Metatranscriptomes (RNA)

### Flocs (FL, anaerobic)

| Replicate | SRR |
|---|---|
| R1 | SRR27548856 |
| R2 | SRR27548855 |

### Small granules (SG, anaerobic)

| Replicate | SRR |
|---|---|
| R1 | SRR27548881 |
| R2 | SRR27548880 |

### Large granules (LG, anaerobic)

| Replicate | SRR |
|---|---|
| R1 | SRR27548875 |
| R2 | SRR27548874 |

---

# Biological Questions

This project explores the following questions:

1. Do different AGS aggregate sizes harbor distinct active microbial communities?

2. Which metabolic pathways are preferentially expressed in flocs versus granules?

3. How does transcriptional activity differ from genomic abundance?

4. Which taxa contribute most strongly to anaerobic phosphorus metabolism?

5. Can genome-resolved transcriptional profiling reveal ecological niche specialization within AGS systems?

---

# Workflow

## 1. Quality Control

Tools:
- fastp
- FastQC

Processing:
- adapter trimming
- quality filtering
- read statistics

---

## 2. Metagenome Assembly

Tool:
- MEGAHIT

Output:
- assembled contigs
- assembly statistics

---

## 3. Genome Binning

Tools:
- MetaBAT2
- CheckM

Output:
- metagenome-assembled genomes (MAGs)
- genome completeness and contamination estimates

---

## 4. Taxonomic Annotation

Tools:
- Kraken2
- GTDB-Tk

Goals:
- identify dominant taxa
- classify PAOs and nitrifiers
- compare community composition across aggregate types

---

## 5. Functional Annotation

Tools:
- Prokka
- eggNOG-mapper

Target pathways:
- phosphorus metabolism
- polyphosphate storage
- nitrification
- denitrification
- carbon metabolism

Key genes:
- ppk1
- ppk2
- pstSCAB
- phaABC
- amoA
- nxrA
- nirS
- nosZ

---

## 6. Metatranscriptomic Mapping

Tools:
- Bowtie2
- featureCounts

RNA reads are mapped against assembled MAGs to quantify transcriptional activity.

---

## 7. Differential Expression Analysis

Tool:
- DESeq2

Comparisons:
- FL vs SG
- FL vs LG
- SG vs LG

Outputs:
- differentially expressed genes
- pathway enrichment
- aggregate-specific metabolic signatures

---

# Expected Outcomes

This project aims to demonstrate:

- reproducible microbiome bioinformatics workflows
- genome-resolved multi-omics integration
- metatranscriptomic interpretation
- ecological specialization across microbial aggregates
- functional differentiation within AGS systems

---

# Preliminary Hypotheses

Based on previous AGS studies:

- Large granules are expected to show stronger PAO-associated transcriptional activity.
- Flocs are expected to exhibit greater fermentative and nitrogen-transforming activity.
- Transcriptional activity will not necessarily correlate with DNA abundance.
- Aggregate size likely creates distinct metabolic niches.

---

# Repository Structure

```text
biofloc-multiomics/
├── config/
├── workflow/
├── scripts/
├── envs/
├── resources/
├── results/
│   ├── qc/
│   ├── assembly/
│   ├── bins/
│   ├── taxonomy/
│   ├── annotation/
│   ├── expression/
│   └── figures/
├── Snakefile
└── README.md
