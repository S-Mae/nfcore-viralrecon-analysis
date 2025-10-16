# nfcore-viralrecon-analysis
### **The Kappa Variant Discovery**

This repository documents my first end-to-end analysis of **SARS-CoV-2 sequencing data** using the **nf-core/viralrecon** pipeline — from raw FASTQ files to lineage identification of the **Kappa (B.1.617.1)** variant.  

It captures the process, challenges, and lessons learned while implementing a real-world viral genome analysis workflow.

---

## Overview  
This project demonstrates the complete process of viral genome reconstruction and mutation profiling using open-source tools like **Nextflow**, **nf-core/viralrecon**, **SnpEff**, **USHER**, and **IGV**.  

It highlights not just the technical steps but also the perseverance required to troubleshoot and optimize complex bioinformatics workflows as a beginner.

---

## Workflow Summary  

| Step | Description | Tools Used |
|------|--------------|------------|
| **1. Data Retrieval** | Downloaded Illumina paired-end FASTQ files from NCBI SRA. | `fasterq-dump`, NCBI SRA Toolkit |
| **2. Preprocessing** | Performed quality control and primer trimming. | `FastQC`, `Cutadapt` |
| **3. Genome Alignment** | Mapped reads to the SARS-CoV-2 reference genome. | `Bowtie2`, `SAMtools` |
| **4. Variant Calling** | Identified nucleotide and amino acid substitutions. | `iVar`, `SnpEff` |
| **5. Lineage Classification** | Verified lineage across tools for accuracy. | `Pangolin`, `Nextclade`, `USHER` |
| **6. Visualization** | Inspected BAM and VCF files for variant confirmation. | `IGV` |

---

## Objectives  
- Understand and execute the **nf-core/viralrecon** pipeline for SARS-CoV-2 datasets.  
- Perform **reference-based variant calling** and annotation.  
- Identify **key spike protein mutations** associated with variants of concern.  
- Develop strong **documentation and reproducibility** practices in computational analysis.

---

## Dataset  

| Sample ID | Source | Platform | Protocol | Genome | Primer Set | Version |
|------------|---------|-----------|-----------|----------|-------------|-----------|
| ERR5181310 | SRA | Illumina | Amplicon | MN908947.3 | ARTIC | V3 |

Input FASTQ files were retrieved from the **Sequence Read Archive (SRA)** and organized using a structured sample sheet.

Example `samplesheet.csv`:
```csv
sample,fastq_1,fastq_2
ERR5181310,Workflow_Data/ERR5181310_1.fastq.gz,Workflow_Data/ERR5181310_2.fastq.gz

---

## Results  
- Successfully processed **5 Illumina samples** using **ARTIC primer set V3**.  
- Achieved complete workflow execution in **~33 minutes** (optimized from 26 minutes).  
- Identified **key spike mutations** characteristic of the **Kappa variant**:  
  - `L452R`, `E484Q`, `P681R`, `D614G`  
- Visualized read alignments (BAM) and variant sites (VCF) in **IGV** for confirmation.  
- Lineage verification performed using **USHER**, confirming **B.1.617.1 (Kappa)**.  

---

## Challenges Faced  
- **Path confusion** — missing symbolic links and misreferenced directories.  
- **Parameter definition issues** — incorrect process definitions led to truncations.  
- **Workflow restarts** — multiple resume attempts after failed executions.

---

## Conclusions  
- Successfully reconstructed SARS-CoV-2 genomes and identified the **Kappa variant**.  
- Learned the importance of:
  - Proper parameter specification and reference file validation.  
  - **Documentation** — every command, error, and fix matters.  
  - Visualization (IGV) for verifying variant presence and mapping quality.  
- Reinforced a key principle:  
  **“Tools don’t replace thinking — they amplify it.”**  
