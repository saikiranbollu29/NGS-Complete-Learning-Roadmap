# 🌍 Whole Genome Sequencing (WGS)

---

# 📖 Introduction

The human genome contains approximately **3.2 billion base pairs** distributed across **23 pairs of chromosomes**. These DNA sequences contain all the genetic information required for the growth, development, and functioning of an individual.

Many genetic diseases are caused by variations that occur throughout the genome—not only in protein-coding regions but also in non-coding regulatory regions.

To identify these variations comprehensively, scientists use **Whole Genome Sequencing (WGS)**.

Whole Genome Sequencing is considered the most comprehensive DNA sequencing approach because it analyzes **the entire genome**, including coding and non-coding regions.

---

# 🧬 Definition

**Whole Genome Sequencing (WGS)** is a Next-Generation Sequencing (NGS) technique used to determine the complete DNA sequence of an organism's genome by sequencing all genomic DNA, including coding regions (exons), non-coding regions (introns), promoters, enhancers, regulatory elements, and intergenic regions.

Unlike targeted sequencing or Whole Exome Sequencing (WES), WGS does not selectively capture specific genomic regions. Instead, it provides a complete view of the genome.

---

# 🎯 Objectives of WGS

The main objectives of Whole Genome Sequencing are:

- Identify genetic variants across the entire genome.
- Detect disease-causing mutations.
- Discover novel genetic variants.
- Analyze structural changes in chromosomes.
- Study inherited and acquired genetic disorders.
- Support precision medicine and personalized healthcare.
- Understand evolutionary relationships and population genetics.

---

# 🧬 What Does WGS Sequence?

Whole Genome Sequencing analyzes:

✅ Exons (Protein-coding regions)

✅ Introns (Non-coding regions within genes)

✅ Promoters

✅ Enhancers

✅ Regulatory regions

✅ Intergenic regions

✅ Mitochondrial DNA (usually included)

---

# 🧠 Why is WGS Important?

Many disease-causing variants occur **outside exons**.

Examples include:

- Promoter mutations
- Enhancer mutations
- Structural variants
- Copy number changes
- Chromosomal rearrangements

These variants may be missed by Whole Exome Sequencing.

Therefore, WGS provides the most comprehensive genomic analysis.

---

# ⚙ Principle

Whole Genome Sequencing follows the principle of **Massively Parallel Sequencing**.

Instead of sequencing one DNA fragment at a time, genomic DNA is fragmented into millions of small fragments.

Each fragment is sequenced simultaneously.

The resulting sequencing reads are aligned to a reference genome using bioinformatics software.

Finally, genetic variants are identified and interpreted.

---

# 🔬 Complete WGS Workflow

```
Patient Sample
       │
       ▼
DNA Extraction
       │
       ▼
DNA Quality Control
       │
       ▼
DNA Fragmentation
       │
       ▼
Library Preparation
       │
       ▼
Adapter Ligation
       │
       ▼
Library QC
       │
       ▼
NGS Sequencing
       │
       ▼
FASTQ Files
       │
       ▼
Quality Control
(FastQC)
       │
       ▼
Read Trimming
(Fastp)
       │
       ▼
Alignment
(BWA-MEM)
       │
       ▼
SAM
       │
       ▼
BAM
       │
       ▼
Sorting
       │
       ▼
Indexing
       │
       ▼
Variant Calling
(GATK / DeepVariant)
       │
       ▼
VCF
       │
       ▼
Variant Annotation
(VEP / ANNOVAR)
       │
       ▼
Clinical Interpretation
```

---

# 🧪 Sample Requirements

Common biological samples include:

- Peripheral blood
- Saliva
- Buccal swab
- Fresh tissue
- Frozen tissue
- Cell culture
- FFPE tissue (with limitations)

DNA quality is critical for obtaining reliable sequencing results.

---

# 📦 Library Preparation

Library preparation typically includes:

1. DNA fragmentation
2. End repair
3. A-tailing (platform-dependent)
4. Adapter ligation
5. PCR amplification (optional in some protocols)
6. Library quality assessment

---

# 💻 Bioinformatics Pipeline

Typical software used in WGS analysis:

| Step | Common Tools |
|------|--------------|
| QC | FastQC, MultiQC |
| Trimming | Fastp, Trimmomatic |
| Alignment | BWA-MEM, Bowtie2 |
| BAM Processing | SAMtools, Picard |
| Variant Calling | GATK, DeepVariant, FreeBayes |
| Annotation | ANNOVAR, Ensembl VEP, SnpEff |

---

# 📂 Output Files

| File | Purpose |
|------|----------|
| FASTQ | Raw sequencing reads with quality scores |
| SAM | Text-based alignment file |
| BAM | Binary alignment file |
| BAI | BAM index file |
| VCF | Detected genetic variants |
| Annotated VCF | Variants with biological interpretation |

---

# 📊 Variants Detected

Whole Genome Sequencing can detect:

- Single Nucleotide Variants (SNVs)
- Single Nucleotide Polymorphisms (SNPs)
- Insertions
- Deletions
- Copy Number Variants (CNVs)
- Structural Variants (SVs)
- Chromosomal rearrangements

---

# 🏥 Applications

WGS is widely used in:

- Rare disease diagnosis
- Cancer genomics
- Precision medicine
- Pharmacogenomics
- Population genetics
- Evolutionary biology
- Infectious disease surveillance
- Newborn screening (selected settings)

---

# ✅ Advantages

- Complete genome coverage
- Detects coding and non-coding variants
- Identifies structural variants
- Detects novel mutations
- Comprehensive genomic information
- Supports personalized medicine

---

# ❌ Limitations

- Higher cost than WES or targeted sequencing
- Large data storage requirements
- Computationally intensive
- Complex interpretation
- Longer analysis time

---

# 🌍 Real-World Example

A child with unexplained developmental delay undergoes several genetic tests without a diagnosis.

Whole Genome Sequencing identifies a pathogenic variant in a regulatory region that affects gene expression. This variant would not have been detected by Whole Exome Sequencing because it lies outside the coding regions.

This demonstrates the value of WGS in diagnosing rare genetic disorders.

---

# 💼 Interview Questions

### 1. What is Whole Genome Sequencing?

### 2. Why is WGS considered the most comprehensive sequencing approach?

### 3. What regions are sequenced in WGS?

### 4. What variants can WGS detect?

### 5. Why is WGS more expensive than WES?

### 6. What is the bioinformatics workflow of WGS?

### 7. What are the major clinical applications of WGS?

---

# 🧠 Interview Tip

If asked:

**"Why would you choose WGS instead of WES?"**

A strong answer is:

> WGS sequences the entire genome, including both coding and non-coding regions. It is preferred when disease-causing variants may occur outside exons or when a comprehensive analysis of structural variants, regulatory regions, and novel mutations is required.

---

# 📝 Key Points to Remember

- WGS sequences the complete genome.
- Covers both coding and non-coding DNA.
- Detects almost all classes of genomic variants.
- Generates large datasets requiring bioinformatics analysis.
- Commonly used in research and clinical genomics.

---

# 📚 References

1. National Human Genome Research Institute (NHGRI)
2. Illumina – Whole Genome Sequencing
3. Nature Reviews Genetics
4. Genome Research
5. Genomics by T.A. Brown
