# 📄 Viewing File Contents (cat, less, head, tail, more)

> [!NOTE]
> **Module 3 • Lesson 5**
>
> Learn how to inspect text files in Linux using commands commonly used in bioinformatics workflows.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Display the contents of text files.
- View large files efficiently.
- Display only the first or last lines.
- Monitor log files in real time.
- Inspect FASTQ, FASTA, GTF, BED, VCF, and SAM files safely.

---

# 📚 Prerequisites

- Linux Navigation
- Creating Files
- Basic Linux Commands

---

# 💡 Real-Life Analogy

Imagine receiving a 5,000-page laboratory notebook.

You rarely read every page.

Instead, you:

- Read the first page.
- Read the last page.
- Search for specific information.
- Flip through pages.

Linux provides commands for each of these tasks.

---

# 🧬 Bioinformatics Scenario

Suppose your project contains:

```text
RNASeq_Project/

raw_data/

sample_R1.fastq

sample_R2.fastq

reference/

genome.fa

annotation.gtf

results/

counts.txt

logs/

fastqc.log
```

Before analysis, you inspect these files.

---

# 📌 Command 1 — cat

## Purpose

Displays the entire contents of a file.

---

## Syntax

```bash
cat filename
```

---

## Example

```bash
cat metadata.csv
```

---

## Expected Output

```text
SampleID,Condition

S1,Control

S2,Treated
```

---

## Explanation

```
cat

↓

Concatenate

(Usually used to display files)
```

---

## Bioinformatics Example

View a FASTA file.

```bash
cat genome.fa
```

Output

```text
>chr1

ATCGATCGATCGATCG...
```

---

## View Multiple Files

```bash
cat sample1.txt sample2.txt
```

---

## Create a File Using cat

```bash
cat > notes.txt
```

Type:

```text
NGS Pipeline Notes
```

Press

```
CTRL + D
```

to save.

---

# 📌 Command 2 — less

## Purpose

View very large files page by page.

Unlike `cat`, it does not load the whole file onto the screen at once.

---

## Syntax

```bash
less filename
```

---

## Example

```bash
less genome.fa
```

---

## Navigation

| Key | Action |
|------|--------|
| Space | Next page |
| b | Previous page |
| ↑ ↓ | Move line by line |
| / | Search text |
| n | Next search result |
| q | Quit |

---

## Bioinformatics Example

```bash
less annotation.gtf
```

Search for:

```
BRCA1
```

Type

```
/BRCA1
```

---

# 📌 Command 3 — head

## Purpose

Displays the first lines of a file.

Default:

```
10 lines
```

---

## Syntax

```bash
head filename
```

---

## Example

```bash
head sample.fastq
```

---

## Expected Output

```text
@SEQ_ID

ATCGATCG

+

IIIIIIII
```

Perfect for checking FASTQ files.

---

## First 20 Lines

```bash
head -20 sample.fastq
```

---

# 📌 Command 4 — tail

## Purpose

Displays the last lines of a file.

---

## Syntax

```bash
tail filename
```

---

## Example

```bash
tail fastqc.log
```

---

## Expected Output

```text
Analysis Completed Successfully
```

---

## Last 20 Lines

```bash
tail -20 fastqc.log
```

---

## Real-Time Monitoring

```bash
tail -f fastqc.log
```

Useful while a program is running.

Exit with:

```
CTRL + C
```

---

# 📌 Command 5 — more

## Purpose

Displays a file one screen at a time.

Older than `less`.

---

## Syntax

```bash
more filename
```

---

## Example

```bash
more genome.fa
```

---

# 📊 Command Comparison

| Command | Best Used For |
|----------|---------------|
| cat | Small files |
| less | Large files |
| head | Beginning of file |
| tail | End of file |
| tail -f | Live log monitoring |
| more | Page-by-page viewing |

---

# 🧬 NGS Workflow Connection

Suppose you've downloaded sequencing data.

Before analysis:

Check FASTQ

```bash
head sample_R1.fastq
```

Check reference genome

```bash
head genome.fa
```

Check annotation

```bash
less annotation.gtf
```

Check FastQC completion

```bash
tail fastqc.log
```

This simple inspection helps detect problems before starting expensive analyses.

---

# 🧬 Common Bioinformatics File Types

| File | Command |
|------|---------|
| FASTQ | head |
| FASTA | less |
| GTF | less |
| BED | head |
| VCF | head |
| SAM | less |
| BAM | Use samtools view (covered later) |
| LOG | tail |

---

# 💪 Practice Exercises

## Exercise 1

Create a practice file.

```bash
touch practice.txt
```

---

## Exercise 2

Add text.

```bash
cat > practice.txt
```

Type:

```
Linux for Bioinformatics
```

Save using:

```
CTRL + D
```

---

## Exercise 3

Display the file.

```bash
cat practice.txt
```

---

## Exercise 4

View the first lines.

```bash
head practice.txt
```

---

## Exercise 5

View the last lines.

```bash
tail practice.txt
```

---

## Exercise 6

Open using less.

```bash
less practice.txt
```

Exit:

```
q
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Using `cat` on very large FASTQ files, which floods the terminal.
> - Forgetting to exit `less` using `q`.
> - Editing a file when you only intended to inspect it.
> - Using `tail` instead of `tail -f` when monitoring a running analysis.

---

# 🧠 Interview Corner

### ❓ What is the difference between `cat` and `less`?

`cat` prints the entire file to the terminal, while `less` allows you to navigate through the file page by page.

---

### ❓ Why is `head` useful in bioinformatics?

It quickly verifies the format of files such as FASTQ, FASTA, BED, GTF, and VCF before analysis.

---

### ❓ When should you use `tail -f`?

To monitor log files in real time while a bioinformatics tool (such as FastQC or an aligner) is running.

---

### ❓ Why should you avoid using `cat` on large FASTQ files?

Large sequencing files can contain millions of lines, making the output difficult to view and slowing down the terminal.

---

# 📝 Lesson Summary

- `cat` displays complete file contents.
- `less` is ideal for large files.
- `head` shows the beginning of a file.
- `tail` shows the end of a file.
- `tail -f` monitors files in real time.
- Inspecting files before analysis is a standard bioinformatics practice.

---

# ⚡ Quick Revision

| Command | Purpose |
|----------|---------|
| `cat` | Display entire file |
| `less` | Browse large files |
| `head` | Show first 10 lines |
| `head -20` | Show first 20 lines |
| `tail` | Show last 10 lines |
| `tail -20` | Show last 20 lines |
| `tail -f` | Monitor file in real time |
| `more` | Page-by-page viewing |

---

# 📚 References

- GNU Core Utilities Manual
- Ubuntu Documentation
- The Linux Documentation Project

---

# ➡️ Next Lesson

**Searching Files (`find`, `locate`, `which`, `whereis`)**
