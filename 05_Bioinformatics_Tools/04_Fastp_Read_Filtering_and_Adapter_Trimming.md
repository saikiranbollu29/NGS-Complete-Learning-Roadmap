# ✂️ Fastp – Read Filtering, Adapter Trimming & Quality Control

> [!NOTE]
> **Module 4 • Lesson 4**
>
> Learn how to improve sequencing data quality using Fastp. This tool performs adapter trimming, quality filtering, read correction, and generates quality reports in a single step.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand why trimming is necessary.
- Learn how Fastp works.
- Perform adapter trimming.
- Filter low-quality reads.
- Generate HTML and JSON quality reports.
- Prepare sequencing reads for alignment.

---

# 📚 Prerequisites

- FastQC
- MultiQC
- Linux Basics

---

# 💡 Why Do We Trim Reads?

Raw sequencing reads often contain:

- Adapter sequences
- Low-quality bases
- Poly-G tails (common in some Illumina platforms)
- Poly-X tails
- Short reads
- Reads containing many unknown bases (N)

These problems reduce alignment accuracy and can affect downstream analyses.

---

# 📌 Where Does Fastp Fit?

```text
FASTQ

↓

FastQC

↓

Fastp

↓

FastQC (Again)

↓

Alignment

↓

Variant Calling
```

FastQC evaluates quality.

Fastp improves quality.

A second FastQC confirms that trimming was successful.

---

# 📌 What is Fastp?

Fastp is an all-in-one FASTQ preprocessing tool.

It can:

- Detect adapters automatically
- Trim adapters
- Remove low-quality bases
- Remove short reads
- Filter reads with many N bases
- Generate quality reports

Unlike FastQC, Fastp modifies the sequencing reads.

---

# 📌 Installation

```bash
mamba install fastp -c bioconda
```

Verify:

```bash
fastp --version
```

---

# 📌 Input

```text
sample_R1.fastq.gz

sample_R2.fastq.gz
```

Supports both single-end and paired-end sequencing data.

---

# 📌 Output

Example:

```text
trimmed_R1.fastq.gz

trimmed_R2.fastq.gz

fastp.html

fastp.json
```

---

# 📌 Basic Command (Single-End)

```bash
fastp \
-i sample.fastq.gz \
-o sample_trimmed.fastq.gz
```

---

# 📌 Basic Command (Paired-End)

```bash
fastp \
-i sample_R1.fastq.gz \
-I sample_R2.fastq.gz \
-o trimmed_R1.fastq.gz \
-O trimmed_R2.fastq.gz
```

---

# 📌 Generate Reports

```bash
fastp \
-i sample_R1.fastq.gz \
-I sample_R2.fastq.gz \
-o trimmed_R1.fastq.gz \
-O trimmed_R2.fastq.gz \
-h fastp.html \
-j fastp.json
```

---

# 📌 Important Parameters

| Option | Purpose |
|----------|----------|
| `-i` | Input Read 1 |
| `-I` | Input Read 2 |
| `-o` | Output Read 1 |
| `-O` | Output Read 2 |
| `-h` | HTML report |
| `-j` | JSON report |
| `-w` | Number of threads |
| `--detect_adapter_for_pe` | Auto-detect adapters in paired-end data |
| `--length_required` | Minimum read length |
| `--qualified_quality_phred` | Minimum quality score |

---

# 📌 Example Project

```text
RNASeq_Project/

raw_data/

sample_R1.fastq.gz

sample_R2.fastq.gz

trimmed/

reports/
```

Run:

```bash
fastp \
-i raw_data/sample_R1.fastq.gz \
-I raw_data/sample_R2.fastq.gz \
-o trimmed/sample_R1.trimmed.fastq.gz \
-O trimmed/sample_R2.trimmed.fastq.gz \
-h reports/fastp.html \
-j reports/fastp.json \
-w 8
```

---

# 📊 Fastp Reports

Fastp produces:

### HTML Report

Interactive report showing:

- Before vs After filtering
- Read quality
- Adapter trimming statistics
- GC content
- Read length distribution

---

### JSON Report

Machine-readable summary.

Useful for:

- Automation
- MultiQC
- Pipelines

---

# 📌 Before vs After

Fastp compares:

| Before | After |
|----------|---------|
| Total Reads | Remaining Reads |
| Q20 | Improved |
| Q30 | Improved |
| Adapter Bases | Removed |
| Low-quality Bases | Removed |

---

# 📌 Automatic Adapter Detection

Fastp can automatically detect Illumina adapters.

Example:

```bash
--detect_adapter_for_pe
```

Usually recommended for paired-end sequencing.

---

# 📌 Poly-G Trimming

Some Illumina instruments may generate artificial Poly-G tails.

Fastp detects and removes them automatically when appropriate.

---

# 📌 Quality Filtering

Reads below the specified quality threshold can be filtered.

Example:

```bash
--qualified_quality_phred 20
```

This uses a Phred quality threshold of 20.

---

# 📌 Minimum Read Length

Remove very short reads.

```bash
--length_required 50
```

Reads shorter than 50 bases are discarded.

---

# 🧬 Real NGS Workflow

```text
Raw FASTQ

↓

FastQC

↓

Adapter Detected?

↓

YES

↓

Fastp

↓

Trimmed FASTQ

↓

FastQC Again

↓

Alignment
```

---

# 🤖 Bash Automation

```bash
#!/bin/bash

mkdir -p trimmed reports

for r1 in raw_data/*_R1.fastq.gz
do
    r2=${r1/_R1/_R2}

    sample=$(basename "$r1" _R1.fastq.gz)

    fastp \
    -i "$r1" \
    -I "$r2" \
    -o "trimmed/${sample}_R1.fastq.gz" \
    -O "trimmed/${sample}_R2.fastq.gz" \
    -h "reports/${sample}.html" \
    -j "reports/${sample}.json" \
    --detect_adapter_for_pe \
    -w 8

done
```

---

# 🧪 Hands-on Practice

Project structure

```text
Fastp_Practice/

raw_data/

trimmed/

reports/
```

Run

```bash
fastp \
-i raw_data/sample_R1.fastq.gz \
-I raw_data/sample_R2.fastq.gz \
-o trimmed/sample_R1.fastq.gz \
-O trimmed/sample_R2.fastq.gz \
-h reports/fastp.html \
-j reports/fastp.json
```

---

# 🚨 Common Errors

## Error

```text
fastp: command not found
```

Solution

```bash
conda activate ngs

which fastp
```

---

## Error

```text
Input file not found
```

Check

```bash
ls raw_data/
```

---

## Error

```text
Permission denied
```

Check permissions

```bash
ls -l raw_data/
```

---

# 🧠 Interview Questions

### ❓ Why is Fastp used?

To improve sequencing read quality before alignment.

---

### ❓ What is adapter trimming?

The removal of artificial adapter sequences added during library preparation.

---

### ❓ Does Fastp replace FastQC?

No.

FastQC evaluates sequencing quality, while Fastp improves the reads. They are complementary tools.

---

### ❓ Why run FastQC again after Fastp?

To verify that adapter contamination and low-quality regions have been successfully removed.

---

### ❓ What reports does Fastp generate?

- HTML report
- JSON report

---

# 📝 Lesson Summary

- Fastp is an all-in-one FASTQ preprocessing tool.
- It performs adapter trimming, quality filtering, and read filtering.
- It generates both HTML and JSON reports.
- FastQC is typically run before and after Fastp.
- High-quality reads improve downstream alignment and variant calling.

---

# ⚡ Quick Revision

| Topic | Key Point |
|--------|-----------|
| Input | FASTQ / FASTQ.gz |
| Output | Trimmed FASTQ + HTML + JSON |
| Main Purpose | Read preprocessing |
| Removes | Adapters, low-quality bases, short reads |
| Used Before | Alignment |

---

# 📚 References

- Fastp Documentation
- Chen et al., Fastp: an ultra-fast all-in-one FASTQ preprocessor
- Bioinformatics Data Skills (Book)

---

# ➡️ Next Lesson

**BWA – Burrows-Wheeler Aligner (DNA Sequence Alignment: Theory + Hands-on + Interview Questions)**
