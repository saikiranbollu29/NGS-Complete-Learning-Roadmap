# 🔍 Searching Files (find, locate, which, whereis)

> [!NOTE]
> **Module 3 • Lesson 6**
>
> Learn how to search for files, directories, and installed programs efficiently using Linux commands that are essential for bioinformatics workflows.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Search for files and folders.
- Find sequencing files quickly.
- Locate installed bioinformatics software.
- Search by filename, extension, size, and modification time.
- Answer Linux interview questions confidently.

---

# 📚 Prerequisites

- Linux Navigation
- File Management
- Viewing File Contents

---

# 💡 Real-Life Analogy

Imagine working in a biobank containing one million samples.

Instead of opening every freezer,

you search using the sample ID.

Linux search commands work exactly the same way.

---

# 🧬 Bioinformatics Scenario

Suppose your project looks like this:

```text
RNASeq_Project/

raw_data/

sample1_R1.fastq.gz

sample1_R2.fastq.gz

sample2_R1.fastq.gz

sample2_R2.fastq.gz

alignment/

sample1.bam

sample2.bam

variants/

sample1.vcf

sample2.vcf
```

Instead of browsing folders,

Linux can find everything instantly.

---

# 📌 Command 1 — find

## Purpose

Searches for files and directories.

---

## Syntax

```bash
find path options
```

---

## Example

Search current directory

```bash
find .
```

`.` means

```
Current Directory
```

---

## Find FASTQ Files

```bash
find . -name "*.fastq.gz"
```

Expected Output

```text
./raw_data/sample1_R1.fastq.gz

./raw_data/sample1_R2.fastq.gz

./raw_data/sample2_R1.fastq.gz

./raw_data/sample2_R2.fastq.gz
```

---

## Find BAM Files

```bash
find . -name "*.bam"
```

---

## Find VCF Files

```bash
find . -name "*.vcf"
```

---

## Ignore Uppercase/Lowercase

```bash
find . -iname "*.fastq.gz"
```

`-iname`

↓

Case insensitive

---

## Find Directories

```bash
find . -type d
```

---

## Find Only Files

```bash
find . -type f
```

---

## Find Files Larger Than 1 GB

```bash
find . -type f -size +1G
```

---

## Find Empty Files

```bash
find . -empty
```

---

## Find Recently Modified Files

Modified within the last 7 days:

```bash
find . -mtime -7
```

Modified more than 30 days ago:

```bash
find . -mtime +30
```

---

# 📌 Command 2 — locate

## Purpose

Finds files using a prebuilt database.

Usually much faster than `find`.

---

## Syntax

```bash
locate filename
```

---

## Example

```bash
locate genome.fa
```

---

## Update Database

```bash
sudo updatedb
```

Without updating,

new files may not appear.

---

# 📌 Command 3 — which

## Purpose

Shows the location of an executable command.

Very useful in bioinformatics.

---

## Syntax

```bash
which command
```

---

## Example

```bash
which bwa
```

Output

```text
/home/sai/miniconda3/envs/ngs/bin/bwa
```

---

## More Examples

```bash
which samtools

which fastqc

which python

which R
```

---

# 📌 Command 4 — whereis

## Purpose

Finds:

- Executable
- Source files
- Manual pages

---

## Syntax

```bash
whereis command
```

---

## Example

```bash
whereis bwa
```

Output

```text
bwa:
/home/sai/miniconda3/envs/ngs/bin/bwa
```

---

# 📊 Command Comparison

| Command | Best For |
|----------|----------|
| find | Search files and directories |
| locate | Very fast filename search |
| which | Find executable location |
| whereis | Find executable, source, and manual |

---

# 🧬 NGS Workflow Connection

Suppose you downloaded sequencing data.

Locate FASTQ files:

```bash
find raw_data -name "*.fastq.gz"
```

Locate reference genome:

```bash
find reference -name "*.fa"
```

Locate BAM files:

```bash
find alignment -name "*.bam"
```

Check BWA installation:

```bash
which bwa
```

Check Samtools installation:

```bash
which samtools
```

---

# 🧬 Real NGS Dataset Challenge

### Challenge 1

Find every FASTQ file.

```bash
find . -name "*.fastq.gz"
```

---

### Challenge 2

Find every BAM file.

```bash
find . -name "*.bam"
```

---

### Challenge 3

Find all VCF files.

```bash
find . -name "*.vcf"
```

---

### Challenge 4

Find files larger than 1 GB.

```bash
find . -type f -size +1G
```

---

### Challenge 5

Locate BWA.

```bash
which bwa
```

---

### Challenge 6

Locate FastQC.

```bash
which fastqc
```

---

### Challenge 7

Find empty log files.

```bash
find logs -empty
```

---

# 💪 Practice Exercises

## Exercise 1

Find every directory.

```bash
find . -type d
```

---

## Exercise 2

Find every file.

```bash
find . -type f
```

---

## Exercise 3

Find every `.txt` file.

```bash
find . -name "*.txt"
```

---

## Exercise 4

Locate Python.

```bash
which python
```

---

## Exercise 5

Locate R.

```bash
which R
```

---

## Exercise 6

Locate Bash.

```bash
whereis bash
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Forgetting quotes around wildcard patterns like `"*.fastq.gz"`.
> - Expecting `locate` to find newly created files before running `updatedb`.
> - Confusing `which` (executables only) with `find` (any file).
> - Running `find /` unnecessarily, which searches the entire system and can be slow.

---

# 🧠 Interview Corner

### ❓ What is the difference between `find` and `locate`?

`find` searches the file system in real time, while `locate` searches a prebuilt database, making it faster but potentially outdated.

---

### ❓ Why is `which` important in bioinformatics?

It confirms which version of a program (such as `bwa`, `samtools`, or `python`) will be executed, which is especially useful when using Conda environments.

---

### ❓ How do you find every FASTQ file in a project?

```bash
find . -name "*.fastq.gz"
```

---

### ❓ How do you check whether BWA is installed?

```bash
which bwa
```

---

# 📝 Lesson Summary

- `find` searches files and directories.
- `locate` provides fast filename searches.
- `which` finds the executable path of a command.
- `whereis` finds executables, source files, and manuals.
- These commands are used daily in bioinformatics projects.

---

# ⚡ Quick Revision

| Command | Purpose |
|----------|---------|
| `find .` | Search current directory |
| `find . -name "*.fastq.gz"` | Find FASTQ files |
| `find . -type f` | Find files |
| `find . -type d` | Find directories |
| `find . -size +1G` | Find files >1 GB |
| `locate filename` | Fast filename search |
| `which bwa` | Find executable |
| `whereis bwa` | Find executable, source, and manual |

---

# 📚 References

- GNU Findutils Manual
- Ubuntu Documentation
- The Linux Documentation Project

---

# ➡️ Next Lesson

**Text Processing with `grep`**
