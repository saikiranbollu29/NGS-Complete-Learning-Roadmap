# 🧬 Whole Exome Sequencing (WES)

---

# 📖 Introduction

The human genome consists of approximately **3.2 billion base pairs**, but only **1–2%** of this genome contains **protein-coding regions**, known as **exons**. Although exons represent a small fraction of the genome, they contain a large proportion of known disease-causing mutations.

Whole Exome Sequencing (WES) focuses only on these coding regions, making it a cost-effective approach for identifying genetic variants associated with inherited disorders and many other diseases.

---

# 🧬 Definition

**Whole Exome Sequencing (WES)** is a Next-Generation Sequencing (NGS) technique that sequences only the **protein-coding regions (exons)** of the genome after enriching them through an **exome capture** process.

Unlike Whole Genome Sequencing (WGS), WES does not sequence most non-coding regions.

---

# 🎯 Objectives

The main objectives of WES are:

- Identify disease-causing variants in coding regions.
- Diagnose rare genetic disorders.
- Detect pathogenic mutations.
- Support clinical genetic testing.
- Discover novel coding variants.
- Study inherited diseases.

---

# ❓ Why Do We Need WES?

Although exons account for only **1–2%** of the genome, they contain approximately **85% of currently known disease-causing variants**.

Sequencing only exons:

- Reduces sequencing cost.
- Generates less data.
- Simplifies analysis.
- Provides high coverage of clinically important regions.

---

# 🧬 What Does WES Sequence?

Whole Exome Sequencing mainly targets:

- Protein-coding exons
- Exon–intron boundaries (depending on the capture kit)

It generally does **not** cover:

- Introns
- Promoters
- Enhancers
- Most intergenic regions

---

# 🧪 Sample Requirements

Common samples include:

- Peripheral blood
- Saliva
- Buccal swab
- Fresh tissue
- Cell culture

High-quality genomic DNA is required for successful exome capture.

---

# 🧫 Library Preparation

Library preparation for WES includes:

1. DNA extraction
2. DNA fragmentation
3. End repair
4. Adapter ligation
5. PCR amplification (if required)
6. **Exome capture using probe-based enrichment**
7. Library quality control

---

# ⚙ Principle

The key feature of WES is **target enrichment**.

Instead of sequencing the entire genome, DNA fragments corresponding to exons are captured using biotinylated probes (capture probes). These enriched fragments are then sequenced using an NGS platform.

---

# 🔬 Step-by-Step Workflow

```
Patient Sample
      │
      ▼
DNA Extraction
      │
      ▼
DNA QC
      │
      ▼
DNA Fragmentation
      │
      ▼
Adapter Ligation
      │
      ▼
Exome Capture
      │
      ▼
Library QC
      │
      ▼
NGS Sequencing
      │
      ▼
FASTQ
      │
      ▼
FastQC
      │
      ▼
Read Trimming
      │
      ▼
Alignment
      │
      ▼
BAM
      │
      ▼
Variant Calling
      │
      ▼
VCF
      │
      ▼
Variant Annotation
      │
      ▼
Clinical Interpretation
```

---

# 💻 Bioinformatics Pipeline

| Step | Common Tools |
|------|--------------|
| Quality Control | FastQC, MultiQC |
| Trimming | Fastp, Trimmomatic |
| Alignment | BWA-MEM |
| BAM Processing | SAMtools, Picard |
| Variant Calling | GATK, DeepVariant |
| Annotation | ANNOVAR, VEP, SnpEff |

---

# 💻 Linux Commands (Example Pipeline)

## 1. Quality Check

```bash
fastqc sample_R1.fastq.gz sample_R2.fastq.gz
```

**Purpose:** Assess the quality of raw sequencing reads.

---

## 2. Read Trimming

```bash
fastp \
-i sample_R1.fastq.gz \
-I sample_R2.fastq.gz \
-o clean_R1.fastq.gz \
-O clean_R2.fastq.gz
```

**Purpose:** Remove adapters and low-quality bases.

---

## 3. Alignment

```bash
bwa mem reference.fa \
clean_R1.fastq.gz \
clean_R2.fastq.gz \
> sample.sam
```

**Purpose:** Align sequencing reads to the reference genome.

---

## 4. Convert SAM to BAM

```bash
samtools view -Sb sample.sam > sample.bam
```

**Purpose:** Convert text-based SAM to compressed BAM format.

---

## 5. Sort BAM

```bash
samtools sort sample.bam -o sample.sorted.bam
```

**Purpose:** Sort alignments by genomic coordinates.

---

## 6. Index BAM

```bash
samtools index sample.sorted.bam
```

**Purpose:** Create a BAM index (.bai) for rapid access.

---

# 📂 Input Files

- DNA sample
- Reference genome (FASTA)
- FASTQ files

---

# 📂 Output Files

| File | Description |
|------|-------------|
| FASTQ | Raw reads |
| BAM | Aligned reads |
| BAI | BAM index |
| VCF | Detected variants |
| Annotated VCF | Biologically interpreted variants |

---

# 📊 Variants Detected

WES can identify:

- SNVs
- SNPs
- Small insertions
- Small deletions

It has limited ability to detect:

- Structural variants
- Large CNVs
- Non-coding variants

---

# 🏥 Clinical Applications

- Rare disease diagnosis
- Developmental disorders
- Intellectual disability
- Neuromuscular disorders
- Inherited metabolic diseases
- Hereditary cancers

---

# 🔬 Research Applications

- Gene discovery
- Disease gene identification
- Population genetics
- Functional genomics

---

# 📈 Advantages

- Lower cost than WGS
- High coverage of coding regions
- Smaller data size
- Easier analysis
- Widely used in clinical genomics

---

# ⚠ Limitations

- Misses most non-coding variants
- Depends on capture efficiency
- Limited detection of structural variants
- Some exons may have poor coverage

---

# 🌍 Real Case Study

A child with unexplained developmental delay undergoes Whole Exome Sequencing after routine genetic tests fail to identify the cause.

A pathogenic mutation is found in the coding region of a gene associated with a rare neurodevelopmental disorder, leading to a confirmed diagnosis and appropriate genetic counseling.

---

# 🧠 Interview Questions

1. What is Whole Exome Sequencing?
2. Why does WES focus only on exons?
3. What is exome capture?
4. Why is WES cheaper than WGS?
5. What are the limitations of WES?
6. When would you choose WES instead of WGS?
7. What variants can WES detect?

---

# ⭐ Key Points to Remember

- WES sequences only the coding regions of the genome.
- Exons represent about 1–2% of the genome but contain many known disease-causing variants.
- WES uses an exome capture step before sequencing.
- WES is less expensive and generates less data than WGS.
- WES is widely used in clinical diagnostics and rare disease research.

---

# 📚 References

1. National Human Genome Research Institute (NHGRI)
2. Illumina – Whole Exome Sequencing
3. Nature Reviews Genetics
4. Genome Research
