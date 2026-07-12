  # 🛠 Installing Bioinformatics Tools with Bioconda

> [!NOTE]
> **Module 4 • Lesson 1**
>
> Learn how to install the most widely used bioinformatics software using Bioconda. These tools form the foundation of modern NGS analysis pipelines.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand Bioconda.
- Configure Conda channels correctly.
- Install common bioinformatics software.
- Verify installations.
- Organize tools into project-specific environments.
- Troubleshoot installation problems.

---

# 📚 Prerequisites

- Linux Basics
- Conda & Mamba
- Environment Variables

---

# 💡 Why Bioconda?

Installing bioinformatics software manually is difficult because many tools depend on:

- C/C++
- Java
- Python
- Perl
- R
- HTSlib
- zlib
- Boost

Bioconda automatically installs these dependencies.

---

# 📌 What is Bioconda?

Bioconda is a Conda channel that provides thousands of bioinformatics packages.

Advantages:

- Easy installation
- Dependency management
- Cross-platform support
- Reproducible environments
- Active community support

Currently, Bioconda hosts thousands of bioinformatics packages covering genomics, transcriptomics, proteomics, metagenomics, phylogenetics, and more.

---

# 📌 Configure Conda Channels

Run these commands only once.

```bash
conda config --add channels defaults

conda config --add channels bioconda

conda config --add channels conda-forge

conda config --set channel_priority strict
```

Verify:

```bash
conda config --show channels
```

Expected Output

```text
channels:

- conda-forge

- bioconda

- defaults
```

---

# 📌 Create an NGS Environment

```bash
mamba create -n ngs python=3.11
```

Activate:

```bash
conda activate ngs
```

---

# 📌 Install FastQC

```bash
mamba install fastqc -c bioconda
```

Verify:

```bash
fastqc --version
```

Example

```text
FastQC v0.12.1
```

Purpose

✔ Raw sequencing quality assessment

---

# 📌 Install MultiQC

```bash
mamba install multiqc -c bioconda
```

Verify

```bash
multiqc --version
```

Purpose

✔ Combine reports from multiple QC tools

---

# 📌 Install BWA

```bash
mamba install bwa -c bioconda
```

Verify

```bash
bwa
```

Purpose

✔ DNA sequence alignment

---

# 📌 Install HISAT2

```bash
mamba install hisat2 -c bioconda
```

Verify

```bash
hisat2 --version
```

Purpose

✔ RNA-Seq alignment

---

# 📌 Install STAR

```bash
mamba install star -c bioconda
```

Verify

```bash
STAR --version
```

Purpose

✔ High-speed RNA-Seq alignment

---

# 📌 Install Samtools

```bash
mamba install samtools -c bioconda
```

Verify

```bash
samtools --version
```

Purpose

✔ Manipulate SAM/BAM/CRAM files

---

# 📌 Install BCFtools

```bash
mamba install bcftools -c bioconda
```

Verify

```bash
bcftools --version
```

Purpose

✔ Process VCF and BCF files

---

# 📌 Install GATK

```bash
mamba install gatk4 -c bioconda
```

Verify

```bash
gatk --version
```

Purpose

✔ Variant discovery and genotyping

---

# 📊 Tool Summary

| Tool | Purpose | Used In |
|------|---------|----------|
| FastQC | Read quality assessment | All NGS |
| MultiQC | Aggregate QC reports | All NGS |
| BWA | DNA alignment | WGS/WES |
| HISAT2 | RNA alignment | RNA-Seq |
| STAR | RNA alignment | RNA-Seq |
| Samtools | BAM/SAM processing | All NGS |
| BCFtools | Variant processing | WGS/WES |
| GATK | Variant calling | WGS/WES |

---

# 🧬 Typical NGS Workflow

```
FASTQ

↓

FastQC

↓

MultiQC

↓

Alignment

↓

BWA / HISAT2 / STAR

↓

SAM/BAM

↓

Samtools

↓

BCFtools / GATK

↓

VCF

↓

Variant Annotation
```

---

# 🧬 Verify Installation

Locate each tool.

```bash
which fastqc

which multiqc

which bwa

which hisat2

which STAR

which samtools

which bcftools

which gatk
```

Example

```text
/home/user/miniconda3/envs/ngs/bin/fastqc
```

---

# 🧬 Interview Lab

### Scenario

You have created a new environment named `ngs`.

Install all essential NGS software.

```bash
mamba install \
fastqc \
multiqc \
bwa \
hisat2 \
star \
samtools \
bcftools \
gatk4 \
-c bioconda
```

Verify

```bash
fastqc --version

samtools --version

gatk --version
```

---

# 💪 Practice Exercises

## Exercise 1

Create a new environment.

```bash
mamba create -n ngs python=3.11
```

---

## Exercise 2

Activate it.

```bash
conda activate ngs
```

---

## Exercise 3

Install FastQC.

```bash
mamba install fastqc -c bioconda
```

---

## Exercise 4

Verify FastQC.

```bash
fastqc --version
```

---

## Exercise 5

Locate Samtools.

```bash
which samtools
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Installing tools in the `base` environment instead of a project-specific environment.
> - Forgetting to activate the correct environment before running tools.
> - Mixing incompatible Conda channels.
> - Assuming installation succeeded without checking the tool version.

---

# 🧠 Interview Corner

### ❓ What is Bioconda?

A Conda channel that provides bioinformatics software with automatic dependency management.

---

### ❓ Why is Mamba preferred over Conda?

It resolves dependencies and installs packages much faster.

---

### ❓ Why should FastQC and BWA be installed in an isolated environment?

To avoid dependency conflicts with other projects and ensure reproducibility.

---

### ❓ How do you verify that Samtools is installed?

```bash
samtools --version
```

or

```bash
which samtools
```

---

### ❓ Which aligner would you use for WGS and RNA-Seq?

- **WGS/WES:** BWA
- **RNA-Seq:** HISAT2 or STAR

---

# 📝 Lesson Summary

- Bioconda is the standard package source for bioinformatics tools.
- Create separate environments for different workflows.
- Always verify installations after installing software.
- FastQC, BWA, HISAT2, STAR, Samtools, BCFtools, and GATK are core tools in NGS analysis.

---

# ⚡ Quick Revision

| Tool | Main Purpose |
|------|--------------|
| FastQC | Quality control |
| MultiQC | QC report aggregation |
| BWA | DNA alignment |
| HISAT2 | RNA-Seq alignment |
| STAR | RNA-Seq alignment |
| Samtools | BAM/SAM processing |
| BCFtools | VCF processing |
| GATK | Variant calling |

---

# 📚 References

- Bioconda Documentation
- Conda Documentation
- FastQC Documentation
- MultiQC Documentation
- BWA Manual
- HISAT2 Manual
- STAR Manual
- Samtools Documentation
- BCFtools Documentation
- GATK Documentation

---

# ➡️ Next Lesson

**FastQC: Sequencing Quality Control (Theory + Hands-on + Interview Questions)**
