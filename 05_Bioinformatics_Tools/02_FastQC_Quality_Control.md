# 🔬 FastQC – Sequencing Quality Control

> [!NOTE]
> **Module 4 • Lesson 2**
>
> Learn how to perform quality control (QC) on raw sequencing reads using FastQC. Quality assessment is the first step in every NGS workflow.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand why sequencing quality control is important.
- Learn what FastQC does.
- Interpret FastQC reports.
- Identify common sequencing problems.
- Run FastQC on FASTQ files.
- Automate FastQC for multiple samples.

---

# 📚 Prerequisites

- Linux Basics
- Conda & Mamba
- FastQC Installation

---

# 💡 Why is Quality Control Necessary?

Sequencing machines are not perfect.

Raw sequencing data may contain:

- Low-quality bases
- Adapter contamination
- PCR duplicates
- GC bias
- Overrepresented sequences
- Poor-quality reads

If these problems are ignored,

the downstream analysis may produce unreliable results.

---

# 📌 Where Does FastQC Fit?

Typical DNA-Seq Pipeline

```
Sequencer

↓

FASTQ

↓

FastQC

↓

Trimming (Fastp/Trimmomatic)

↓

Alignment (BWA)

↓

BAM

↓

Variant Calling

↓

VCF
```

FastQC is always performed **before alignment**.

---

# 📌 What is FastQC?

FastQC is a quality assessment tool for FASTQ sequencing files.

It produces an HTML report summarizing sequencing quality.

FastQC **does not modify** your FASTQ file.

It only analyzes the data.

---

# 📌 Input

Supported input files:

```text
sample.fastq

sample.fastq.gz
```

---

# 📌 Output

FastQC generates two files.

Example:

```text
sample_fastqc.html

sample_fastqc.zip
```

---

# 📌 Install FastQC

```bash
mamba install fastqc -c bioconda
```

---

Verify installation.

```bash
fastqc --version
```

Example

```text
FastQC v0.12.1
```

---

# 📌 Basic Command

```bash
fastqc sample.fastq.gz
```

---

# Save Results to a Folder

```bash
mkdir -p qc

fastqc sample.fastq.gz -o qc/
```

---

# Run Multiple Samples

```bash
fastqc *.fastq.gz -o qc/
```

---

# Use Multiple Threads

```bash
fastqc *.fastq.gz -t 8 -o qc/
```

Explanation

```
-t

↓

Threads
```

---

# 📂 Example Project

```text
RNASeq_Project/

raw_data/

sample1_R1.fastq.gz

sample1_R2.fastq.gz

qc/
```

Run

```bash
fastqc raw_data/*.fastq.gz -o qc/
```

---

# 📌 FastQC Report

Open

```text
sample_fastqc.html
```

in your browser.

The report contains several quality modules.

---

# 📊 FastQC Modules

| Module | Purpose |
|----------|----------|
| Basic Statistics | File information |
| Per Base Sequence Quality | Base quality across reads |
| Per Sequence Quality Scores | Overall read quality |
| Per Base GC Content | GC distribution |
| Per Sequence GC Content | GC variation |
| Per Base N Content | Unknown bases |
| Sequence Length Distribution | Read lengths |
| Sequence Duplication Levels | Duplicate reads |
| Overrepresented Sequences | Adapter contamination |
| Adapter Content | Adapter detection |

---

# 📌 Understanding PASS, WARN and FAIL

Each module is marked as:

🟢 PASS

No significant problem detected.

🟡 WARN

Possible issue requiring attention.

🔴 FAIL

A significant quality issue was detected.

A FAIL does **not automatically mean the sequencing run is unusable**. Some failures (such as duplication in RNA-Seq) may be expected depending on the experiment.

---

# 📌 Important Module 1

## Basic Statistics

Shows:

- Filename
- File type
- Total sequences
- Read length
- GC percentage

---

# 📌 Important Module 2

## Per Base Sequence Quality

This is one of the most important graphs.

It shows quality scores across each base position.

Good sequencing:

```
Q40

████████████

Q30

████████████

Q20

████████

Q10
```

Poor sequencing:

```
Q40

██

Q30

████

Q20

████████

Q10

██████████
```

Generally:

- Green region = High quality
- Orange = Moderate quality
- Red = Poor quality

---

# 📌 Quality Scores (Phred Score)

| Score | Accuracy |
|--------|----------|
| Q10 | 90% |
| Q20 | 99% |
| Q30 | 99.9% |
| Q40 | 99.99% |

Most sequencing facilities aim for **Q30 or higher**.

---

# 📌 Adapter Content

Adapters are artificial sequences added during library preparation.

If adapters remain in the reads,

they should usually be removed before alignment.

Common trimming tools include:

- Fastp
- Trimmomatic
- Cutadapt

---

# 📌 Overrepresented Sequences

This module detects sequences that occur much more often than expected.

Possible reasons include:

- Adapter contamination
- PCR artifacts
- Ribosomal RNA contamination
- Biological enrichment

Interpret this module in the context of your experiment.

---

# 📌 Sequence Duplication Levels

High duplication may indicate:

- PCR duplication
- Low library complexity

However,

RNA-Seq datasets often show higher duplication because highly expressed genes generate many identical reads.

---

# 📌 GC Content

The GC distribution should generally resemble the expected distribution for the organism and experiment.

A large shift may indicate:

- Contamination
- Library preparation bias
- Mixed samples

---

# 📊 Important FastQC Options

| Option | Purpose |
|----------|----------|
| `-o` | Output directory |
| `-t` | Number of threads |
| `--nogroup` | Disable grouping of long reads |
| `--extract` | Extract ZIP report |

---

# 🧬 Real NGS Workflow

```text
FASTQ

↓

FastQC

↓

Review HTML Report

↓

Good Quality?

↓

YES

↓

Alignment

↓

NO

↓

Trim Reads

↓

Run FastQC Again
```

---

# 🤖 Bash Automation

```bash
#!/bin/bash

mkdir -p qc

for sample in raw_data/*.fastq.gz
do
    echo "Running FastQC on $sample"
    fastqc "$sample" -o qc -t 8
done

echo "FastQC analysis completed."
```

Make executable.

```bash
chmod +x run_fastqc.sh
```

Run.

```bash
./run_fastqc.sh
```

---

# 🧪 Hands-on Practice

Create project.

```bash
mkdir FastQC_Practice

cd FastQC_Practice

mkdir raw_data qc
```

Place FASTQ files inside

```text
raw_data/
```

Run

```bash
fastqc raw_data/*.fastq.gz -o qc/
```

---

# 🚨 Common Errors

## Error

```text
fastqc: command not found
```

Reason

FastQC is not installed or the environment is not activated.

Solution

```bash
conda activate ngs

which fastqc
```

---

## Error

```text
Permission denied
```

Solution

```bash
chmod +x run_fastqc.sh
```

or check file permissions using

```bash
ls -l
```

---

## Error

```text
No such file or directory
```

Check the file path.

```bash
ls raw_data/
```

---

# 🧠 Interview Questions

### ❓ Why is FastQC the first step in an NGS pipeline?

Because it evaluates the quality of raw sequencing reads before downstream analysis.

---

### ❓ Does FastQC modify FASTQ files?

No.

It only analyzes the sequencing data and generates reports.

---

### ❓ What are the two main output files?

- HTML report
- ZIP archive

---

### ❓ What does a low Phred score indicate?

A higher probability of sequencing errors.

---

### ❓ If FastQC reports adapter contamination, what would you do next?

Trim adapters using tools such as Fastp, Trimmomatic, or Cutadapt, then rerun FastQC to confirm improvement.

---

# 📝 Lesson Summary

- FastQC is the standard quality control tool for FASTQ files.
- It is the first analytical step in most NGS workflows.
- It produces HTML and ZIP reports.
- Key modules include base quality, GC content, duplication levels, and adapter content.
- Review FastQC results before proceeding to alignment or variant calling.

---

# ⚡ Quick Revision

| Topic | Key Point |
|--------|-----------|
| Input | `.fastq`, `.fastq.gz` |
| Output | HTML + ZIP |
| First Step | Quality Control |
| Good Quality | Q30 or higher |
| Common Issues | Adapters, low quality, duplication, GC bias |
| Next Step | Trimming if necessary |

---

# 📚 References

- FastQC Documentation
- Babraham Bioinformatics
- Bioinformatics Data Skills (Book)

---

# ➡️ Next Lesson

**MultiQC – Combining FastQC Reports into a Single Interactive Report**
