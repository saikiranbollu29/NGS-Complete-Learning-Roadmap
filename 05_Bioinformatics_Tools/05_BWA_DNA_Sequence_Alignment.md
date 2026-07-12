# 🧬 BWA – Burrows-Wheeler Aligner (DNA Sequence Alignment)

> [!NOTE]
> **Module 4 • Lesson 5**
>
> Learn how DNA sequencing reads are aligned to a reference genome using BWA. This lesson covers the theory, algorithm, hands-on practice, automation, troubleshooting, and interview questions.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand sequence alignment.
- Learn how BWA works internally.
- Build a reference genome index.
- Align FASTQ reads to a reference genome.
- Understand the SAM output.
- Interpret mapping quality (MAPQ).
- Automate alignment using Bash.

---

# 📚 Prerequisites

- Linux Basics
- FastQC
- Fastp
- Conda & Mamba

---

# 💡 Why is Alignment Necessary?

Sequencing machines produce millions of short DNA reads.

Example

```
ATCGTAGCTAGCT

CGATCGATCGATC

GCTAGCTAGCTAA
```

These reads have no chromosome information.

Alignment determines:

- Which chromosome they came from.
- Their genomic position.
- Whether mismatches, insertions, or deletions exist.

---

# 📌 Where Does BWA Fit?

```text
FASTQ

↓

FastQC

↓

Fastp

↓

BWA Index

↓

BWA-MEM

↓

SAM

↓

Samtools

↓

BAM

↓

Variant Calling
```

---

# 📌 What is BWA?

BWA (Burrows–Wheeler Aligner) is a DNA sequence aligner.

It maps sequencing reads to a reference genome using the Burrows–Wheeler Transform (BWT) and the FM-index.

It is widely used for:

- Whole Genome Sequencing (WGS)
- Whole Exome Sequencing (WES)
- Targeted sequencing

---

# 📌 What is Sequence Alignment?

Sequence alignment is the process of finding the most likely location of a sequencing read within a reference genome.

Example

Reference

```text
ATCGTAGCTAGCTAGCTA
```

Read

```text
TAGCTAG
```

Alignment

```text
ATCGTAGCTAGCTAGCTA

     TAGCTAG
```

---

# 📌 Why Build an Index?

Searching every read against a 3.2-billion-base human genome directly would be extremely slow.

BWA first builds an index.

Think of it like creating an index for a textbook.

Instead of reading every page,

you immediately jump to the relevant section.

---

# 📌 Burrows–Wheeler Transform (BWT)

The Burrows–Wheeler Transform rearranges the reference genome into a format that enables very fast substring searching.

Advantages:

- Fast searching
- Low memory usage
- Efficient storage

You do not need to perform BWT manually; BWA builds it automatically during indexing.

---

# 📌 FM-index

The FM-index is a compressed data structure built from the BWT.

It allows BWA to:

- Search efficiently
- Use less memory
- Scale to very large genomes

---

# 📌 BWA Algorithms

| Algorithm | Best Use |
|------------|----------|
| BWA-backtrack | Short reads (legacy) |
| BWA-SW | Long reads (legacy) |
| BWA-MEM | Modern Illumina DNA sequencing |

Today, BWA-MEM is the recommended algorithm for most WGS and WES analyses.

---

# 📌 Installation

```bash
mamba install bwa -c bioconda
```

Verify

```bash
bwa
```

---

# 📌 Input Files

```text
Reference Genome

genome.fa
```

```text
FASTQ

sample_R1.fastq.gz

sample_R2.fastq.gz
```

---

# 📌 Step 1 – Build Reference Index

```bash
bwa index genome.fa
```

Generated files

```text
genome.fa.amb

genome.fa.ann

genome.fa.bwt

genome.fa.pac

genome.fa.sa
```

These files are required for alignment.

---

# 📌 Step 2 – Align Reads

```bash
bwa mem \
genome.fa \
sample_R1.fastq.gz \
sample_R2.fastq.gz \
> sample.sam
```

---

# 📌 Multi-threading

```bash
bwa mem \
-t 8 \
genome.fa \
sample_R1.fastq.gz \
sample_R2.fastq.gz \
> sample.sam
```

`-t`

↓

Number of CPU threads.

---

# 📌 Output

```text
sample.sam
```

SAM = Sequence Alignment/Map format.

---

# 📌 What is a SAM File?

A SAM file contains alignment information for each sequencing read.

Example

```text
Read ID

Chromosome

Position

Mapping Quality

CIGAR String

Sequence
```

---

# 📌 Understanding MAPQ

MAPQ (Mapping Quality) represents the confidence that a read has been aligned correctly.

Higher MAPQ generally indicates greater confidence.

---

# 📌 Understanding the CIGAR String

The CIGAR string describes how a read aligns to the reference.

Common operations:

| Symbol | Meaning |
|---------|---------|
| M | Match or mismatch |
| I | Insertion |
| D | Deletion |
| S | Soft clipping |
| H | Hard clipping |

Example

```text
100M
```

A read aligned across 100 bases.

Example

```text
90M10S
```

90 aligned bases followed by 10 soft-clipped bases.

---

# 📌 Important BWA Options

| Option | Purpose |
|----------|----------|
| `mem` | Alignment algorithm |
| `index` | Build reference index |
| `-t` | Number of threads |
| `-R` | Read group information |
| `-M` | Mark shorter split hits (compatibility with some downstream tools) |

---

# 🧬 Example Project

```text
WGS_Project/

reference/

genome.fa

raw_data/

sample_R1.fastq.gz

sample_R2.fastq.gz

alignment/
```

---

Build index

```bash
cd reference

bwa index genome.fa
```

Run alignment

```bash
bwa mem \
-t 8 \
reference/genome.fa \
raw_data/sample_R1.fastq.gz \
raw_data/sample_R2.fastq.gz \
> alignment/sample.sam
```

---

# 🧬 Real NGS Workflow

```text
Reference Genome

↓

BWA Index

↓

FASTQ

↓

BWA-MEM

↓

SAM

↓

Samtools View

↓

BAM

↓

Sorting

↓

Variant Calling
```

---

# 🤖 Bash Automation

```bash
#!/bin/bash

mkdir -p alignment

REFERENCE="reference/genome.fa"

for r1 in raw_data/*_R1.fastq.gz
do
    r2=${r1/_R1/_R2}
    sample=$(basename "$r1" _R1.fastq.gz)

    bwa mem \
    -t 8 \
    "$REFERENCE" \
    "$r1" \
    "$r2" \
    > "alignment/${sample}.sam"

done

echo "Alignment completed."
```

---

# 🧪 Hands-on Practice

Project structure

```text
WGS_Practice/

reference/

genome.fa

raw_data/

sample_R1.fastq.gz

sample_R2.fastq.gz
```

Commands

```bash
bwa index reference/genome.fa
```

```bash
bwa mem \
reference/genome.fa \
raw_data/sample_R1.fastq.gz \
raw_data/sample_R2.fastq.gz \
> sample.sam
```

---

# 🚨 Common Errors

## Error

```text
[bwa_index] fail to locate the index files
```

Solution

Run

```bash
bwa index genome.fa
```

before alignment.

---

## Error

```text
command not found
```

Solution

```bash
conda activate ngs

which bwa
```

---

## Error

```text
No such file or directory
```

Verify file paths.

```bash
ls reference/

ls raw_data/
```

---

# 🧠 Interview Questions

### ❓ What is BWA?

A DNA sequence alignment tool that maps sequencing reads to a reference genome using the Burrows–Wheeler Transform and FM-index.

---

### ❓ Why do we build a reference index?

To allow fast and memory-efficient searching during alignment.

---

### ❓ What is BWA-MEM?

The recommended BWA algorithm for aligning modern Illumina DNA sequencing reads in WGS and WES projects.

---

### ❓ What is the output of BWA?

A SAM file containing read alignments.

---

### ❓ What does MAPQ represent?

The confidence that a read has been mapped to the correct genomic location.

---

### ❓ Can BWA be used for RNA-Seq?

Generally no.

RNA-Seq reads span exon–exon junctions, so splice-aware aligners such as HISAT2 or STAR are preferred.

---

# 📝 Lesson Summary

- BWA aligns DNA sequencing reads to a reference genome.
- Build the reference index before alignment.
- BWA-MEM is the standard algorithm for most Illumina DNA sequencing.
- Output is a SAM file containing alignment information.
- Mapping quality and the CIGAR string are key parts of the alignment.

---

# ⚡ Quick Revision

| Topic | Key Point |
|--------|-----------|
| Input | Reference FASTA + FASTQ |
| Output | SAM |
| First Step | `bwa index` |
| Main Algorithm | BWA-MEM |
| Used For | WGS, WES, Targeted Sequencing |
| Next Step | Samtools (SAM → BAM) |

---

# 📚 References

- Li H. & Durbin R. (2009). Fast and accurate short read alignment with Burrows–Wheeler Transform.
- BWA Documentation
- SAM/BAM Format Specification
- Bioinformatics Data Skills (Book)

---

# ➡️ Next Lesson

**Samtools – Working with SAM, BAM & CRAM Files (View, Convert, Sort, Index, Statistics)**
