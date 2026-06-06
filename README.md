# NGS-Snakemake-Pipeline

A scalable and reproducible Snakemake workflow for processing Next-Generation Sequencing (NGS) data, including quality control, read trimming, alignment, variant calling, and reporting.

## Overview

This pipeline automates common NGS analysis steps while ensuring reproducibility and efficient resource management.

### Workflow

```text
Raw FASTQ Files
        │
        ▼
      FastQC
        │
        ▼
   Read Trimming
        │
        ▼
 Post-trim FastQC
        │
        ▼
     Alignment
        │
        ▼
 BAM Processing
        │
        ▼
 Variant Calling
        │
        ▼
 Variant Filtering
        │
        ▼
     MultiQC
```

## Features

* Automated workflow using Snakemake
* Paired-end FASTQ processing
* Quality assessment with FastQC
* Adapter trimming with Fastp
* Read alignment using BWA-MEM
* BAM sorting and indexing using SAMtools
* Variant calling using BCFtools
* MultiQC summary reports
* Conda environment support
* Local workstation and HPC compatible

## Directory Structure

```text
NGS-Snakemake-Pipeline/
│
├── workflow/
│   ├── Snakefile
│   └── rules/
│       ├── qc.smk
│       ├── trimming.smk
│       ├── alignment.smk
│       └── variant_calling.smk
│
├── config/
│   └── config.yaml
│
├── envs/
│   ├── fastqc.yaml
│   ├── fastp.yaml
│   ├── bwa.yaml
│   ├── samtools.yaml
│   └── bcftools.yaml
│
├── data/
│   ├── raw/
│   └── reference/
│
├── results/
├── logs/
└── README.md
```

## Software Requirements

* Snakemake ≥ 7.0
* FastQC
* Fastp
* BWA
* SAMtools
* BCFtools
* MultiQC
* Conda / Mamba

## Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/NGS-Snakemake-Pipeline.git
cd NGS-Snakemake-Pipeline
```

Create a Snakemake environment:

```bash
conda create -n snakemake python=3.11
conda activate snakemake
conda install -c conda-forge -c bioconda snakemake
```

## Configuration

Edit `config/config.yaml`:

```yaml
samples:
  sample1:
    R1: data/raw/sample1_R1.fastq.gz
    R2: data/raw/sample1_R2.fastq.gz

reference:
  genome: data/reference/genome.fa

threads: 8
```

## Run Pipeline

Dry run:

```bash
snakemake -n
```

Execute workflow:

```bash
snakemake --cores 8
```

Run with Conda environments:

```bash
snakemake --use-conda --cores 8
```

Generate DAG:

```bash
snakemake --dag | dot -Tpng > workflow_dag.png
```

## Output

```text
results/
├── fastqc/
├── trimmed/
├── aligned/
├── variants/
└── multiqc/
```

## Example Applications

* Whole Genome Sequencing (WGS)
* Whole Exome Sequencing (WES)
* Targeted Sequencing Panels
* Small-scale Variant Discovery Projects
* Educational Bioinformatics Workflows

## Future Enhancements

* GATK Best Practices
* RNA-Seq Workflow
* Structural Variant Detection
* CNV Analysis
* Docker/Singularity Support
* Cloud Deployment
