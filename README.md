# 🧬 nfcore-viralrecon-analysis  
### **The Kappa Variant Discovery**

This repository documents my first end-to-end analysis of **SARS-CoV-2 sequencing data** using the **nf-core/viralrecon** pipeline from raw FASTQ files to lineage identification of the **Kappa (B.1.617.1)** variant.  

The project originated from the **Bioinformatics for Biologists course** by Wellcome Connecting Science, where I was introduced to the **nf-core/viralrecon** workflow. However, after completing the guided steps, I expanded the analysis independently via troubleshooting, modifying, and extending the workflow to identify variants and mutations in real samples.

---

## Overview  
This project demonstrates the complete process of viral genome reconstruction and mutation profiling using open-source tools like **Nextflow**, **nf-core/viralrecon**, **SnpEff**, **USHER**, and **IGV**.  

It highlights the learning curve of a beginner navigating real-world bioinformatics pipelines from repetitive errors and failed runs to achieving reproducible and interpretable results.

---

## Workflow Summary  

| Step | Description | Tools Used |
|------|--------------|------------|
| **1. Data Retrieval** | Downloaded Illumina paired-end FASTQ files from NCBI SRA. | `fasterq-dump`, NCBI SRA Toolkit |
| **2. Preprocessing** | Performed quality control and primer trimming. | `FastQC`, `Cutadapt` |
| **3. Genome Alignment** | Mapped reads to the SARS-CoV-2 reference genome. | `Bowtie2`, `SAMtools` |
| **4. Variant Calling** | Identified nucleotide and amino acid substitutions. | `iVar`, `SnpEff` |
| **5. Lineage Classification** | Verified lineage using multiple tools. | `Pangolin`, `Nextclade`, `USHER` |
| **6. Visualization** | Inspected BAM and VCF files for variant confirmation. | `IGV` |

---

## Objectives  
- Understand and execute the **nf-core/viralrecon** pipeline for SARS-CoV-2 datasets.  
- Perform **reference-based variant calling** and annotation.  
- Identify **key spike protein mutations** associated with variants of concern.  
- Strengthen **documentation**, troubleshooting, and reproducibility in bioinformatics workflows.

---

## Dataset  

| Sample ID | Source | Platform | Protocol | Genome | Primer Set | Version |
|------------|---------|-----------|-----------|----------|-------------|-----------|
| ERR5556343 | SRA | Illumina | Amplicon | MN908947.3 | ARTIC | V3 |
| SRR13500958 | SRA | Illumina | Amplicon | MN908947.3 | ARTIC | V3 |
| ERR5743893 | SRA | Illumina | Amplicon | MN908947.3 | ARTIC | V3 |
| ERR5181310 | SRA | Illumina | Amplicon | MN908947.3 | ARTIC | V3 |
| ERR5405022 | SRA | Illumina | Amplicon | MN908947.3 | ARTIC | V3 |

The analysis began with all five samples; however, **sample ERR5743893** was selected for **further evaluation and mutation profiling**, where key spike mutations characteristic of the **Kappa variant (B.1.617.1)** were identified.

---

## Results 
- Successfully processed **5 Illumina samples** using **ARTIC primer set V3**.  
- Achieved complete workflow execution in **~33 minutes** (optimized from 26 minutes).  
- Identified **key spike mutations** characteristic of the **Kappa variant**:  
  - `L452R`, `E484Q`, `P681R`, `D614G`  
- Visualized read alignments (BAM) and variant sites (VCF) in **IGV** for confirmation.  
- Lineage verification performed using **USHER**, confirming **B.1.617.1 (Kappa)**.

## Challenges Faced 
- **Path confusion** — missing symbolic links and misreferenced directories.
- **Parameter definition issues** — incorrect process definitions led to truncations.
- **Workflow restarts** — multiple resume attempts after failed executions.
  
---

## Reflections and Lessons Learned

This project was as much about problem-solving as it was about analysis.
After several failed pipeline runs and repeated debugging, I learned that understanding how a workflow operates is more valuable than simply executing it.

Working through these errors improved my understanding of:

- How Nextflow manages processes and containers.
- How reference file integrity affects downstream analysis.
- The critical role of metadata organization (samplesheets, primers).
- The value of IGV for visually confirming computational results.

This experience reinforced one principle:

**“Tools don’t replace thinking, they amplify it.”**
