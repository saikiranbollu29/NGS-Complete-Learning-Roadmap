# 🔨 Samtools – Working with SAM, BAM & CRAM Files

> [!NOTE]
> **Module 4 • Lesson 6**
>
> Learn how to manipulate alignment files using Samtools. This lesson covers SAM, BAM, CRAM formats, conversion, sorting, indexing, filtering, statistics, and real-world NGS workflows.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand SAM, BAM and CRAM formats.
- Convert SAM to BAM.
- Sort and index BAM files.
- View alignments.
- Calculate mapping statistics.
- Extract genomic regions.
- Prepare BAM files for downstream analysis.

---

# 📚 Prerequisites

- Linux Basics
- BWA Alignment
- Bash Scripting

---

# 💡 Why Do We Need Samtools?

After alignment using BWA, HISAT2 or STAR,

the output is usually

```
sample.sam
```

SAM files are:

- Very large
- Text-based
- Slow to process

Samtools converts them into compressed binary BAM files for faster analysis.

---

# 🧬 Pipeline Continuation

```
FASTQ

↓

FastQC

↓

Fastp

↓

BWA

↓

SAM

↓

Samtools

↓

BAM

↓

Sorted BAM

↓

Indexed BAM

↓

Variant Calling
```

---

# 📌 What is Samtools?

Samtools is a collection of command-line utilities for manipulating alignment files.

It supports:

- SAM
- BAM
- CRAM

It can:

- Convert
- Sort
- Index
- Filter
- View
- Calculate statistics
- Extract regions

---

# 📌 File Formats

## SAM

Sequence Alignment Map

- Text format
- Human-readable
- Large file size

Example

```text
sample.sam
```

---

## BAM

Binary Alignment Map

- Binary version of SAM
- Compressed
- Faster
- Smaller

Example

```text
sample.bam
```

---

## CRAM

Compressed Reference-oriented Alignment Map

- Even smaller than BAM
- Uses the reference genome for compression
- Saves storage space

Example

```text
sample.cram
```

---

# 📊 Comparison

| Format | Human Readable | Compressed | Common Use |
|---------|---------------|------------|------------|
| SAM | ✅ | ❌ | Intermediate |
| BAM | ❌ | ✅ | Standard |
| CRAM | ❌ | ✅ | Long-term storage |

---

# 📌 Installation

```bash
mamba install samtools -c bioconda
```

Verify

```bash
samtools --version
```

---

# 📌 View SAM File

```bash
samtools view sample.sam
```

---

# View Header Only

```bash
samtools view -H sample.sam
```

---

# Convert SAM → BAM

```bash
samtools view \
-b \
sample.sam \
> sample.bam
```

Explanation

```
-b

↓

Output BAM
```

---

# Convert BAM → SAM

```bash
samtools view \
-h \
sample.bam \
> sample.sam
```

---

# 📌 Sort BAM

Most downstream tools require sorted BAM files.

```bash
samtools sort \
sample.bam \
-o sample.sorted.bam
```

---

# 📌 Index BAM

```bash
samtools index sample.sorted.bam
```

Generated

```text
sample.sorted.bam.bai
```

The index allows rapid access to genomic regions.

---

# 📌 View Alignment Statistics

```bash
samtools flagstat sample.sorted.bam
```

Example Output

```text
100000 reads

98000 mapped

98%
```

---

# 📌 Alignment Summary

```bash
samtools stats sample.sorted.bam
```

Useful for:

- Mapping statistics
- Insert size
- Coverage
- Base composition

---

# 📌 Calculate Coverage

```bash
samtools depth sample.sorted.bam
```

Average depth

```bash
samtools depth sample.sorted.bam \
| awk '{sum+=$3} END {print sum/NR}'
```

---

# 📌 Extract One Chromosome

```bash
samtools view \
sample.sorted.bam \
chr1 \
> chr1.sam
```

---

# Extract BAM Region

```bash
samtools view \
-b \
sample.sorted.bam \
chr17:43044295-43125482 \
> BRCA1.bam
```

---

# 📌 Count Reads

```bash
samtools view \
-c \
sample.sorted.bam
```

---

# Count Mapped Reads

```bash
samtools view \
-c \
-F 4 \
sample.sorted.bam
```

---

# Count Unmapped Reads

```bash
samtools view \
-c \
-f 4 \
sample.sorted.bam
```

---

# 📌 Quick File Check

```bash
samtools quickcheck sample.sorted.bam
```

Useful for detecting truncated or corrupted BAM files.

---

# 📌 Important Commands

| Command | Purpose |
|----------|----------|
| view | Display or convert alignments |
| sort | Sort BAM |
| index | Create BAM index |
| flagstat | Mapping statistics |
| stats | Detailed statistics |
| depth | Per-base coverage |
| quickcheck | Validate BAM integrity |

---

# 🧬 Example Project

```text
WGS_Project/

alignment/

sample.sam

sample.bam

sample.sorted.bam

sample.sorted.bam.bai
```

---

# Complete Workflow

Convert

```bash
samtools view -b sample.sam > sample.bam
```

Sort

```bash
samtools sort sample.bam \
-o sample.sorted.bam
```

Index

```bash
samtools index sample.sorted.bam
```

Statistics

```bash
samtools flagstat sample.sorted.bam
```

---

# 🤖 Bash Automation

```bash
#!/bin/bash

mkdir -p alignment

for sam in alignment/*.sam
do

sample=$(basename "$sam" .sam)

samtools view \
-b "$sam" \
> alignment/${sample}.bam

samtools sort \
alignment/${sample}.bam \
-o alignment/${sample}.sorted.bam

samtools index \
alignment/${sample}.sorted.bam

done

echo "Samtools pipeline completed."
```

---

# 🧪 Hands-on Practice

Project

```text
WGS_Practice/

alignment/

sample.sam
```

Commands

```bash
samtools view \
-b sample.sam \
> sample.bam
```

```bash
samtools sort \
sample.bam \
-o sample.sorted.bam
```

```bash
samtools index \
sample.sorted.bam
```

```bash
samtools flagstat \
sample.sorted.bam
```

---

# 🚨 Common Errors

## Error

```text
[E::idx_find_and_load]
```

Reason

BAM index missing.

Solution

```bash
samtools index sample.sorted.bam
```

---

## Error

```text
samtools: command not found
```

Solution

```bash
conda activate ngs

which samtools
```

---

## Error

```text
file is not coordinate sorted
```

Solution

Sort first.

```bash
samtools sort \
sample.bam \
-o sample.sorted.bam
```

---

# 🧠 Interview Questions

### ❓ What is the difference between SAM and BAM?

SAM is a text-based alignment format, while BAM is its compressed binary equivalent.

---

### ❓ Why sort BAM files?

Sorting organizes reads by genomic coordinates, which is required for indexing and many downstream analyses.

---

### ❓ Why create a BAM index?

An index enables rapid random access to specific genomic regions without reading the entire file.

---

### ❓ What does `samtools flagstat` provide?

A summary of alignment statistics, including total reads, mapped reads, properly paired reads, duplicates (if marked), and mapping percentages.

---

### ❓ What is the difference between BAM and CRAM?

CRAM is a more compressed format that uses the reference genome during compression, reducing storage requirements compared with BAM.

---

# 📝 Lesson Summary

- Samtools is the standard toolkit for manipulating alignment files.
- Convert SAM to BAM for efficient storage and processing.
- Sort and index BAM files before downstream analyses.
- Use `flagstat`, `stats`, and `depth` for quality assessment.
- Indexed BAM files enable rapid genomic region access.

---

# ⚡ Quick Revision

| Step | Command |
|------|----------|
| SAM → BAM | `samtools view -b` |
| Sort BAM | `samtools sort` |
| Index BAM | `samtools index` |
| Statistics | `samtools flagstat` |
| Coverage | `samtools depth` |
| Count Reads | `samtools view -c` |

---

# 📚 References

- Samtools Documentation
- HTSlib Documentation
- SAM/BAM Format Specification
- Li H. et al. (2009), The Sequence Alignment/Map format and SAMtools

---

# ➡️ Next Lesson

**BCFtools – Variant Calling, Filtering & VCF Processing**
