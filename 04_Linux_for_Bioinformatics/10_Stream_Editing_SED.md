# ✏️ Stream Editing with sed

> [!NOTE]
> **Module 3 • Lesson 10**
>
> Learn how to edit text automatically using `sed` (Stream Editor). It is one of the most useful Linux tools for cleaning and modifying bioinformatics datasets.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand what `sed` is.
- Replace text automatically.
- Delete lines.
- Insert new lines.
- Modify genomic files.
- Automate repetitive editing tasks.

---

# 📚 Prerequisites

- grep
- cut
- awk

---

# 💡 Real-Life Analogy

Imagine you have **50,000 patient reports**.

Every report contains

```
Tumor
```

but now the hospital wants it changed to

```
Tumour
```

Would you edit every file manually?

No.

`sed` performs this replacement automatically.

---

# 📌 What is sed?

`sed` stands for **Stream Editor**.

It reads text line by line and performs editing operations such as:

- Replace text
- Delete lines
- Insert lines
- Modify patterns

Unlike a text editor, `sed` works directly from the command line and is ideal for automation.

---

# 🧬 Bioinformatics Scenario

Suppose

```text
samples.txt
```

contains

```text
Sample1 Control

Sample2 Tumor

Sample3 Tumor

Sample4 Control
```

---

# 📌 Basic Syntax

```bash
sed 's/old/new/' filename
```

---

# Replace First Match

```bash
sed 's/Tumor/Tumour/' samples.txt
```

Output

```text
Sample1 Control

Sample2 Tumour

Sample3 Tumour

Sample4 Control
```

Only the first occurrence in each line is replaced.

---

# Replace All Matches

```bash
sed 's/Tumor/Tumour/g' samples.txt
```

`g`

↓

Global replacement

---

# Ignore Case

```bash
sed 's/tumor/Tumour/Ig' samples.txt
```

`I`

↓

Ignore case

---

# Save Changes to File

```bash
sed -i 's/Tumor/Tumour/g' samples.txt
```

> [!WARNING]
>
> `-i` edits the original file permanently.
> Create a backup if needed.

---

# Create Backup Before Editing

```bash
sed -i.bak 's/Tumor/Tumour/g' samples.txt
```

Creates

```text
samples.txt

samples.txt.bak
```

---

# Delete a Line

Delete line 3

```bash
sed '3d' samples.txt
```

---

# Delete Blank Lines

```bash
sed '/^$/d' samples.txt
```

Useful when cleaning metadata files.

---

# Delete Comment Lines

```bash
sed '/^#/d' sample.vcf
```

---

# Print Specific Line

```bash
sed -n '5p' sample.vcf
```

---

# Print Lines 10–20

```bash
sed -n '10,20p' sample.vcf
```

---

# Insert a Line

Insert before line 1

```bash
sed '1i\
SampleID Condition
' samples.txt
```

---

# Append a Line

```bash
sed '$a\
End_of_File
' samples.txt
```

---

# Replace Chromosome Names

Suppose

```text
variants.tsv
```

contains

```text
1

2

3

X
```

Convert

```bash
sed 's/^/chr/' variants.tsv
```

Output

```text
chr1

chr2

chr3

chrX
```

---

# Remove "chr"

```bash
sed 's/^chr//' variants.tsv
```

---

# 🧬 sed with FASTA

Rename chromosome headers.

```bash
sed 's/>1/>chr1/' genome.fa
```

---

# 🧬 sed with FASTQ

Rename sample IDs.

```bash
sed 's/SRR000001/Sample01/' sample.fastq
```

---

# 🧬 sed with VCF

Remove comment lines.

```bash
sed '/^#/d' sample.vcf
```

---

# 🧬 sed with GTF

Replace gene name.

```bash
sed 's/BRCA1/BRCA1_v2/' annotation.gtf
```

---

# 📊 sed vs grep vs awk

| Tool | Purpose |
|------|----------|
| grep | Search text |
| sed | Edit text |
| awk | Analyze columns |

---

# 🧬 Linux Pipelines

Replace chromosome names then count variants.

```bash
sed 's/^1/chr1/' variants.tsv | wc -l
```

---

Replace gene names then search.

```bash
sed 's/BRCA1/BRCA1_NEW/' annotation.gtf | grep BRCA1_NEW
```

---

# 🧬 NGS Workflow Connection

Rename chromosome names.

```bash
sed 's/^1/chr1/' variants.tsv
```

Remove VCF headers.

```bash
sed '/^#/d' sample.vcf
```

Replace sample IDs.

```bash
sed 's/SRR123456/Patient001/' metadata.tsv
```

Clean blank lines.

```bash
sed '/^$/d' metadata.tsv
```

---

# 🧬 Real NGS Dataset Challenge

## Challenge 1

Remove VCF headers.

```bash
sed '/^#/d' sample.vcf
```

---

## Challenge 2

Rename chromosome numbers.

```bash
sed 's/^1/chr1/' variants.tsv
```

---

## Challenge 3

Replace sample names.

```bash
sed 's/Sample1/Patient001/' samples.txt
```

---

## Challenge 4

Delete blank lines.

```bash
sed '/^$/d' metadata.tsv
```

---

## Challenge 5

Print only lines 5–10.

```bash
sed -n '5,10p' annotation.gtf
```

---

# 💪 Practice Exercises

## Exercise 1

Replace

```
Control
```

with

```
Healthy
```

```bash
sed 's/Control/Healthy/g' samples.txt
```

---

## Exercise 2

Delete line 2.

```bash
sed '2d' samples.txt
```

---

## Exercise 3

Print line 3.

```bash
sed -n '3p' samples.txt
```

---

## Exercise 4

Remove blank lines.

```bash
sed '/^$/d' samples.txt
```

---

## Exercise 5

Create a backup and edit the file.

```bash
sed -i.bak 's/Tumor/Tumour/g' samples.txt
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Using `-i` without a backup.
> - Forgetting the `g` flag for global replacement.
> - Confusing searching (`grep`) with editing (`sed`).
> - Editing original sequencing files instead of working on copies.

---

# 🧠 Interview Corner

### ❓ What is sed?

A stream editor used to modify text automatically from the command line.

---

### ❓ What does `s` mean in sed?

It stands for **substitute**, which replaces matching text.

---

### ❓ What does the `g` flag do?

It replaces **all** matching occurrences on a line instead of only the first.

---

### ❓ How do you edit a file directly?

```bash
sed -i 's/old/new/g' filename
```

---

### ❓ When is sed useful in bioinformatics?

It is used to clean metadata, rename chromosome identifiers, standardize sample names, remove comments, and automate repetitive text edits.

---

# 📝 Lesson Summary

- `sed` edits text streams.
- Replace, delete, insert, and modify text automatically.
- Supports in-place editing with `-i`.
- Commonly used for cleaning genomic datasets.
- Complements `grep` (search) and `awk` (analysis).

---

# ⚡ Quick Revision

| Command | Purpose |
|---------|---------|
| `sed 's/A/B/'` | Replace first match |
| `sed 's/A/B/g'` | Replace all matches |
| `sed -i` | Edit file in place |
| `sed -i.bak` | Edit with backup |
| `sed '3d'` | Delete line 3 |
| `sed '/^#/d'` | Delete comment lines |
| `sed -n '5p'` | Print line 5 |
| `sed -n '5,10p'` | Print lines 5–10 |

---

# 📚 References

- GNU sed Manual
- Ubuntu Documentation
- Bioinformatics Data Skills (Book)

---

# ➡️ Next Lesson

**Pipes, Redirection & Command Chaining (`|`, `>`, `>>`, `<`)**
