# 🧬 BCFtools – Variant Calling & VCF Processing

> [!NOTE]
> **Module 4 • Lesson 7**
>
> Learn how to identify DNA variants from aligned sequencing data using BCFtools. This lesson covers variant calling, VCF files, filtering, statistics, and real-world workflows.

---

# 🧬 Pipeline Position

```text
FASTQ
   │
   ▼
FastQC
   │
   ▼
Fastp
   │
   ▼
BWA
   │
   ▼
Samtools
   │
   ▼
BCFtools   ← You are here
   │
   ▼
Variant Annotation
   │
   ▼
Clinical Interpretation
```

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand variant calling.
- Learn how BCFtools works.
- Generate VCF files.
- Filter variants.
- Interpret VCF columns.
- Calculate variant statistics.
- Prepare variants for annotation.

---

# 📚 Prerequisites

- FastQC
- Fastp
- BWA
- Samtools

---

# 💡 Why Variant Calling?

Sequencing reads are aligned to a reference genome.

Example

Reference

```
A T C G A T C
```

Sample

```
A T T G A T C
```

Difference

```
Reference

C

↓

Sample

T
```

This difference is called a **variant**.

Variant calling identifies these differences automatically.

---

# 📌 What is a Variant?

A variant is any DNA sequence difference between a sample and the reference genome.

Common types include:

- SNP (Single Nucleotide Polymorphism)
- Insertion (INS)
- Deletion (DEL)
- Multi-Nucleotide Variant (MNV)

---

# 📌 What is a SNP?

A change in a single nucleotide.

Example

Reference

```
A
```

Sample

```
G
```

A → G

---

# 📌 What is an Indel?

Insertion

Reference

```
ATCG
```

Sample

```
ATCCG
```

↓

Insertion

---

Deletion

Reference

```
ATCG
```

Sample

```
ATG
```

↓

Deletion

---

# 📌 What is Variant Calling?

Variant calling compares aligned reads with the reference genome to identify sequence differences.

Input:

- Reference genome
- Sorted BAM
- BAM index

Output:

- VCF file

---

# 📌 What is BCFtools?

BCFtools is a toolkit for:

- Variant calling
- VCF processing
- Filtering
- Statistics
- Format conversion

It is commonly used with Samtools.

---

# 📌 Installation

```bash
mamba install bcftools -c bioconda
```

Verify

```bash
bcftools --version
```

---

# 📌 Input

```text
reference.fa

sample.sorted.bam

sample.sorted.bam.bai
```

---

# 📌 Output

```text
variants.vcf
```

or

```text
variants.vcf.gz
```

---

# 📌 Step 1 – Generate mpileup

```bash
bcftools mpileup \
-f reference.fa \
sample.sorted.bam \
-o variants.bcf
```

Explanation

```
-f

↓

Reference genome
```

---

# 📌 Step 2 – Call Variants

```bash
bcftools call \
-m \
-v \
-Ov \
-o variants.vcf \
variants.bcf
```

Options

| Option | Meaning |
|---------|----------|
| `-m` | Multiallelic caller |
| `-v` | Variant sites only |
| `-Ov` | Output VCF |

---

# 📌 One-Step Workflow

```bash
bcftools mpileup \
-f reference.fa \
sample.sorted.bam \
| bcftools call \
-m \
-v \
-Ov \
-o variants.vcf
```

---

# 📌 Compress VCF

```bash
bgzip variants.vcf
```

Output

```text
variants.vcf.gz
```

---

# 📌 Index VCF

```bash
tabix -p vcf variants.vcf.gz
```

Output

```text
variants.vcf.gz.tbi
```

---

# 📌 View Variants

```bash
bcftools view variants.vcf
```

---

# 📌 Count Variants

```bash
bcftools view \
-H variants.vcf \
| wc -l
```

---

# 📌 Filter by Quality

Keep variants with QUAL ≥ 30

```bash
bcftools filter \
-i 'QUAL>=30' \
variants.vcf \
-o high_quality.vcf
```

---

# 📌 Filter by Read Depth

Keep variants with depth ≥ 10

```bash
bcftools filter \
-i 'DP>=10' \
variants.vcf \
-o filtered.vcf
```

---

# 📌 Understanding VCF Columns

Example

```text
#CHROM POS ID REF ALT QUAL FILTER INFO
```

| Column | Meaning |
|----------|----------|
| CHROM | Chromosome |
| POS | Position |
| ID | Variant ID |
| REF | Reference base |
| ALT | Alternate base |
| QUAL | Variant quality |
| FILTER | PASS/FAIL |
| INFO | Additional information |

---

# 📌 Important INFO Fields

| Field | Meaning |
|---------|---------|
| DP | Read Depth |
| AC | Allele Count |
| AF | Allele Frequency |
| MQ | Mapping Quality |

---

# 📊 Pipeline Example

```
Reference

↓

BWA

↓

SAM

↓

Samtools

↓

Sorted BAM

↓

BCFtools mpileup

↓

Variant Calling

↓

VCF

↓

Filtering

↓

Annotation
```

---

# 🤖 Bash Automation

```bash
#!/bin/bash

REFERENCE="reference/genome.fa"

mkdir -p variants

for bam in alignment/*.sorted.bam
do

sample=$(basename "$bam" .sorted.bam)

bcftools mpileup \
-f "$REFERENCE" \
"$bam" \
| bcftools call \
-m \
-v \
-Ov \
-o variants/${sample}.vcf

done

echo "Variant calling completed."
```

---

# 🧪 Hands-on Practice

```bash
bcftools mpileup \
-f reference/genome.fa \
alignment/sample.sorted.bam \
| bcftools call \
-m \
-v \
-Ov \
-o variants.vcf
```

---

# 🚨 Common Errors

## Error

```
Reference not found
```

Check

```bash
ls reference/
```

---

## Error

```
BAM index missing
```

Create index

```bash
samtools index sample.sorted.bam
```

---

## Error

```
bcftools: command not found
```

Activate environment

```bash
conda activate ngs
```

---

# 🧠 Interview Questions

### ❓ What is variant calling?

The process of identifying DNA sequence differences between a sample and the reference genome.

---

### ❓ What is a VCF file?

A Variant Call Format (VCF) file stores information about detected genetic variants.

---

### ❓ What is a SNP?

A change in a single nucleotide.

---

### ❓ Why do we filter variants?

To remove low-confidence or poor-quality variant calls before downstream analysis.

---

### ❓ What does QUAL represent?

The confidence score assigned to a variant call. Higher values generally indicate greater confidence.

---

### ❓ What is DP?

DP (Depth) represents the number of sequencing reads covering a genomic position.

---

# 📝 Lesson Summary

- BCFtools performs variant calling from aligned sequencing data.
- The primary output is a VCF file.
- Variants can be filtered based on quality and read depth.
- VCF files contain chromosome, position, reference allele, alternate allele, and additional annotations.
- Filtered variants are typically passed to annotation tools for biological interpretation.

---

# ⚡ Quick Revision

| Step | Command |
|------|----------|
| Generate pileup | `bcftools mpileup` |
| Call variants | `bcftools call` |
| View variants | `bcftools view` |
| Filter variants | `bcftools filter` |
| Compress VCF | `bgzip` |
| Index VCF | `tabix` |

---

# 📚 References

- BCFtools Documentation
- HTSlib Documentation
- VCF Specification
- Danecek et al. (2021), Twelve years of SAMtools and BCFtools

---

# ➡️ Next Lesson

**GATK – Best Practices for Variant Discovery (HaplotypeCaller, BQSR, Variant Filtering)**
