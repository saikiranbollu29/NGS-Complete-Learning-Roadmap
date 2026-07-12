# 🐍 Conda & Mamba for Bioinformatics

> [!NOTE]
> **Module 3 • Lesson 17**
>
> Learn how to create isolated environments, install bioinformatics software, manage dependencies, and use Conda and Mamba efficiently.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand Conda and Mamba.
- Create isolated environments.
- Install bioinformatics software.
- Manage package dependencies.
- Export and share environments.
- Follow best practices for NGS projects.

---

# 📚 Prerequisites

- Linux Basics
- PATH
- Bash Scripting

---

# 💡 Real-Life Analogy

Imagine a laboratory.

Each research project has its own room.

Each room contains:

- Different reagents
- Different instruments
- Different protocols

Projects do not interfere with each other.

Conda environments work exactly like these separate laboratory rooms.

---

# 📌 Why Do We Need Conda?

Bioinformatics tools often require different software versions.

Example:

| Tool | Python Version |
|------|----------------|
| FastQC | Java |
| MultiQC | Python 3.11 |
| GATK | Java 17 |
| TensorFlow | Python 3.10 |
| PyTorch | Python 3.12 |

Installing everything together can create dependency conflicts.

Conda solves this by creating isolated environments.

---

# 📌 What is Conda?

Conda is a package and environment manager.

It can:

- Install software
- Create environments
- Manage dependencies
- Update packages
- Remove packages

---

# 📌 What is Mamba?

Mamba is a faster implementation of Conda.

Advantages:

- Faster dependency solving
- Faster installation
- Fully compatible with Conda commands

---

# 📊 Conda vs Mamba

| Feature | Conda | Mamba |
|---------|-------|--------|
| Environment Management | ✅ | ✅ |
| Package Installation | ✅ | ✅ |
| Dependency Solving | Slower | Faster |
| Compatibility | Standard | Fully Compatible |

---

# 📌 Check Installation

Check Conda.

```bash
conda --version
```

Example

```text
conda 25.x.x
```

Check Mamba.

```bash
mamba --version
```

---

# 📌 Create an Environment

```bash
conda create -n rnaseq python=3.11
```

Explanation

```
create

↓

New Environment

-n

↓

Environment Name
```

---

# 📌 Activate Environment

```bash
conda activate rnaseq
```

Prompt changes

```text
(rnaseq)
user@ubuntu:~$
```

---

# 📌 Deactivate Environment

```bash
conda deactivate
```

---

# 📌 List Environments

```bash
conda env list
```

or

```bash
conda info --envs
```

Example

```text
base

rnaseq

wes

wgs

metagenomics
```

---

# 📌 Install Packages

Install FastQC.

```bash
conda install -c bioconda fastqc
```

---

Install MultiQC.

```bash
conda install -c bioconda multiqc
```

---

Install BWA.

```bash
conda install -c bioconda bwa
```

---

Install Samtools.

```bash
conda install -c bioconda samtools
```

---

Install HISAT2.

```bash
conda install -c bioconda hisat2
```

---

Install STAR.

```bash
conda install -c bioconda star
```

---

# 📌 Install Using Mamba

Simply replace

```bash
conda
```

with

```bash
mamba
```

Example

```bash
mamba install -c bioconda fastqc
```

---

# 📌 Search Packages

```bash
conda search fastqc
```

---

# 📌 Update Package

```bash
conda update fastqc
```

---

# 📌 Remove Package

```bash
conda remove fastqc
```

---

# 📌 Remove Environment

```bash
conda env remove -n rnaseq
```

---

# 📌 Export Environment

Create a YAML file.

```bash
conda env export > environment.yml
```

Example

```text
environment.yml
```

This file records:

- Environment name
- Packages
- Versions
- Channels

---

# 📌 Create Environment from YAML

```bash
conda env create -f environment.yml
```

Very useful for sharing projects.

---

# 🧬 Recommended Bioinformatics Environments

Instead of installing everything in one environment:

```text
rnaseq

↓

RNA-Seq Tools
```

```text
wes

↓

Variant Calling Tools
```

```text
wgs

↓

Whole Genome Tools
```

```text
metagenomics

↓

Microbiome Tools
```

```text
ml

↓

Machine Learning
```

---

# 🧬 NGS Workflow Connection

Example RNA-Seq environment.

```bash
conda create -n rnaseq python=3.11
```

Activate.

```bash
conda activate rnaseq
```

Install tools.

```bash
mamba install fastqc multiqc hisat2 samtools -c bioconda
```

Verify.

```bash
which fastqc

which hisat2

which samtools
```

---

# 🧬 Interview Lab

### Scenario

You receive a project requiring:

- FastQC
- HISAT2
- Samtools
- MultiQC

Should you install them in the base environment?

❌ No.

Create a separate environment.

```bash
conda create -n rnaseq python=3.11

conda activate rnaseq

mamba install fastqc hisat2 samtools multiqc -c bioconda
```

---

# 💪 Practice Exercises

## Exercise 1

Create an environment.

```bash
conda create -n practice python=3.11
```

---

## Exercise 2

Activate it.

```bash
conda activate practice
```

---

## Exercise 3

Install FastQC.

```bash
mamba install -c bioconda fastqc
```

---

## Exercise 4

Verify installation.

```bash
fastqc --version
```

---

## Exercise 5

Export the environment.

```bash
conda env export > environment.yml
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Installing all software in the `base` environment.
> - Forgetting to activate the correct environment before running tools.
> - Mixing packages from incompatible channels.
> - Not exporting the environment for reproducibility.

---

# 🧠 Interview Corner

### ❓ What is Conda?

A package and environment manager used to install software and isolate project dependencies.

---

### ❓ What is the advantage of Mamba?

It installs packages and resolves dependencies much faster than Conda.

---

### ❓ Why should you avoid using the base environment?

To prevent dependency conflicts and keep the base installation clean.

---

### ❓ How do you share an environment with another researcher?

Export it using:

```bash
conda env export > environment.yml
```

and recreate it with:

```bash
conda env create -f environment.yml
```

---

### ❓ Why are isolated environments important in bioinformatics?

Different tools often require different software versions. Isolated environments ensure that installing or updating one tool does not break another project.

---

# 📝 Lesson Summary

- Conda manages packages and environments.
- Mamba provides faster package installation.
- Use one environment per project or workflow.
- Export environments for reproducibility.
- Never install all bioinformatics tools in the base environment.

---

# ⚡ Quick Revision

| Command | Purpose |
|---------|---------|
| `conda create -n env python=3.11` | Create environment |
| `conda activate env` | Activate environment |
| `conda deactivate` | Exit environment |
| `conda env list` | List environments |
| `mamba install package` | Install package |
| `conda update package` | Update package |
| `conda remove package` | Remove package |
| `conda env export > environment.yml` | Export environment |
| `conda env create -f environment.yml` | Recreate environment |

---

# 📚 References

- Conda Documentation
- Mamba Documentation
- Bioconda Documentation
- Conda-Forge Documentation

---

# ➡️ Next Lesson

**Installing Bioinformatics Tools with Bioconda (FastQC, MultiQC, BWA, HISAT2, STAR, Samtools, BCFtools, GATK)**
