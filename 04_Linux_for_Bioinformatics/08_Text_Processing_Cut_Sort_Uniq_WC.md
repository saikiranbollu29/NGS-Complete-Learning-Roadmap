# 📊 Text Processing (cut, sort, uniq, wc)

> [!NOTE]
> **Module 3 • Lesson 8**
>
> Learn how to extract columns, sort data, remove duplicate entries, and count records using Linux commands that are essential for bioinformatics.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Extract columns from text files.
- Sort genomic data.
- Remove duplicate entries.
- Count lines, words, and characters.
- Combine multiple commands using pipelines.
- Analyze bioinformatics files efficiently.

---

# 📚 Prerequisites

- Linux Navigation
- grep
- Basic Linux Commands

---

# 💡 Real-Life Analogy

Imagine you have an Excel spreadsheet containing thousands of patient records.

Sometimes you only need:

- Patient IDs
- Gene names
- Chromosome numbers

Instead of opening Excel,

Linux extracts exactly what you need.

---

# 🧬 Bioinformatics Scenario

Suppose you have a variant file:

```text
variants.tsv
```

Contents

```text
Chr    Position    Gene

chr1   12345       TP53

chr17  43044295    BRCA1

chr17  43125482    BRCA1

chr7   55181378    EGFR
```

We will use this file throughout the lesson.

---

# 📌 Command 1 — cut

## Purpose

Extracts selected columns from a file.

---

## Syntax

```bash
cut -f column file
```

---

## Extract Gene Column

```bash
cut -f3 variants.tsv
```

Output

```text
Gene

TP53

BRCA1

BRCA1

EGFR
```

---

## Extract Chromosome and Gene

```bash
cut -f1,3 variants.tsv
```

Output

```text
Chr    Gene

chr1   TP53

chr17  BRCA1

chr17  BRCA1

chr7   EGFR
```

---

## Explanation

```
-f

↓

Field
```

Fields are usually separated by:

- Tab
- Comma
- Colon

---

## Comma-Separated File Example

```bash
cut -d "," -f2 sample.csv
```

`-d`

↓

Delimiter

---

# 🧬 Bioinformatics Example

Extract chromosome names from a VCF file.

```bash
cut -f1 variants.vcf
```

---

# 📌 Command 2 — sort

## Purpose

Sorts text alphabetically or numerically.

---

## Syntax

```bash
sort filename
```

---

## Example

```bash
sort genes.txt
```

Output

```text
BRCA1

BRCA2

EGFR

MYC

TP53
```

---

## Numeric Sorting

```bash
sort -n positions.txt
```

---

## Reverse Sorting

```bash
sort -r genes.txt
```

---

# 🧬 Bioinformatics Example

Sort chromosome list.

```bash
cut -f1 variants.tsv | sort
```

Output

```text
chr1

chr17

chr17

chr7
```

---

# 📌 Command 3 — uniq

## Purpose

Removes duplicate consecutive lines.

---

## Syntax

```bash
uniq filename
```

---

## Example

```text
BRCA1

BRCA1

EGFR

TP53
```

Run

```bash
uniq genes.txt
```

Output

```text
BRCA1

EGFR

TP53
```

---

## Count Duplicates

```bash
uniq -c genes.txt
```

Output

```text
2 BRCA1

1 EGFR

1 TP53
```

---

## Important Note

`uniq` only removes **adjacent duplicates**.

Always sort first.

Correct:

```bash
sort genes.txt | uniq
```

Not:

```bash
uniq genes.txt
```

---

# 📌 Command 4 — wc

## Purpose

Counts:

- Lines
- Words
- Characters
- Bytes

---

## Syntax

```bash
wc filename
```

---

## Count Lines

```bash
wc -l genes.txt
```

Output

```text
5
```

---

## Count Words

```bash
wc -w genes.txt
```

---

## Count Characters

```bash
wc -m genes.txt
```

---

## Count Bytes

```bash
wc -c genes.txt
```

---

# 📊 Command Summary

| Command | Purpose |
|----------|----------|
| cut | Extract columns |
| sort | Sort data |
| uniq | Remove duplicates |
| uniq -c | Count duplicates |
| wc -l | Count lines |
| wc -w | Count words |
| wc -m | Count characters |

---

# 🧬 Linux Pipelines

A pipeline connects commands together.

```
Command A

↓

|

↓

Command B
```

Output from one command becomes input for the next.

---

# Example 1

Count chromosomes.

```bash
cut -f1 variants.tsv | sort | uniq
```

Output

```text
chr1

chr17

chr7
```

---

# Example 2

Count unique chromosomes.

```bash
cut -f1 variants.tsv | sort | uniq | wc -l
```

Output

```text
3
```

---

# Example 3

Count variants per chromosome.

```bash
cut -f1 variants.tsv | sort | uniq -c
```

Output

```text
1 chr1

2 chr17

1 chr7
```

---

# 🧬 NGS Workflow Connection

Count FASTA chromosomes.

```bash
grep "^>" genome.fa | wc -l
```

Count variants.

```bash
grep -v "^#" sample.vcf | wc -l
```

Extract chromosome names.

```bash
cut -f1 sample.vcf | sort | uniq
```

Count unique genes.

```bash
cut -f3 variants.tsv | sort | uniq | wc -l
```

---

# 🧬 Real NGS Dataset Challenge

### Challenge 1

Count FASTA sequences.

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

List chromosomes.

```bash
cut -f1 sample.vcf | sort | uniq
```

---

### Challenge 4

Count chromosome frequency.

```bash
cut -f1 sample.vcf | sort | uniq -c
```

---

### Challenge 5

Count unique genes.

```bash
cut -f3 variants.tsv | sort | uniq | wc -l
```

---

# 💪 Practice Exercises

## Exercise 1

Extract the first column.

```bash
cut -f1 variants.tsv
```

---

## Exercise 2

Sort gene names.

```bash
cut -f3 variants.tsv | sort
```

---

## Exercise 3

Remove duplicates.

```bash
cut -f3 variants.tsv | sort | uniq
```

---

## Exercise 4

Count unique genes.

```bash
cut -f3 variants.tsv | sort | uniq | wc -l
```

---

## Exercise 5

Count duplicate genes.

```bash
cut -f3 variants.tsv | sort | uniq -c
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Using `uniq` without sorting first.
> - Using the wrong delimiter with `cut`.
> - Forgetting that VCF headers start with `#`.
> - Confusing `wc -l` (lines) with `wc -w` (words).

---

# 🧠 Interview Corner

### ❓ What does `cut` do?

Extracts specific columns (fields) from a text file.

---

### ❓ Why should `sort` usually come before `uniq`?

Because `uniq` only removes duplicate lines that are adjacent.

---

### ❓ How do you count the number of variants in a VCF file?

```bash
grep -v "^#" sample.vcf | wc -l
```

---

### ❓ How do you count unique chromosomes?

```bash
cut -f1 sample.vcf | sort | uniq | wc -l
```

---

### ❓ What is a Linux pipeline?

A pipeline (`|`) passes the output of one command as the input to another command.

---

# 📝 Lesson Summary

- `cut` extracts columns.
- `sort` orders data.
- `uniq` removes adjacent duplicates.
- `wc` counts lines, words, and characters.
- Pipelines allow multiple commands to work together.
- These commands are fundamental for processing genomics datasets.

---

# ⚡ Quick Revision

| Command | Purpose |
|---------|---------|
| `cut -f1` | Extract first column |
| `cut -d "," -f2` | Extract second CSV column |
| `sort` | Sort data |
| `sort -n` | Numeric sort |
| `uniq` | Remove duplicates |
| `uniq -c` | Count duplicates |
| `wc -l` | Count lines |
| `wc -w` | Count words |
| `wc -m` | Count characters |
| `|` | Connect commands |

---

# 📚 References

- GNU Core Utilities Manual
- Ubuntu Documentation
- Bioinformatics Data Skills (Book)

---

# ➡️ Next Lesson

**Advanced Text Processing with `awk`**
