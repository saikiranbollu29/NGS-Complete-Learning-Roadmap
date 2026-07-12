# 🎯 Targeted Sequencing

> **Module 2 • Lesson 4**

Targeted Sequencing is an NGS approach that sequences only selected genes or genomic regions instead of the entire genome or exome.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Explain Targeted Sequencing.
- Differentiate Targeted Sequencing, WES, and WGS.
- Understand Amplicon Sequencing and Hybrid Capture.
- Create a Linux environment.
- Understand the bioinformatics workflow.
- Explain Targeted Sequencing in interviews.

---

# 📚 Prerequisites

Before starting this lesson, you should know:

- DNA Structure
- Genes
- Genome
- WGS
- WES
- FASTQ

---

# 💡 Real-Life Analogy

Imagine a city with **50,000 houses**.

A police officer only needs to investigate **10 specific houses** related to a case.

Instead of searching the entire city, they focus only on those houses.

Targeted Sequencing follows the same idea.

Instead of sequencing the entire genome, it sequences only selected genes that are clinically or biologically relevant.

---

# 🧬 What is Targeted Sequencing?

Targeted Sequencing is an NGS method in which only predefined genes or genomic regions are enriched and sequenced.

It provides very high sequencing depth for selected targets while reducing sequencing cost and analysis time.

---

# ❓ Why Do We Need Targeted Sequencing?

Sometimes we already know which genes are associated with a disease.

Examples:

- BRCA1
- BRCA2
- TP53
- EGFR
- KRAS
- BRAF

Instead of sequencing all genes, we sequence only these clinically relevant genes.

---

# 🔬 Types of Targeted Sequencing

## 1️⃣ Amplicon Sequencing

Uses PCR primers to amplify specific DNA regions before sequencing.

### Workflow

```
DNA

↓

PCR Amplification

↓

Library Preparation

↓

Sequencing
```

### Best For

- Small gene panels
- Mutation screening
- Clinical diagnostics

---

## 2️⃣ Hybrid Capture Sequencing

Uses capture probes that bind to target DNA fragments.

### Workflow

```
DNA

↓

Fragmentation

↓

Capture Probes

↓

Target Enrichment

↓

Sequencing
```

### Best For

- Large gene panels
- Cancer panels
- Hereditary disease testing

---

# 🆚 WGS vs WES vs Targeted Sequencing

| Feature | WGS | WES | Targeted |
|----------|-----|-----|----------|
| Genome Coverage | Entire Genome | Exons Only | Selected Genes |
| Cost | High | Moderate | Low |
| Data Generated | Very Large | Medium | Small |
| Coverage Depth | Moderate | High | Very High |
| Clinical Use | Comprehensive | Broad | Disease-Specific |

---

# 🧪 Sample Types

- Blood
- Saliva
- FFPE Tissue
- Fresh Tissue
- Bone Marrow
- Cell Culture

---

# 🔬 Wet Lab Workflow

```
Sample

↓

DNA Extraction

↓

DNA QC

↓

Library Preparation

↓

Target Enrichment

↓

Sequencing

↓

FASTQ
```

---

# 💻 Bioinformatics Workflow

```
FASTQ

↓

FastQC

↓

Fastp

↓

Alignment (BWA)

↓

BAM

↓

Variant Calling

↓

VCF

↓

Annotation

↓

Clinical Report
```

---

# 🐧 Linux Environment

## Create Environment

```bash
conda create -n targeted_seq python=3.11
```

Activate

```bash
conda activate targeted_seq
```

---

# 📦 Install Required Software

```bash
mamba install \
fastqc \
multiqc \
fastp \
bwa \
samtools \
bcftools
```

---

# Verify Installation

```bash
fastqc --version
bwa
samtools --version
bcftools --version
```

---

# 📁 Project Structure

```
Targeted_Sequencing/

raw_data/

reference/

qc/

trimmed/

alignment/

variants/

annotation/

results/

logs/
```

---

# 📥 Input Files

| File | Description |
|------|-------------|
| FASTQ | Raw Reads |
| Reference Genome | FASTA |
| BED File | Target Regions |

---

# 🔧 Analysis Pipeline

## Step 1

Quality Check

```bash
fastqc sample_R1.fastq.gz sample_R2.fastq.gz
```

---

## Step 2

Read Trimming

```bash
fastp \
-i sample_R1.fastq.gz \
-I sample_R2.fastq.gz \
-o clean_R1.fastq.gz \
-O clean_R2.fastq.gz
```

---

## Step 3

Alignment

```bash
bwa mem reference.fa \
clean_R1.fastq.gz \
clean_R2.fastq.gz \
> sample.sam
```

---

## Step 4

Convert SAM to BAM

```bash
samtools view -Sb sample.sam > sample.bam
```

---

## Step 5

Sort BAM

```bash
samtools sort sample.bam -o sample.sorted.bam
```

---

## Step 6

Index BAM

```bash
samtools index sample.sorted.bam
```

---

## Step 7

Variant Calling

```bash
bcftools mpileup \
-f reference.fa \
sample.sorted.bam | \
bcftools call -mv \
-o variants.vcf
```

---

# 📂 Output Files

| File | Description |
|------|-------------|
| FASTQ | Raw Reads |
| BAM | Alignment |
| BAI | BAM Index |
| VCF | Detected Variants |

---

# 🏥 Clinical Applications

- Hereditary Cancer Testing
- Breast Cancer Panels
- Lung Cancer Panels
- Cardiovascular Disorders
- Rare Genetic Diseases
- Pharmacogenomics

---

# ⭐ Advantages

- Lowest sequencing cost
- Very high coverage
- Fast analysis
- Easy interpretation
- Excellent for known disease genes

---

# ⚠️ Limitations

- Cannot detect variants outside the target regions
- Requires predefined gene panels
- Novel disease genes may be missed

---

# 🌍 Real Clinical Example

A patient with a strong family history of breast cancer undergoes a hereditary cancer panel.

Instead of sequencing the whole genome, the laboratory sequences:

- BRCA1
- BRCA2
- TP53
- PALB2

This provides high-depth analysis of clinically relevant genes at a lower cost than WGS.

---

# 🧠 Interview Corner

### Why is Targeted Sequencing cheaper than WES?

Because only a small number of predefined genes are sequenced, resulting in lower sequencing and analysis costs.

---

### What is the difference between Amplicon Sequencing and Hybrid Capture?

Amplicon sequencing uses PCR to amplify target regions, whereas hybrid capture uses probes to enrich target DNA fragments.

---

### When should you choose Targeted Sequencing?

When the disease-associated genes are already known and only those genes need to be analyzed.

---

# ⭐ Lesson Summary

✅ Selected genes only

✅ Lowest cost

✅ Highest sequencing depth

✅ Widely used in clinical diagnostics

✅ Excellent for hereditary disease testing

---

# 🚀 Next Lesson

➡️ Metagenomics
