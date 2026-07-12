# 🧬 GATK – Best Practices for Variant Discovery

> [!NOTE]
> **Module 4 • Lesson 8**
>
> Learn how GATK performs high-quality germline variant discovery using the Broad Institute Best Practices workflow. This lesson covers duplicate marking, Base Quality Score Recalibration (BQSR), HaplotypeCaller, variant filtering, and clinical applications.

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
GATK   ← You are here
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

- Understand GATK Best Practices.
- Learn why duplicate marking is important.
- Understand Base Quality Score Recalibration (BQSR).
- Perform variant calling with HaplotypeCaller.
- Generate GVCF and VCF files.
- Apply hard filters to variants.
- Prepare variants for annotation.

---

# 📚 Prerequisites

- FastQC
- Fastp
- BWA
- Samtools
- Basic understanding of VCF files

---

# 💡 Why GATK?

Different variant callers may produce different results.

GATK focuses on:

- High accuracy
- Reduced false positives
- Clinical-grade workflows
- Reproducibility

It is widely used for:

- Whole Genome Sequencing (WGS)
- Whole Exome Sequencing (WES)
- Germline variant discovery

---

# 📌 What is GATK?

The Genome Analysis Toolkit (GATK) is a software package developed by the Broad Institute for discovering and genotyping genetic variants from NGS data.

---

# 📌 GATK Best Practices Workflow

```text
FASTQ

↓

FastQC

↓

Fastp

↓

BWA-MEM

↓

Sorted BAM

↓

Mark Duplicates

↓

BQSR

↓

HaplotypeCaller

↓

GVCF / VCF

↓

Variant Filtering

↓

Annotation
```

---

# 📌 Step 1 – Mark Duplicates

PCR amplification can create duplicate reads.

These duplicates may bias variant calling.

Common tool:

```text
GATK MarkDuplicatesSpark
```

or

```text
Picard MarkDuplicates
```

---

# 📌 Step 2 – Base Quality Score Recalibration (BQSR)

Sequencing machines assign quality scores to each base.

Sometimes these scores are systematically inaccurate.

BQSR recalibrates base quality scores using known high-confidence variant sites.

Benefits:

- Improves variant calling accuracy.
- Reduces false-positive calls.

---

# 📌 Step 3 – HaplotypeCaller

HaplotypeCaller is the core GATK variant caller.

Unlike simple pileup-based methods, it performs local reassembly of reads in candidate variant regions.

Advantages:

- Better detection of indels.
- Higher accuracy in complex genomic regions.
- Improved genotype assignment.

---

# 📌 Installation

```bash
mamba install gatk4 -c bioconda
```

Verify

```bash
gatk --version
```

---

# 📌 Input

```text
reference.fa

sample.sorted.bam

sample.sorted.bam.bai
```

---

# 📌 Create Sequence Dictionary

Some GATK tools require a sequence dictionary.

```bash
gatk CreateSequenceDictionary \
-R reference.fa
```

Output

```text
reference.dict
```

---

# 📌 Index the Reference

```bash
samtools faidx reference.fa
```

Output

```text
reference.fa.fai
```

---

# 📌 Run HaplotypeCaller

```bash
gatk HaplotypeCaller \
-R reference.fa \
-I sample.sorted.bam \
-O sample.vcf.gz
```

---

# 📌 Generate GVCF

For joint genotyping across multiple samples:

```bash
gatk HaplotypeCaller \
-R reference.fa \
-I sample.sorted.bam \
-ERC GVCF \
-O sample.g.vcf.gz
```

---

# 📌 What is a GVCF?

A Genomic VCF (GVCF) stores information about both variant and non-variant regions.

It is used for joint genotyping of multiple samples.

---

# 📌 Variant Filtering

Hard-filter SNPs

```bash
gatk VariantFiltration \
-V sample.vcf.gz \
-O filtered.vcf.gz \
--filter-expression "QD < 2.0 || FS > 60.0 || MQ < 40.0" \
--filter-name "BasicFilter"
```

---

# 📌 Important Quality Metrics

| Metric | Meaning |
|---------|---------|
| QD | Quality by Depth |
| FS | Strand Bias |
| MQ | Mapping Quality |
| DP | Read Depth |
| QUAL | Variant Confidence |

---

# 📊 BCFtools vs GATK

| Feature | BCFtools | GATK |
|---------|----------|------|
| Speed | Faster | Slower |
| Accuracy | High | Very High |
| Local Assembly | No | Yes |
| Clinical Use | Common | Gold Standard |
| GVCF Support | Limited | Excellent |

---

# 🧬 Example Project

```text
WES_Project/

reference/

reference.fa

alignment/

sample.sorted.bam

variants/
```

Run

```bash
gatk HaplotypeCaller \
-R reference/reference.fa \
-I alignment/sample.sorted.bam \
-O variants/sample.vcf.gz
```

---

# 🤖 Bash Automation

```bash
#!/bin/bash

REFERENCE="reference/reference.fa"

mkdir -p variants

for bam in alignment/*.sorted.bam
do

sample=$(basename "$bam" .sorted.bam)

gatk HaplotypeCaller \
-R "$REFERENCE" \
-I "$bam" \
-O "variants/${sample}.vcf.gz"

done

echo "Variant calling completed."
```

---

# 🧬 Clinical & Research Perspective

Example:

```text
Patient DNA

↓

Sequencing

↓

GATK Variant Calling

↓

BRCA1 Variant Found

↓

Variant Annotation
(VEP / ANNOVAR / SnpEff)

↓

ClinVar
gnomAD
COSMIC

↓

ACMG Classification

↓

Clinical Report
```

GATK identifies candidate variants. Their biological and clinical significance is determined in later annotation and interpretation steps.

---

# 🚨 Common Errors

## Error

```text
Reference dictionary missing
```

Solution

```bash
gatk CreateSequenceDictionary -R reference.fa
```

---

## Error

```text
Reference index missing
```

Solution

```bash
samtools faidx reference.fa
```

---

## Error

```text
gatk: command not found
```

Solution

```bash
conda activate ngs

which gatk
```

---

# 🧠 Interview Questions

### ❓ What is GATK?

A toolkit developed by the Broad Institute for high-quality variant discovery and genotyping.

---

### ❓ Why is HaplotypeCaller preferred?

Because it performs local haplotype assembly, improving accuracy, especially for indels.

---

### ❓ What is BQSR?

Base Quality Score Recalibration adjusts systematic errors in sequencing quality scores to improve variant calling.

---

### ❓ What is a GVCF?

A genomic VCF that records both variant and non-variant sites, enabling joint genotyping across multiple samples.

---

### ❓ Why mark duplicates?

To reduce bias introduced by PCR duplicates and improve variant calling accuracy.

---

### ❓ What is the difference between BCFtools and GATK?

BCFtools is lightweight and fast, while GATK uses more advanced algorithms such as local assembly and is widely adopted for clinical-grade germline variant calling.

---

# 📝 Lesson Summary

- GATK is a widely used toolkit for germline variant discovery.
- Best Practices include duplicate marking, BQSR, HaplotypeCaller, and variant filtering.
- HaplotypeCaller performs local assembly for improved accuracy.
- GVCFs are used for joint genotyping.
- Filtered variants are ready for annotation and clinical interpretation.

---

# ⚡ Quick Revision

| Step | Tool |
|------|------|
| Duplicate Removal | MarkDuplicates |
| Quality Recalibration | BQSR |
| Variant Calling | HaplotypeCaller |
| Output | VCF / GVCF |
| Filtering | VariantFiltration |
| Next Step | Variant Annotation |

---

# 📚 References

- GATK Documentation
- Broad Institute GATK Best Practices
- Van der Auwera & O'Connor, Genomics in the Cloud
- McKenna et al. (2010), The Genome Analysis Toolkit

---

# ➡️ Next Lesson

**Variant Annotation – VEP, ANNOVAR & SnpEff (Gene Annotation, Functional Impact & Clinical Interpretation)**
