# 🐧 Introduction to Linux for Bioinformatics

> [!NOTE]
> **Module 3 • Lesson 1**
>
> Learn why Linux is the standard operating system for bioinformatics and understand the Linux file system before starting NGS analysis.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Explain what Linux is.
- Understand why Linux is used in Bioinformatics.
- Identify the Linux file system.
- Navigate important directories.
- Understand the terminal.
- Answer Linux interview questions.

---

# 📚 Prerequisites

No prior Linux knowledge is required.

This lesson starts from absolute basics.

---

# 💡 Real-Life Analogy

Imagine a laboratory.

Every instrument has its own room.

- Microscopes → Imaging Room
- PCR Machine → Molecular Lab
- Sequencer → Sequencing Room

Linux organizes files in a similar way.

Everything has a specific location.

Understanding this organization makes it much easier to manage bioinformatics projects.

---

# 📌 What is Linux?

Linux is an open-source operating system widely used in:

- Bioinformatics
- Genomics
- Artificial Intelligence
- Cloud Computing
- High Performance Computing (HPC)
- Supercomputers

Most bioinformatics software is developed primarily for Linux.

---

# ❓ Why Bioinformaticians Use Linux

Linux offers several advantages:

- Free and open source
- Stable for long-running analyses
- Efficient memory management
- Easy software installation using package managers
- Powerful command-line interface
- Widely supported on research servers and HPC clusters

---

# 🧬 Why Learn Linux for NGS?

Almost every NGS pipeline runs on Linux.

Examples include:

- FastQC
- MultiQC
- BWA
- Bowtie2
- HISAT2
- STAR
- Samtools
- BCFtools
- GATK
- FreeBayes
- Minimap2

If you know Linux, you can run these tools efficiently and automate workflows.

---

# 📌 What is the Terminal?

The **Terminal** (also called the **Shell**) is a text-based interface where you type commands to interact with the operating system.

Example:

```bash
pwd
```

Output:

```text
/home/username
```

Instead of clicking folders with a mouse, you control the system using commands.

---

# 📂 Linux File System

Unlike Windows, Linux has a **single hierarchical file system** that starts from the **root directory**.

```text
/

├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

Everything in Linux begins from the root directory (`/`).

---

# 📌 Important Directories

| Directory | Purpose |
|-----------|---------|
| `/` | Root directory |
| `/home` | User home directories |
| `/usr` | Installed software and user applications |
| `/bin` | Essential command-line programs |
| `/etc` | Configuration files |
| `/tmp` | Temporary files |
| `/var` | Log files and variable data |
| `/opt` | Optional third-party software |
| `/mnt` | Mounted drives |
| `/dev` | Devices (disks, terminals, etc.) |

---

# 🧬 Bioinformatics Example

Suppose you create a project:

```text
/home/sai/RNASeq_Project/
```

Inside it:

```text
RNASeq_Project/

├── raw_data/
├── qc/
├── trimmed/
├── reference/
├── alignment/
├── counts/
├── results/
├── scripts/
└── logs/
```

This structure keeps sequencing data, analysis, and scripts organized.

---

# 📌 Linux vs Windows

| Feature | Linux | Windows |
|----------|--------|----------|
| Cost | Free | Commercial license |
| Bioinformatics Support | Excellent | Limited (native) |
| Command Line | Powerful | PowerShell / CMD |
| HPC Support | Excellent | Limited |
| Software Availability | Extensive | Often via WSL or containers |

---

# 📊 Where Linux is Used

- Research laboratories
- Universities
- Hospitals
- Cloud platforms (AWS, Azure, GCP)
- Supercomputers
- National genomics centers
- Pharmaceutical companies

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Thinking Linux and Ubuntu are the same thing.
> - Confusing the root directory (`/`) with the root user.
> - Expecting Linux to behave exactly like Windows.

---

# 🧠 Interview Corner

### ❓ What is Linux?

Linux is an open-source operating system widely used for scientific computing, bioinformatics, and high-performance computing.

---

### ❓ Why is Linux preferred in Bioinformatics?

Because most bioinformatics tools are designed for Linux, it provides better performance, automation, and compatibility with research computing environments.

---

### ❓ What is the root directory?

The root directory (`/`) is the top-level directory from which all other directories originate.

---

### ❓ What is the difference between `/` and `/home`?

- `/` is the root of the entire file system.
- `/home` contains personal directories for users.

---

# 📝 Lesson Summary

- Linux is the standard operating system for bioinformatics.
- Most NGS tools are developed for Linux.
- The Linux file system starts at the root directory (`/`).
- The terminal is the primary interface for running bioinformatics tools.
- Organizing projects properly is essential for reproducible analyses.

---

# ⚡ Quick Revision

| Question | Answer |
|----------|--------|
| Linux? | Open-source operating system |
| Why Linux? | Most bioinformatics tools run on it |
| Root Directory? | `/` |
| User Files? | `/home` |
| Configuration Files? | `/etc` |
| Temporary Files? | `/tmp` |

---

# 📚 References

- The Linux Documentation Project
- Ubuntu Documentation
- GNU Project
- Bioinformatics Data Skills (Book)

---

# ➡️ Next Lesson

**Installing Ubuntu, WSL & Terminal**
