# 🔐 File Permissions & Ownership (chmod, chown, umask)

> [!NOTE]
> **Module 3 • Lesson 12**
>
> Learn how Linux controls access to files and directories using permissions and ownership. This knowledge is essential for running bioinformatics pipelines on personal computers, servers, and HPC clusters.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand Linux permissions.
- Read permission strings.
- Change permissions using chmod.
- Change file ownership using chown.
- Understand umask.
- Solve "Permission denied" errors.

---

# 📚 Prerequisites

- Linux Navigation
- File Management
- Pipes and Redirection

---

# 💡 Real-Life Analogy

Imagine a laboratory.

Every room has access rules.

Some people can:

- Enter
- Read records
- Perform experiments

Others cannot.

Linux permissions work exactly the same way.

Every file has rules defining who can:

- Read
- Write
- Execute

---

# 📌 Why Permissions Matter

Bioinformatics projects often contain:

- Patient information
- Genome sequences
- Clinical reports
- Research data

Permissions help protect these files from accidental modification or unauthorized access.

---

# 📌 View Permissions

Use

```bash
ls -l
```

Example

```text
-rw-r--r-- 1 sai bioinfo 253 Jul 15 metadata.tsv
```

---

# Understanding the Output

```
-rw-r--r--

↓

Type

↓

Owner

↓

Group

↓

Others
```

---

## File Type

| Symbol | Meaning |
|----------|---------|
| - | File |
| d | Directory |
| l | Symbolic link |

---

## Permission Groups

```
-rw-r--r--

Owner

rw-

Group

r--

Others

r--
```

---

## Permission Meaning

| Symbol | Meaning |
|---------|----------|
| r | Read |
| w | Write |
| x | Execute |
| - | No permission |

---

# 📌 Numeric Permissions

Each permission has a number.

| Permission | Value |
|------------|------:|
| Read | 4 |
| Write | 2 |
| Execute | 1 |

Add them together.

Examples

```
7

=

4+2+1

=

rwx
```

```
6

=

4+2

=

rw-
```

```
5

=

4+1

=

r-x
```

```
4

=

Read Only
```

---

# Common Permission Values

| Number | Permission |
|----------|-----------|
| 777 | rwx rwx rwx |
| 755 | rwx r-x r-x |
| 700 | rwx --- --- |
| 644 | rw- r-- r-- |
| 600 | rw- --- --- |

---

# 📌 chmod

## Purpose

Changes file permissions.

---

## Syntax

```bash
chmod permissions filename
```

---

## Example

Make a shell script executable.

```bash
chmod +x fastqc.sh
```

Run it.

```bash
./fastqc.sh
```

---

## Numeric Method

```bash
chmod 755 fastqc.sh
```

---

## Make a File Read-Only

```bash
chmod 444 results.txt
```

---

## Owner Read & Write Only

```bash
chmod 600 metadata.tsv
```

---

# 📌 Recursive Permissions

Change an entire directory.

```bash
chmod -R 755 RNASeq_Project/
```

> [!WARNING]
>
> Be careful with recursive permission changes, especially on shared servers.

---

# 📌 chown

## Purpose

Changes the owner of a file or directory.

---

## Syntax

```bash
sudo chown owner filename
```

---

## Example

```bash
sudo chown sai metadata.tsv
```

---

## Change Owner and Group

```bash
sudo chown sai:bioinfo metadata.tsv
```

---

## Recursive Ownership

```bash
sudo chown -R sai RNASeq_Project/
```

---

# 📌 umask

## Purpose

Defines the default permissions for newly created files and directories.

---

## Check Current umask

```bash
umask
```

Example Output

```text
0022
```

---

## What Does 0022 Mean?

Default permissions are reduced by the umask value.

Typical results:

| Item | Default Permissions |
|------|---------------------|
| Files | 644 |
| Directories | 755 |

---

# 🧬 Bioinformatics Examples

### Make a Pipeline Script Executable

```bash
chmod +x run_pipeline.sh
```

---

### Protect Patient Metadata

```bash
chmod 600 patient_metadata.tsv
```

Only the owner can read and modify it.

---

### Allow Shared Access to Results

```bash
chmod 755 results/
```

---

### Verify BWA Script Permissions

```bash
ls -l run_bwa.sh
```

Example

```text
-rwxr-xr-x
```

---

# 🧬 NGS Workflow Connection

Before running a pipeline:

```bash
ls -l run_pipeline.sh
```

If not executable:

```bash
chmod +x run_pipeline.sh
```

Run:

```bash
./run_pipeline.sh
```

Without execute permission, Linux returns:

```text
Permission denied
```

---

# 🧬 Interview Lab

### Scenario

You downloaded:

```text
sample_R1.fastq.gz

sample_R2.fastq.gz
```

When running FastQC:

```bash
fastqc sample_R1.fastq.gz
```

Linux returns

```text
Permission denied
```

---

## Step 1

Check permissions.

```bash
ls -l sample_R1.fastq.gz
```

---

## Step 2

If needed, allow the owner to read and write.

```bash
chmod 600 sample_R1.fastq.gz
```

If appropriate, allow everyone to read.

```bash
chmod 644 sample_R1.fastq.gz
```

---

## Step 3

Run FastQC again.

---

# 📊 Common Permission Values

| Use Case | Permission |
|----------|------------|
| Shell Script | 755 |
| Metadata | 600 |
| FASTQ | 644 |
| Results Folder | 755 |
| Private Research Folder | 700 |

---

# 💪 Practice Exercises

## Exercise 1

Check permissions.

```bash
ls -l
```

---

## Exercise 2

Create a script.

```bash
touch test.sh
```

---

## Exercise 3

Make it executable.

```bash
chmod +x test.sh
```

---

## Exercise 4

Verify permissions.

```bash
ls -l test.sh
```

---

## Exercise 5

Check umask.

```bash
umask
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Using `chmod 777` unnecessarily. It gives read, write, and execute permissions to everyone and should generally be avoided.
> - Forgetting to make shell scripts executable before running them.
> - Running `chmod -R` in the wrong directory.
> - Confusing file ownership (`chown`) with file permissions (`chmod`).

---

# 🧠 Interview Corner

### ❓ What does chmod do?

Changes file or directory permissions.

---

### ❓ What does chown do?

Changes the owner (and optionally the group) of a file or directory.

---

### ❓ What does chmod 755 mean?

- Owner: Read, Write, Execute
- Group: Read, Execute
- Others: Read, Execute

---

### ❓ Why is chmod +x used?

To make a file executable, such as a shell script.

---

### ❓ Why should chmod 777 usually be avoided?

Because it grants full access to everyone, which can create security risks and accidental file modifications.

---

# 📝 Lesson Summary

- Linux controls file access using permissions.
- Permissions are divided into owner, group, and others.
- `chmod` changes permissions.
- `chown` changes ownership.
- `umask` defines default permissions.
- Understanding permissions is essential for working on Linux servers and HPC systems.

---

# ⚡ Quick Revision

| Command | Purpose |
|---------|---------|
| `ls -l` | View permissions |
| `chmod +x script.sh` | Make executable |
| `chmod 755 file` | Set permissions |
| `chmod 644 file` | Read/write for owner, read for others |
| `chmod 600 file` | Private file |
| `chown user file` | Change owner |
| `umask` | View default permissions |

---

# 📚 References

- GNU Core Utilities Manual
- Ubuntu Documentation
- Linux File Permission Guide

---

# ➡️ Next Lesson

**Compression & Archiving (`gzip`, `gunzip`, `tar`, `zip`, `unzip`)**
