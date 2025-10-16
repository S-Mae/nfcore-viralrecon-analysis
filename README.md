# nfcore-viralrecon-analysis
The Kappa Variant Discovery

This repository documents my first end-to-end experience analyzing **SARS-CoV-2 sequencing data** using the **nf-core/viralrecon** pipeline — from raw FASTQ files to lineage identification of the **Kappa (B.1.617.1)** variant.   

---

## Overview  
This project demonstrates the process of viral genome reconstruction and mutation profiling using open-source tools like **Nextflow**, **nf-core/viralrecon**, **SnpEff**, **USHER**, and **IGV**.  
It reflects the persistence and growth that comes with debugging, optimizing, and learning as a beginner in real-world bioinformatics workflow automation.

---

## Workflow Summary  

| Step | Description | Tools Used |
|------|--------------|------------|
| **1. Data Retrieval** | Downloaded Illumina paired-end FASTQ files from NCBI SRA. | `fasterq-dump`, NCBI SRA Toolkit |
| **2. Preprocessing** | Performed quality control and primer trimming. | `FastQC`, `Cutadapt` |
| **3. Genome Alignment** | Mapped reads to SARS-CoV-2 reference genome. | `Bowtie2`, `SAMtools` |
| **4. Variant Calling** | Detected nucleotide and amino acid substitutions. | `iVar`, `SnpEff` |
| **5. Lineage Classification** | Verified lineage with multiple tools. | `Pangolin`, `Nextclade`, `USHER` |
| **6. Visualization** | Examined BAM and VCF files for alignment accuracy and variant confirmation. | `IGV` |

---

## Results  
- Successfully processed **5 Illumina samples** using **ARTIC primer set V3**.  
- Achieved complete workflow execution in **~33 minutes** (optimized from 26 minutes).  
- Identified **key spike mutations** characteristic of the **Kappa variant**:  
  - `L452R`, `E484Q`, `P681R`, `D614G`  
- Visualized read alignments (BAM) and variant sites (VCF) in **IGV** for confirmation.  
- Lineage verification performed using **USHER**, confirming **B.1.617.1 (Kappa)**.  

---

## Objectives
- To understand and execute the nf-core/viralrecon pipeline for SARS-CoV-2 datasets.  
- To perform reference-based variant calling and annotation.  
- To identify key spike protein mutations in the variant.  
- To develop documentation skills for reproducible computational workflows.

---

## Challenges Faced  
- **Path confusion** — missing symbolic links and misreferenced directories.  
- **Parameter definition issues** — incorrect process definitions led to truncations.  
- **Workflow restarts** — multiple resume attempts after failed executions.

## 🧩 Conclusions  
- Successfully reconstructed SARS-CoV-2 genomes and identified the **Kappa variant**.  
- Learned the importance of:
  - Proper parameter specification and reference file validation.  
  - **Documentation** — every command, error, and fix matters.  
  - Visualization (IGV) for verifying variant presence and mapping quality.  
- Reinforced a key principle:  
  **“Tools don’t replace thinking — they amplify it.”**  
  
## Dataset
| Sample ID | Source | Platform | Protocol | Genome | Primer Set | Version |
|------------|---------|-----------|-----------|----------|-------------|-----------|
| ERR5181310 | SRA | Illumina | Amplicon | MN908947.3 | ARTIC | V3 |

Input files were retrieved from the **Sequence Read Archive (SRA)**.  
Each paired-end FASTQ file was downloaded using `fasterq-dump` and organized via a sample sheet.

Example sample sheet (`samplesheet.csv`):

```csv
sample,fastq_1,fastq_2
ERR5181310,Workflow_Data/ERR5181310_1.fastq.gz,Workflow_Data/ERR5181310_2.fastq.gz
