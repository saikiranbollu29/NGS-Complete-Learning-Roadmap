# 🔎 Text Processing with grep

> [!NOTE]
> **Module 3 • Lesson 7**
>
> Learn how to search for specific text patterns using the `grep` command. This is one of the most frequently used commands in bioinformatics for filtering and inspecting sequencing data.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Search text inside files.
- Search genes, chromosomes, and sequence identifiers.
- Use common grep options.
- Combine grep with other Linux commands.
- Apply grep in real NGS workflows.
- Answer interview questions confidently.

---

# 📚 Prerequisites

- Linux Navigation
- Viewing Files
- Searching Files

---

# 💡 Real-Life Analogy

Imagine a library with one million books.

Instead of reading every book,

you search for the word

```
Cancer
```

and instantly find every page containing it.

`grep` performs exactly this task for text files.

---

# 📌 What is grep?

`grep` searches for a specific word, phrase, or pattern inside one or more files.

It prints only the lines that match the search pattern.

---

# 🧬 Bioinformatics Scenario

Suppose you have:

```text
reference/

genome.fa

annotation.gtf

alignment/

sample.sam

variants/

sample.vcf

logs/

pipeline.log
```

Instead of reading thousands of lines,

you search only for the information you need.

---

# 📌 Basic Syntax

```bash
grep "pattern" filename
```

---

# Example

Suppose

```text
genes.txt
```

contains

```text
BRCA1

TP53

EGFR

MYC

BRCA2
```

Run

```bash
grep "BRCA1" genes.txt
```

Output

```text
BRCA1
```

---

# Example 2

```bash
grep "TP53" genes.txt
```

Output

```text
TP53
```

---

# 📌 Ignore Uppercase/Lowercase

```bash
grep -i "brca1" genes.txt
```

Output

```text
BRCA1
```

Useful when capitalization varies.

---

# 📌 Show Line Numbers

```bash
grep -n "BRCA1" genes.txt
```

Output

```text
1:BRCA1
```

---

# 📌 Count Matches

```bash
grep -c "BRCA" genes.txt
```

Output

```text
2
```

---

# 📌 Invert Match

Display lines **without** the pattern.

```bash
grep -v "BRCA1" genes.txt
```

Output

```text
TP53

EGFR

MYC

BRCA2
```

---

# 📌 Search Multiple Files

```bash
grep "TP53" *.txt
```

---

# 📌 Recursive Search

Search every file inside a directory.

```bash
grep -r "BRCA1" .
```

---

# 📌 Highlight Matches

```bash
grep --color=auto "BRCA1" genes.txt
```

The matching word is highlighted.

---

# 🧬 grep with FASTA Files

Suppose

```text
genome.fa
```

contains

```text
>chr1

ATCG...

>chr2

ATCG...

>chrX

ATCG...
```

Display only chromosome names.

```bash
grep "^>" genome.fa
```

Output

```text
>chr1

>chr2

>chrX
```

Explanation

```
^

↓

Beginning of line

>

↓

FASTA header
```

---

# 🧬 grep with FASTQ Files

Display read identifiers.

```bash
grep "^@" sample.fastq
```

Output

```text
@SRR123456.1

@SRR123456.2
```

---

# 🧬 grep with GTF Files

Find BRCA1 annotations.

```bash
grep "BRCA1" annotation.gtf
```

---

# 🧬 grep with SAM Files

Display alignments on chromosome 17.

```bash
grep "chr17" sample.sam
```

---

# 🧬 grep with VCF Files

Display chromosome 1 variants.

```bash
grep "^chr1" sample.vcf
```

---

# 🧬 grep Log Files

Find errors.

```bash
grep "ERROR" pipeline.log
```

Find warnings.

```bash
grep "WARNING" pipeline.log
```

---

# 📌 Common Options

| Option | Meaning |
|---------|----------|
| `-i` | Ignore case |
| `-n` | Show line numbers |
| `-c` | Count matches |
| `-v` | Show non-matching lines |
| `-r` | Search recursively |
| `--color` | Highlight matches |

---

# 🧬 NGS Workflow Connection

Check FASTA headers.

```bash
grep "^>" genome.fa
```

Check read IDs.

```bash
grep "^@" sample.fastq
```

Check chromosome 17 variants.

```bash
grep "^chr17" variants.vcf
```

Check if FastQC finished successfully.

```bash
grep "Analysis complete" fastqc.log
```

---

# 🧬 Real NGS Dataset Challenge

### Challenge 1

Count chromosomes.

```bash
grep "^>" genome.fa | wc -l
```

---

### Challenge 2

Find BRCA1.

```bash
grep "BRCA1" annotation.gtf
```

---

### Challenge 3

Find chromosome X variants.

```bash
grep "^chrX" sample.vcf
```

---

### Challenge 4

Search FastQC log.

```bash
grep "PASS" fastqc.log
```

---

### Challenge 5

Find every ERROR message.

```bash
grep "ERROR" *.log
```

---

# 💪 Practice Exercises

## Exercise 1

Create a file.

```bash
cat > genes.txt
```

Type

```text
BRCA1
TP53
EGFR
MYC
BRCA2
```

Press

```
CTRL + D
```

---

## Exercise 2

Search BRCA1.

```bash
grep "BRCA1" genes.txt
```

---

## Exercise 3

Ignore case.

```bash
grep -i "tp53" genes.txt
```

---

## Exercise 4

Count BRCA genes.

```bash
grep -c "BRCA" genes.txt
```

---

## Exercise 5

Show line numbers.

```bash
grep -n "EGFR" genes.txt
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Forgetting quotation marks around patterns containing special characters.
> - Using `grep "^@"` on compressed FASTQ (`.fastq.gz`) files directly. Use `zgrep` or decompress first.
> - Confusing `grep -v` (invert match) with deleting lines.
> - Searching binary files with `grep`.

---

# 🧠 Interview Corner

### ❓ What does grep do?

Searches for matching text patterns inside files.

---

### ❓ How do you search for BRCA1?

```bash
grep "BRCA1" annotation.gtf
```

---

### ❓ How do you count matching lines?

```bash
grep -c "BRCA" genes.txt
```

---

### ❓ How do you search recursively?

```bash
grep -r "TP53" .
```

---

### ❓ Why is grep important in bioinformatics?

It quickly filters large genomic files, allowing researchers to find genes, variants, sequence identifiers, or log messages without opening the entire file.

---

# 📝 Lesson Summary

- `grep` searches text inside files.
- Supports case-insensitive, recursive, and line-number searches.
- Frequently used with FASTA, FASTQ, GTF, SAM, VCF, and log files.
- One of the most commonly used Linux commands in bioinformatics.

---

# ⚡ Quick Revision

| Command | Purpose |
|---------|---------|
| `grep "BRCA1" file` | Search text |
| `grep -i` | Ignore case |
| `grep -n` | Show line numbers |
| `grep -c` | Count matches |
| `grep -v` | Show non-matching lines |
| `grep -r` | Recursive search |
| `grep "^>" genome.fa` | FASTA headers |
| `grep "^@" sample.fastq` | FASTQ read IDs |

---

# 📚 References

- GNU Grep Manual
- Ubuntu Documentation
- Bioinformatics Data Skills (Book)

---

# ➡️ Next Lesson

**Text Processing (`cut`, `sort`, `uniq`, `wc`)**
