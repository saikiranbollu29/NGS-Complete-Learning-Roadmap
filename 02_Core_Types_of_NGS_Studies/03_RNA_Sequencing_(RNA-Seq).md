# 🧬 RNA Sequencing (RNA-Seq)

> **Module 2 • Lesson 3**

RNA-Seq is one of the most widely used applications of Next-Generation Sequencing (NGS) for studying gene expression.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Explain RNA-Seq.
- Understand the complete RNA-Seq workflow.
- Create a Linux environment for RNA-Seq.
- Install required software.
- Understand every analysis step.
- Explain RNA-Seq in interviews.

---

# 📚 Prerequisites

Before starting this lesson, you should know:

- DNA
- RNA
- Gene
- Genome
- NGS Basics
- FASTQ Format

---

# 💡 Real-Life Analogy

Imagine a library.

The genome is the **entire library**.

RNA molecules are the **books currently being read**.

RNA-Seq tells us:

> Which books are being read?

In biology,

that means

**Which genes are currently being expressed?**

---

# 🧬 What is RNA-Seq?

RNA Sequencing (RNA-Seq) is an NGS technique used to sequence RNA molecules (after conversion into cDNA) to study gene expression.

Unlike DNA sequencing,

RNA-Seq tells us

- Which genes are active
- How active they are
- Alternative splicing
- Gene fusions
- Novel transcripts

---

# 🎯 Why Do We Perform RNA-Seq?

RNA-Seq helps answer questions such as:

- Which genes are expressed?
- Which genes are upregulated?
- Which genes are downregulated?
- How does disease affect gene expression?
- How do drugs change gene expression?

---

# 🧪 Sample Types

Common samples include

- Blood
- Tissue
- Cell lines
- FFPE tissue
- Single cells

---

# 🔬 Wet Lab Workflow

```

Sample

↓

RNA Extraction

↓

RNA Quality Check

↓

Library Preparation

↓

cDNA Synthesis

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

Alignment (HISAT2)

↓

BAM

↓

featureCounts

↓

Gene Counts

↓

DESeq2

↓

Differential Expression

↓

Biological Interpretation

```

---

# 🐧 Linux Environment

## Create Environment

```bash
conda create -n rnaseq python=3.11
```

Activate

```bash
conda activate rnaseq
```

---

# 📦 Install Software

```bash
mamba install \
fastqc \
multiqc \
fastp \
hisat2 \
samtools \
subread
```

---

# Verify Installation

```bash
fastqc --version
hisat2 --version
samtools --version
featureCounts -v
```

---

# 📁 Project Structure

```

RNASeq_Project/

├── raw_data/

├── qc/

├── trimmed/

├── reference/

├── alignment/

├── counts/

├── scripts/

├── results/

└── logs/

```

---

# 📥 Input Files

| File | Description |
|------|-------------|
| FASTQ | Raw Reads |
| Reference Genome | FASTA |
| Annotation | GTF |

---

# 🔧 Analysis Pipeline

## Step 1

Quality Check

```bash
fastqc sample_R1.fastq.gz sample_R2.fastq.gz
```

Output

```
HTML Report

ZIP Report
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

Reference Index

```bash
hisat2-build genome.fa genome_index
```

---

## Step 4

Alignment

```bash
hisat2 \
-x genome_index \
-1 clean_R1.fastq.gz \
-2 clean_R2.fastq.gz \
-S sample.sam
```

---

## Step 5

Convert SAM to BAM

```bash
samtools view -Sb sample.sam > sample.bam
```

---

## Step 6

Sort BAM

```bash
samtools sort sample.bam -o sample.sorted.bam
```

---

## Step 7

Index BAM

```bash
samtools index sample.sorted.bam
```

---

## Step 8

Gene Counts

```bash
featureCounts \
-a annotation.gtf \
-o counts.txt \
sample.sorted.bam
```

---

## Step 9

Differential Expression

Usually performed in R

Common package

```
DESeq2
```

---

# 📊 Output Files

| File | Description |
|------|-------------|
| FASTQ | Raw Reads |
| BAM | Alignment |
| BAI | Index |
| Counts.txt | Gene Counts |
| DEGs | Differentially Expressed Genes |

---

# 🏥 Applications

- Cancer Research
- Biomarker Discovery
- Drug Response
- Precision Medicine
- Immunology
- Neuroscience
- Plant Biology

---

# ⭐ Advantages

- Measures gene expression
- Detects novel transcripts
- Detects splice variants
- High sensitivity
- Genome-wide analysis

---

# ⚠ Limitations

- RNA degradation affects results
- Requires high-quality RNA
- Complex data analysis
- Batch effects

---

# 🌍 Real Example

Researchers compare

Healthy

vs

Breast Cancer

samples.

RNA-Seq identifies

- Upregulated genes
- Downregulated genes
- Cancer biomarkers

These genes may become diagnostic markers or therapeutic targets.

---

# 🧠 Interview Corner

### Why is HISAT2 used instead of BWA?

Because RNA contains splice junctions.

HISAT2 is splice-aware.

BWA is designed primarily for genomic DNA alignment.

---

### Why do we use featureCounts?

To count how many reads map to each gene.

---

### What is Differential Expression?

Comparing gene expression between two biological conditions.

---

# ⭐ Quick Revision

✅ RNA → cDNA

✅ Sequencing

✅ Alignment

✅ Gene Counts

✅ DESeq2

✅ Differential Expression

---

# 🚀 Next Lesson

Metagenomics
