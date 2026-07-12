# 🔗 Pipes, Redirection & Command Chaining

> [!NOTE]
> **Module 3 • Lesson 11**
>
> Learn how Linux commands work together using pipes and redirection. This is one of the most important skills for building real bioinformatics workflows.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand pipes.
- Redirect output into files.
- Append results to files.
- Read input from files.
- Save and display output simultaneously.
- Build complete bioinformatics command pipelines.

---

# 📚 Prerequisites

- grep
- cut
- awk
- sed

---

# 💡 Real-Life Analogy

Imagine a laboratory.

One scientist extracts DNA.

↓

Another scientist performs PCR.

↓

Another scientist sequences DNA.

↓

Another scientist analyzes variants.

Each scientist receives the previous person's work.

Linux pipelines work exactly the same way.

```
Command A

↓

Command B

↓

Command C

↓

Final Result
```

---

# 📌 What is a Pipe?

A **pipe (`|`)** sends the output of one command directly to another command.

Instead of saving intermediate files,

commands communicate directly.

---

# Basic Syntax

```bash
Command1 | Command2
```

---

# Example

```bash
ls | wc -l
```

Explanation

```
ls

↓

Lists files

↓

wc -l

↓

Counts files
```

---

# 📌 What is Redirection?

Instead of displaying output on the screen,

Linux can save it into a file.

---

# Output Redirection

```bash
>
```

Example

```bash
ls > files.txt
```

Now

```text
files.txt
```

contains

```
alignment

qc

results

scripts
```

---

# Append Output

```
>>
```

Instead of replacing the file,

append new information.

Example

```bash
date >> logfile.txt
```

---

# Difference

```bash
>
```

Overwrite

↓

Old data removed

---

```bash
>>
```

Append

↓

Old data preserved

---

# Input Redirection

```
<
```

Example

```bash
wc -l < genes.txt
```

Counts lines without specifying the filename as an argument.

---

# 📌 tee

Sometimes you want to

- see output
- save output

at the same time.

Use

```bash
tee
```

Example

```bash
ls | tee files.txt
```

Output appears

- on screen
- inside files.txt

---

# 🧬 Bioinformatics Example

Count chromosomes.

```bash
grep "^>" genome.fa | wc -l
```

Explanation

```
grep

↓

Find FASTA headers

↓

wc -l

↓

Count chromosomes
```

---

# Another Example

Extract chromosome names.

```bash
grep "^>" genome.fa | cut -d " " -f1
```

---

# Example

Count variants.

```bash
grep -v "^#" sample.vcf | wc -l
```

---

# Example

Count chromosome frequency.

```bash
grep -v "^#" sample.vcf \
| cut -f1 \
| sort \
| uniq -c
```

Output

```text
250 chr1

180 chr2

96 chr17
```

---

# Save Results

```bash
grep -v "^#" sample.vcf \
| cut -f1 \
| sort \
| uniq -c \
> chromosome_counts.txt
```

---

# Use tee

```bash
grep -v "^#" sample.vcf \
| cut -f1 \
| sort \
| uniq -c \
| tee chromosome_counts.txt
```

---

# Extract BRCA1 Coordinates

```bash
grep "BRCA1" annotation.gtf \
| awk '{print $1,$4,$5}'
```

---

# Count Unique Genes

```bash
cut -f3 variants.tsv \
| sort \
| uniq \
| wc -l
```

---

# Most Common Gene

```bash
cut -f3 variants.tsv \
| sort \
| uniq -c \
| sort -nr
```

Example Output

```text
52 TP53

40 BRCA1

21 EGFR
```

---

# Find Large BAM Files

```bash
find . -name "*.bam" \
| tee bam_files.txt
```

---

# Search Errors

```bash
grep "ERROR" *.log \
| tee errors.txt
```

---

# 🧬 Complete NGS Workflow Example

Suppose

```
sample.vcf
```

Goal:

Count variants on each chromosome.

Workflow

```bash
grep -v "^#" sample.vcf \
| awk '{print $1}' \
| sort \
| uniq -c \
| sort -nr \
> chromosome_summary.txt
```

Pipeline

```
VCF

↓

Remove Headers

↓

Extract Chromosome

↓

Sort

↓

Count

↓

Sort Counts

↓

Save Results
```

---

# 🧬 RNA-Seq Example

Count mapped reads.

```bash
awk '$3!="*"' sample.sam \
| wc -l
```

---

# FASTA Example

Count sequences.

```bash
grep "^>" genome.fa \
| wc -l
```

---

# FASTQ Example

Count reads.

```bash
grep "^@" sample.fastq \
| wc -l
```

---

# GTF Example

Extract genes.

```bash
awk '$3=="gene"' annotation.gtf \
| wc -l
```

---

# 📊 Symbols Summary

| Symbol | Meaning |
|----------|----------|
| `|` | Pipe |
| `>` | Overwrite output |
| `>>` | Append output |
| `<` | Input redirection |
| `tee` | Display and save output |

---

# 🧬 NGS Workflow Connection

Real bioinformatics pipelines rarely use one command.

Instead

```bash
grep

↓

awk

↓

sort

↓

uniq

↓

wc
```

All connected together.

---

# 🧬 Real NGS Dataset Challenge

### Challenge 1

Count chromosomes.

```bash
grep "^>" genome.fa | wc -l
```

---

### Challenge 2

Count variants.

```bash
grep -v "^#" sample.vcf | wc -l
```

---

### Challenge 3

Find chromosome frequency.

```bash
grep -v "^#" sample.vcf \
| cut -f1 \
| sort \
| uniq -c
```

---

### Challenge 4

Save results.

```bash
grep -v "^#" sample.vcf \
| cut -f1 \
| sort \
| uniq -c \
> summary.txt
```

---

### Challenge 5

Display and save.

```bash
grep "ERROR" *.log \
| tee errors.txt
```

---

# 💪 Practice Exercises

## Exercise 1

Save directory listing.

```bash
ls > files.txt
```

---

## Exercise 2

Append current date.

```bash
date >> files.txt
```

---

## Exercise 3

Count files.

```bash
ls | wc -l
```

---

## Exercise 4

Count unique genes.

```bash
cut -f3 variants.tsv \
| sort \
| uniq \
| wc -l
```

---

## Exercise 5

Count chromosome frequency.

```bash
cut -f1 variants.tsv \
| sort \
| uniq -c
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Accidentally overwriting important files with `>`.
> - Forgetting that `>` replaces existing content.
> - Using `uniq` before `sort`.
> - Creating very long pipelines without testing each command individually.

---

# 🧠 Interview Corner

### ❓ What does the pipe (`|`) operator do?

It sends the output of one command as the input to another command.

---

### ❓ Difference between `>` and `>>`?

- `>` overwrites a file.
- `>>` appends to a file.

---

### ❓ What is `tee` used for?

It displays output on the terminal while simultaneously saving it to a file.

---

### ❓ Why are pipelines important in bioinformatics?

They allow multiple commands to process large genomic datasets efficiently without creating unnecessary intermediate files.

---

# 📝 Lesson Summary

- Pipes connect commands.
- `>` saves output by overwriting.
- `>>` appends output.
- `<` redirects input.
- `tee` displays and saves output.
- Command pipelines are fundamental to Linux-based bioinformatics workflows.

---

# ⚡ Quick Revision

| Command | Purpose |
|---------|---------|
| `|` | Connect commands |
| `>` | Save output |
| `>>` | Append output |
| `<` | Input redirection |
| `tee` | Display and save |
| `grep "^>" genome.fa \| wc -l` | Count FASTA sequences |
| `grep -v "^#" sample.vcf \| wc -l` | Count variants |

---

# 📚 References

- GNU Core Utilities Manual
- GNU Bash Manual
- Ubuntu Documentation
- Bioinformatics Data Skills (Book)

---

# ➡️ Next Lesson

**File Permissions & Ownership (`chmod`, `chown`, `umask`)**
