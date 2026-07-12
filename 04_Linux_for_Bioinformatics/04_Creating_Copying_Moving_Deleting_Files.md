# 📁 Creating, Copying, Moving & Deleting Files

> [!NOTE]
> **Module 3 • Lesson 4**
>
> Learn how to create directories and files, copy and move data, rename files, and safely remove unwanted files. These commands are used daily in bioinformatics workflows.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Create directories.
- Create empty files.
- Copy files and folders.
- Move and rename files.
- Delete files and directories safely.
- Build a professional bioinformatics project structure.

---

# 📚 Prerequisites

- Module 3 Lesson 1
- Module 3 Lesson 2
- Module 3 Lesson 3

---

# 💡 Real-Life Analogy

Imagine you are starting a new research project.

You first:

- Create project folders.
- Store raw sequencing data.
- Copy backup files.
- Move analysis results.
- Delete unnecessary temporary files.

Linux commands perform exactly these tasks.

---

# 🧬 Mini Bioinformatics Lab

Today we'll build a complete RNA-Seq project.

Expected structure:

```text
RNASeq_Project/

├── raw_data/
├── qc/
├── trimmed/
├── reference/
├── alignment/
├── counts/
├── variants/
├── annotation/
├── results/
├── scripts/
└── logs/
```

---

# 📌 Command 1 — mkdir

## Purpose

Creates a new directory (folder).

---

## Syntax

```bash
mkdir directory_name
```

---

## Example

```bash
mkdir RNASeq_Project
```

---

## Expected Output

No output.

Check using:

```bash
ls
```

Output:

```text
RNASeq_Project
```

---

## Explanation

```
mkdir

↓

Make Directory
```

Creates a new folder.

---

## Bioinformatics Example

Create the project directory.

```bash
mkdir RNASeq_Project
```

Move into it.

```bash
cd RNASeq_Project
```

---

# Creating Multiple Directories

Instead of creating folders one by one,

use:

```bash
mkdir raw_data qc trimmed reference alignment counts variants annotation results scripts logs
```

Now check:

```bash
ls
```

Expected Output

```text
alignment

annotation

counts

logs

qc

raw_data

reference

results

scripts

trimmed

variants
```

---

# Create Nested Directories

```bash
mkdir -p data/raw/fastq
```

Output:

```text
data/

└── raw/

    └── fastq/
```

The `-p` option creates parent directories automatically.

---

# 📌 Command 2 — touch

## Purpose

Creates an empty file.

---

## Syntax

```bash
touch filename
```

---

## Example

```bash
touch notes.txt
```

Check:

```bash
ls
```

Output

```text
notes.txt
```

---

## Bioinformatics Example

Create a script.

```bash
touch fastqc.sh
```

Create metadata.

```bash
touch metadata.csv
```

Create README.

```bash
touch README.md
```

---

# 📌 Command 3 — cp

## Purpose

Copies files or directories.

---

## Syntax

```bash
cp source destination
```

---

## Example

```bash
cp metadata.csv backup_metadata.csv
```

---

## Expected Output

```text
metadata.csv

backup_metadata.csv
```

---

## Bioinformatics Example

Copy FASTQ files.

```bash
cp sample_R1.fastq.gz raw_data/
```

Copy paired reads.

```bash
cp sample_R2.fastq.gz raw_data/
```

---

# Copy Entire Directory

```bash
cp -r scripts scripts_backup
```

`-r`

↓

Recursive Copy

Required for directories.

---

# 📌 Command 4 — mv

## Purpose

Moves or renames files.

---

## Syntax

```bash
mv source destination
```

---

## Rename Example

```bash
mv notes.txt project_notes.txt
```

---

## Move Example

```bash
mv project_notes.txt results/
```

---

## Bioinformatics Example

Move a FASTQ file.

```bash
mv sample.fastq.gz raw_data/
```

Move a BAM file.

```bash
mv sample.sorted.bam alignment/
```

Move a VCF file.

```bash
mv variants.vcf variants/
```

---

# 📌 Command 5 — rm

## Purpose

Removes files.

---

## Syntax

```bash
rm filename
```

---

## Example

```bash
rm notes.txt
```

---

## Remove Directory

```bash
rm -r folder_name
```

Example

```bash
rm -r temp
```

---

## Force Remove

```bash
rm -rf temp
```

> [!WARNING]
>
> `rm -rf` permanently deletes files and directories without asking for confirmation.
>
> Always verify the path before running this command.

---

# 📌 Helpful Option

Ask before deleting:

```bash
rm -i file.txt
```

Linux asks:

```
remove regular file?

y/n
```

Safer for beginners.

---

# 📊 Command Summary

| Command | Purpose |
|----------|----------|
| mkdir | Create directory |
| mkdir -p | Create nested directories |
| touch | Create empty file |
| cp | Copy file |
| cp -r | Copy directory |
| mv | Move or rename |
| rm | Delete file |
| rm -r | Delete directory |
| rm -i | Delete with confirmation |

---

# 🧬 Complete Mini Bioinformatics Lab

Create project.

```bash
mkdir RNASeq_Project
```

Enter project.

```bash
cd RNASeq_Project
```

Create folders.

```bash
mkdir raw_data qc trimmed reference alignment counts variants annotation results scripts logs
```

Create files.

```bash
touch README.md

touch metadata.csv

touch scripts/fastqc.sh
```

Check structure.

```bash
ls
```

---

# Expected Output

```text
alignment

annotation

counts

logs

qc

raw_data

README.md

reference

results

scripts

trimmed

variants

metadata.csv
```

---

# 💪 Practice Exercises

## Exercise 1

Create a folder named:

```text
WGS_Project
```

---

## Exercise 2

Inside it create:

```text
raw_data

alignment

variants

results
```

---

## Exercise 3

Create a file:

```text
sample_information.csv
```

---

## Exercise 4

Rename it to:

```text
metadata.csv
```

---

## Exercise 5

Copy it into the results folder.

---

## Exercise 6

Delete the copied file.

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Forgetting `-r` when copying directories.
> - Using `rm -rf` without checking the path.
> - Confusing `cp` (copy) with `mv` (move).
> - Creating projects in the wrong directory.

---

# 🧠 Interview Corner

### ❓ What does `mkdir` do?

Creates a new directory.

---

### ❓ Difference between `cp` and `mv`?

- `cp` creates a copy while keeping the original.
- `mv` moves or renames the original file.

---

### ❓ Why use `mkdir -p`?

It creates parent and child directories in a single command without errors if intermediate directories don't exist.

---

### ❓ Why is `rm -rf` dangerous?

Because it permanently deletes files and directories recursively without confirmation.

---

# 📝 Lesson Summary

- `mkdir` creates folders.
- `touch` creates empty files.
- `cp` copies files.
- `mv` moves or renames files.
- `rm` deletes files.
- Organizing project folders is an essential bioinformatics practice.

---

# ⚡ Quick Revision

| Command | Purpose |
|----------|---------|
| `mkdir` | Create folder |
| `mkdir -p` | Create nested folders |
| `touch` | Create empty file |
| `cp` | Copy file |
| `cp -r` | Copy folder |
| `mv` | Move or rename |
| `rm` | Delete file |
| `rm -r` | Delete folder |
| `rm -rf` | Force delete recursively |

---

# 📚 References

- GNU Core Utilities Manual
- Ubuntu Documentation
- The Linux Documentation Project

---

# ➡️ Next Lesson

**Viewing File Contents (`cat`, `less`, `head`, `tail`)**
