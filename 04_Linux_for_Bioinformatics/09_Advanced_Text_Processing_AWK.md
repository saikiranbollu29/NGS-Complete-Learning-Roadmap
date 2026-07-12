# ⚡ Advanced Text Processing with awk

> [!NOTE]
> **Module 3 • Lesson 9**
>
> Learn how to use `awk` to extract, filter, calculate, and manipulate tabular data. `awk` is one of the most powerful tools in Linux and is widely used in bioinformatics.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand what `awk` is.
- Print specific columns.
- Filter rows using conditions.
- Perform calculations.
- Process genomic files such as VCF, BED, GTF, and SAM.
- Build Linux pipelines using `awk`.

---

# 📚 Prerequisites

- grep
- cut
- sort
- uniq
- wc

---

# 💡 Real-Life Analogy

Imagine an Excel spreadsheet containing:

- Chromosome
- Position
- Gene
- Variant

Instead of manually selecting columns,

`awk` allows Linux to do it automatically.

---

# 📌 What is awk?

`awk` is a pattern scanning and text processing language.

It processes data line by line and column by column.

Unlike `cut`, `awk` can also:

- Apply conditions
- Perform calculations
- Format output
- Create reports

---

# 🧬 Bioinformatics Scenario

Suppose

```text
variants.tsv
```

contains

```text
Chr    Position    Gene

chr1   12345       TP53

chr17  43044295    BRCA1

chr17  43125482    BRCA2

chr7   55181378    EGFR
```

---

# 📌 Basic Syntax

```bash
awk '{print}' filename
```

Prints every line.

---

# Print First Column

```bash
awk '{print $1}' variants.tsv
```

Output

```text
Chr

chr1

chr17

chr17

chr7
```

---

# Print Second Column

```bash
awk '{print $2}' variants.tsv
```

---

# Print Third Column

```bash
awk '{print $3}' variants.tsv
```

Output

```text
Gene

TP53

BRCA1

BRCA2

EGFR
```

---

# Print Multiple Columns

```bash
awk '{print $1,$3}' variants.tsv
```

Output

```text
Chr Gene

chr1 TP53

chr17 BRCA1

chr17 BRCA2

chr7 EGFR
```

---

# Understanding Columns

| Symbol | Meaning |
|---------|----------|
| `$1` | First column |
| `$2` | Second column |
| `$3` | Third column |
| `$NF` | Last column |
| `NR` | Current row number |
| `NF` | Number of columns |

---

# Print Last Column

```bash
awk '{print $NF}' variants.tsv
```

Useful because many genomic formats store annotations in the last column.

---

# Print Row Numbers

```bash
awk '{print NR,$0}' variants.tsv
```

Output

```text
1 Chr Position Gene

2 chr1 12345 TP53

3 chr17 43044295 BRCA1

4 chr17 43125482 BRCA2

5 chr7 55181378 EGFR
```

---

# Filter Rows

Show only chromosome 17.

```bash
awk '$1=="chr17"' variants.tsv
```

Output

```text
chr17 43044295 BRCA1

chr17 43125482 BRCA2
```

---

# Numeric Comparison

Display positions greater than 1,000,000.

```bash
awk '$2>1000000' variants.tsv
```

---

# Print Header + Filtered Rows

```bash
awk 'NR==1 || $1=="chr17"' variants.tsv
```

---

# Change Output Format

```bash
awk '{print $3 " is located on " $1}'
```

Output

```text
TP53 is located on chr1

BRCA1 is located on chr17

BRCA2 is located on chr17

EGFR is located on chr7
```

---

# Count Lines

```bash
awk 'END{print NR}' variants.tsv
```

---

# Sum Values

Suppose

```text
coverage.txt
```

contains

```text
20

25

30

35
```

Calculate total.

```bash
awk '{sum+=$1} END{print sum}' coverage.txt
```

Output

```text
110
```

---

# Calculate Average

```bash
awk '{sum+=$1} END{print sum/NR}' coverage.txt
```

Output

```text
27.5
```

---

# Specify Delimiter

CSV file.

```bash
awk -F "," '{print $2}' samples.csv
```

TSV file.

```bash
awk -F "\t" '{print $3}' variants.tsv
```

---

# 🧬 awk with FASTA

Print FASTA headers.

```bash
awk '/^>/' genome.fa
```

---

# 🧬 awk with FASTQ

Print read IDs.

```bash
awk 'NR%4==1' sample.fastq
```

Explanation

FASTQ format:

```
Line 1 → Read ID

Line 2 → Sequence

Line 3 → +

Line 4 → Quality
```

Every fourth line beginning at line 1 is a read identifier.

---

# 🧬 awk with VCF

Skip comments.

```bash
awk '!/^#/' sample.vcf
```

Print chromosome and position.

```bash
awk '!/^#/ {print $1,$2}' sample.vcf
```

---

# 🧬 awk with GTF

Extract gene names.

```bash
awk '$3=="gene"' annotation.gtf
```

---

# 🧬 awk with SAM

Print mapped reads only.

```bash
awk '$3!="*"' sample.sam
```

---

# 📊 awk vs cut

| cut | awk |
|------|------|
| Extract columns | Extract columns |
| No calculations | Supports calculations |
| No conditions | Supports conditions |
| Simple | Very powerful |

---

# 🧬 Linux Pipelines

Count chromosome frequency.

```bash
awk '{print $1}' variants.tsv | sort | uniq -c
```

---

# Count Unique Genes

```bash
awk '{print $3}' variants.tsv | sort | uniq | wc -l
```

---

# 🧬 NGS Workflow Connection

Extract chromosomes.

```bash
awk '!/^#/ {print $1}' sample.vcf
```

Extract chromosome + position.

```bash
awk '!/^#/ {print $1,$2}' sample.vcf
```

List mapped reads.

```bash
awk '$3!="*"' sample.sam
```

Extract FASTA headers.

```bash
awk '/^>/' genome.fa
```

---

# 🧬 Real NGS Dataset Challenge

### Challenge 1

Print chromosome names.

```bash
awk '!/^#/ {print $1}' sample.vcf
```

---

### Challenge 2

Print chromosome and position.

```bash
awk '!/^#/ {print $1,$2}' sample.vcf
```

---

### Challenge 3

Print gene column.

```bash
awk '{print $3}' variants.tsv
```

---

### Challenge 4

Show only chromosome 17 variants.

```bash
awk '$1=="chr17"' variants.tsv
```

---

### Challenge 5

Count total variants.

```bash
awk 'END{print NR-1}' variants.tsv
```

---

# 💪 Practice Exercises

## Exercise 1

Print the first column.

```bash
awk '{print $1}' variants.tsv
```

---

## Exercise 2

Print the second column.

```bash
awk '{print $2}' variants.tsv
```

---

## Exercise 3

Print the last column.

```bash
awk '{print $NF}' variants.tsv
```

---

## Exercise 4

Display only chromosome 17.

```bash
awk '$1=="chr17"' variants.tsv
```

---

## Exercise 5

Count the number of records.

```bash
awk 'END{print NR}' variants.tsv
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Forgetting that `$1`, `$2`, etc., refer to columns.
> - Not specifying the correct delimiter (`-F`) for CSV or TSV files.
> - Including VCF header lines when processing variants.
> - Confusing `NR` (record number) with `NF` (number of fields).

---

# 🧠 Interview Corner

### ❓ What is awk?

`awk` is a powerful Linux tool used for pattern scanning and processing structured text files.

---

### ❓ What does `$1` represent?

The first column.

---

### ❓ What does `NR` mean?

The current record (line) number.

---

### ❓ What does `NF` mean?

The number of fields (columns) in the current line.

---

### ❓ Why is awk widely used in bioinformatics?

Because most bioinformatics file formats (VCF, GTF, BED, SAM, TSV) are structured into columns, making `awk` ideal for filtering, extracting, and summarizing data.

---

# 📝 Lesson Summary

- `awk` is a powerful text-processing language.
- It works with rows and columns.
- It supports calculations, filtering, and formatting.
- It is extensively used with genomics file formats.
- Learning `awk` is an essential skill for every bioinformatician.

---

# ⚡ Quick Revision

| Command | Purpose |
|---------|---------|
| `awk '{print $1}'` | Print first column |
| `awk '{print $NF}'` | Print last column |
| `awk 'NR==1'` | Print first row |
| `awk 'END{print NR}'` | Count rows |
| `awk '$1=="chr17"'` | Filter chromosome 17 |
| `awk -F ","` | Use comma as delimiter |
| `awk '!/^#/'` | Skip comment lines |

---

# 📚 References

- GNU Awk User Guide
- Ubuntu Documentation
- Bioinformatics Data Skills (Book)

---

# ➡️ Next Lesson

**Stream Editing with `sed`**
