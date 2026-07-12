# 📊 MultiQC – Aggregating NGS Quality Reports

> [!NOTE]
> **Module 4 • Lesson 3**
>
> Learn how to combine multiple FastQC and other bioinformatics reports into a single interactive HTML report using MultiQC.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand the purpose of MultiQC.
- Generate a single report from multiple FastQC outputs.
- Interpret summary statistics.
- Use MultiQC in real NGS workflows.
- Automate report generation.

---

# 📚 Prerequisites

- Linux Basics
- FastQC
- Conda & Mamba

---

# 💡 Why Do We Need MultiQC?

Imagine sequencing:

- 10 samples
- 50 samples
- 500 samples

FastQC generates one report for every sample.

Example

```text
sample1_fastqc.html

sample2_fastqc.html

sample3_fastqc.html

...

sample500_fastqc.html
```

Opening hundreds of reports manually is inefficient.

MultiQC solves this by creating **one summary report**.

---

# 📌 What is MultiQC?

MultiQC is a reporting tool that scans analysis folders and combines outputs from many bioinformatics programs into one interactive HTML report.

It supports dozens of tools including:

- FastQC
- Fastp
- HISAT2
- STAR
- BWA
- Samtools
- Picard
- Qualimap
- Salmon
- Kallisto
- GATK
- BCFtools

---

# 📌 Where Does MultiQC Fit?

Typical NGS Workflow

```text
FASTQ

↓

FastQC

↓

MultiQC

↓

Review Overall Quality

↓

Trimming

↓

Alignment

↓

Variant Calling
```

---

# 📌 Install MultiQC

```bash
mamba install multiqc -c bioconda
```

Verify installation

```bash
multiqc --version
```

Example

```text
multiqc, version 1.xx
```

---

# 📌 Input

MultiQC reads output files from supported tools.

Example

```text
qc/

sample1_fastqc.zip

sample2_fastqc.zip

sample3_fastqc.zip
```

---

# 📌 Basic Command

Generate a report.

```bash
multiqc qc/
```

---

# Specify Output Folder

```bash
multiqc qc/ -o multiqc_report/
```

---

# Rename Report

```bash
multiqc qc/ -n RNASeq_QC_Report.html
```

---

# Force Overwrite Existing Report

```bash
multiqc qc/ --force
```

---

# 📂 Example Project

```text
RNASeq_Project/

raw_data/

qc/

sample1_fastqc.zip

sample2_fastqc.zip

sample3_fastqc.zip
```

Run

```bash
multiqc qc/
```

---

# 📌 Output Files

MultiQC creates

```text
multiqc_report.html

multiqc_data/
```

---

# Understanding the Output

### multiqc_report.html

Interactive report viewed in a web browser.

---

### multiqc_data/

Contains parsed summary tables used to build the report.

Useful for downstream analyses and automation.

---

# 📌 Major Sections of a MultiQC Report

## General Statistics

Provides an overview of all samples.

Includes:

- Total reads
- GC content
- Sequence length
- Duplication levels
- Quality metrics

---

## FastQC Summary

Displays PASS, WARN, and FAIL results for each FastQC module across all samples.

---

## Per Base Quality

Compares quality scores across all samples.

---

## GC Content

Shows GC distribution for every sample.

Useful for detecting contamination or unexpected bias.

---

## Adapter Content

Displays adapter contamination across samples.

If adapter levels are high,

perform trimming before alignment.

---

## Sequence Duplication

Summarizes duplication rates across all samples.

Interpret results based on the experiment.

---

# 📌 Important MultiQC Options

| Option | Purpose |
|----------|----------|
| `-o` | Output directory |
| `-n` | Rename report |
| `--force` | Overwrite existing reports |
| `--title` | Custom report title |
| `--interactive` | Enable interactive report |

---

# 🧬 Real NGS Workflow

```text
FASTQ

↓

FastQC

↓

FastQC Reports

↓

MultiQC

↓

One HTML Report

↓

Review Quality

↓

Proceed to Trimming or Alignment
```

---

# 🤖 Bash Automation

```bash
#!/bin/bash

mkdir -p qc

echo "Running FastQC..."

fastqc raw_data/*.fastq.gz -o qc -t 8

echo "Generating MultiQC report..."

multiqc qc -o qc

echo "Pipeline completed."
```

Make executable

```bash
chmod +x qc_pipeline.sh
```

Run

```bash
./qc_pipeline.sh
```

---

# 🧪 Hands-on Practice

Create project

```bash
mkdir MultiQC_Practice

cd MultiQC_Practice

mkdir raw_data qc
```

Run FastQC

```bash
fastqc raw_data/*.fastq.gz -o qc/
```

Generate MultiQC report

```bash
multiqc qc/
```

Open

```text
multiqc_report.html
```

in your browser.

---

# 🚨 Common Errors

## Error

```text
multiqc: command not found
```

Solution

```bash
conda activate ngs

which multiqc
```

---

## Error

```text
No analysis results found
```

Reason

MultiQC cannot find supported result files.

Check

```bash
ls qc/
```

Ensure FastQC completed successfully.

---

## Error

```text
Permission denied
```

Check file permissions

```bash
ls -l qc/
```

---

# 🧠 Interview Questions

### ❓ What is MultiQC?

A tool that combines results from multiple bioinformatics analyses into one interactive report.

---

### ❓ Why is MultiQC useful?

It allows researchers to review quality metrics for many samples simultaneously instead of opening individual reports.

---

### ❓ Does MultiQC perform quality control?

No.

It summarizes the outputs generated by other tools such as FastQC.

---

### ❓ What are the main output files?

- `multiqc_report.html`
- `multiqc_data/`

---

### ❓ Can MultiQC summarize tools other than FastQC?

Yes. It supports many bioinformatics tools, including aligners, quantification tools, QC software, and variant analysis programs.

---

# 📝 Lesson Summary

- MultiQC aggregates reports from multiple bioinformatics tools.
- It creates a single interactive HTML report.
- It is commonly used after FastQC.
- It simplifies quality assessment for large sequencing projects.
- It is a standard component of modern NGS pipelines.

---

# ⚡ Quick Revision

| Topic | Key Point |
|--------|-----------|
| Input | FastQC and other tool outputs |
| Output | HTML report + data folder |
| Main Use | Aggregate QC results |
| Used After | FastQC |
| Next Step | Trimming or Alignment |

---

# 📚 References

- MultiQC Documentation
- Bioinformatics Data Skills (Book)
- Babraham Bioinformatics

---

# ➡️ Next Lesson

**Fastp – Read Filtering, Adapter Trimming & Quality Control**
