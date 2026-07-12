# 📂 Navigating Directories (pwd, ls, cd)

> [!NOTE]
> **Module 3 • Lesson 3**
>
> Learn how to move around the Linux file system using the three most important commands: `pwd`, `ls`, and `cd`.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Navigate through directories.
- Display the current location.
- List files and folders.
- Move between directories.
- Understand absolute and relative paths.
- Use these commands in bioinformatics projects.

---

# 📚 Prerequisites

- Module 3 Lesson 1
- Module 3 Lesson 2

---

# 💡 Real-Life Analogy

Imagine you are inside a hospital.

Before going anywhere, you need to know:

- Which room am I in?
- What rooms are nearby?
- How do I move to another room?

Linux works exactly the same way.

| Question | Linux Command |
|----------|---------------|
| Where am I? | `pwd` |
| What is here? | `ls` |
| Go somewhere else | `cd` |

---

# 🧬 Bioinformatics Scenario

Suppose you've downloaded RNA-Seq data.

Your project looks like this:

```text
RNASeq_Project/

├── raw_data/
├── qc/
├── trimmed/
├── alignment/
├── counts/
├── results/
├── scripts/
└── logs/
```

You'll move between these folders many times during analysis.

---

# 📌 Command 1 — pwd

## Purpose

Displays the **current working directory**.

Think of it as asking:

> **"Where am I?"**

---

## Syntax

```bash
pwd
```

---

## Example

```bash
pwd
```

---

## Expected Output

```text
/home/sai/RNASeq_Project
```

---

## Explanation

```
pwd

↓

Print

Working

Directory
```

It displays the full path of your current location.

---

## Bioinformatics Example

```bash
cd ~/RNASeq_Project

pwd
```

Output

```text
/home/sai/RNASeq_Project
```

Before running FastQC or BWA, always check you're in the correct directory.

---

# 📌 Command 2 — ls

## Purpose

Lists the contents of the current directory.

Think of it as asking:

> **"What files and folders are here?"**

---

## Syntax

```bash
ls
```

---

## Example

```bash
ls
```

---

## Expected Output

```text
alignment

counts

logs

qc

raw_data

reference

results

scripts

trimmed
```

---

## Common Options

### List with Details

```bash
ls -l
```

Shows:

- Permissions
- Owner
- Size
- Date
- File name

---

### Human Readable Size

```bash
ls -lh
```

Example

```text
2.1G sample_R1.fastq.gz

2.0G sample_R2.fastq.gz
```

Very useful for checking FASTQ sizes.

---

### Show Hidden Files

```bash
ls -a
```

Displays hidden files like

```text
.bashrc

.profile
```

---

### Combine Options

```bash
ls -lah
```

One of the most commonly used Linux commands.

---

# Bioinformatics Example

Check downloaded FASTQ files

```bash
cd raw_data

ls -lh
```

Example

```text
2.1G SRR123456_R1.fastq.gz

2.0G SRR123456_R2.fastq.gz
```

---

# 📌 Command 3 — cd

## Purpose

Changes the current directory.

Think of it as:

> **"Go to another folder."**

---

## Syntax

```bash
cd directory_name
```

---

## Example

Move into raw_data

```bash
cd raw_data
```

Check location

```bash
pwd
```

Output

```text
/home/sai/RNASeq_Project/raw_data
```

---

# Move Back

```bash
cd ..
```

The two dots (`..`) mean:

```
Parent Directory
```

Example

```
raw_data

↓

RNASeq_Project
```

---

# Go Home

```bash
cd
```

or

```bash
cd ~
```

Output

```text
/home/sai
```

---

# Absolute Path

Starts from the root directory (`/`).

Example

```bash
cd /home/sai/RNASeq_Project/raw_data
```

Absolute paths always begin with `/`.

---

# Relative Path

Starts from your current directory.

Suppose you are here:

```text
/home/sai/RNASeq_Project
```

Then

```bash
cd raw_data
```

works because `raw_data` is inside the current directory.

---

# Quick Comparison

| Path Type | Example |
|-----------|---------|
| Absolute | `/home/sai/RNASeq_Project/raw_data` |
| Relative | `raw_data` |

---

# Useful Shortcuts

| Command | Meaning |
|----------|---------|
| `cd` | Home directory |
| `cd ~` | Home directory |
| `cd ..` | Parent directory |
| `cd -` | Previous directory |
| `pwd` | Current directory |
| `ls` | List files |

---

# Typical Bioinformatics Workflow

```bash
cd ~/RNASeq_Project

pwd

ls

cd raw_data

ls -lh

cd ..

cd qc

pwd
```

---

# Expected Output

```text
/home/sai/RNASeq_Project

alignment

qc

raw_data

results

scripts

trimmed

/home/sai/RNASeq_Project/qc
```

---

# 🏥 Real Laboratory Example

You receive:

```text
SRR123456_R1.fastq.gz

SRR123456_R2.fastq.gz
```

First check the location

```bash
pwd
```

Move to raw data

```bash
cd raw_data
```

Verify files

```bash
ls -lh
```

Only then begin quality control.

---

# 💪 Practice Exercises

## Exercise 1

Check current directory.

```bash
pwd
```

---

## Exercise 2

Go to your home directory.

```bash
cd
```

---

## Exercise 3

Return to your project.

```bash
cd ~/RNASeq_Project
```

---

## Exercise 4

List all files including hidden ones.

```bash
ls -la
```

---

## Exercise 5

Move into raw_data.

```bash
cd raw_data
```

---

## Exercise 6

Return to the previous directory.

```bash
cd ..
```

---

## Exercise 7

Go back to the previous location.

```bash
cd -
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Forgetting to check the current directory before running commands.
> - Confusing `.` (current directory) with `..` (parent directory).
> - Using Windows-style paths (`C:\Users\...`) instead of Linux paths (`/home/...`).
> - Running commands in the wrong project directory.

---

# 🧠 Interview Corner

### ❓ What does `pwd` do?

Displays the full path of the current working directory.

---

### ❓ What is the difference between `ls` and `ls -lh`?

`ls` lists file names only, while `ls -lh` also displays detailed information such as permissions, owner, modification date, and human-readable file sizes.

---

### ❓ What does `cd ..` do?

Moves to the parent directory.

---

### ❓ What is the difference between an absolute path and a relative path?

An absolute path starts from the root directory (`/`), while a relative path starts from the current working directory.

---

# 📝 Lesson Summary

- `pwd` shows your current location.
- `ls` lists files and directories.
- `cd` changes directories.
- Absolute paths begin with `/`.
- Relative paths depend on your current location.
- These commands are used constantly in bioinformatics workflows.

---

# ⚡ Quick Revision

| Command | Purpose |
|----------|---------|
| `pwd` | Show current directory |
| `ls` | List files |
| `ls -lh` | List with human-readable sizes |
| `ls -la` | List all files, including hidden |
| `cd folder` | Enter a folder |
| `cd ..` | Go to parent directory |
| `cd ~` | Go to home directory |
| `cd -` | Return to previous directory |

---

# 📚 References

- Ubuntu Documentation
- GNU Core Utilities Manual
- The Linux Documentation Project

---

# ➡️ Next Lesson

**Creating, Copying, Moving & Deleting Files (`mkdir`, `touch`, `cp`, `mv`, `rm`)**
