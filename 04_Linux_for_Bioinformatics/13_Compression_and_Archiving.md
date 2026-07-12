# 📦 Compression & Archiving

> [!NOTE]
> **Module 3 • Lesson 13**
>
> Learn how to compress, decompress, archive, and inspect compressed bioinformatics files using Linux commands. Most sequencing datasets are distributed in compressed formats, making these commands essential for everyday genomics work.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand compression and archiving.
- Compress and decompress files.
- Inspect compressed FASTQ and FASTA files.
- Search inside compressed files.
- Create project archives.
- Understand common compressed genomic file formats.

---

# 📚 Prerequisites

- Linux Navigation
- Viewing Files
- grep
- Pipes

---

# 💡 Real-Life Analogy

Imagine moving an entire laboratory to another city.

Instead of transporting every item individually,

you pack everything into a few boxes.

Compression works similarly.

It reduces file size for easier storage and transfer.

---

# 📌 Compression vs Archiving

Many beginners think these are the same.

They are different.

| Operation | Purpose |
|------------|---------|
| Compression | Reduce file size |
| Archiving | Combine multiple files into one archive |

---

# 📌 Common File Extensions

| Extension | Meaning |
|-----------|---------|
| .gz | Gzip compressed file |
| .tar | Archive containing multiple files |
| .tar.gz | Tar archive compressed with gzip |
| .zip | ZIP archive |
| .bz2 | Bzip2 compressed file |
| .xz | XZ compressed file |

---

# 📌 gzip

## Purpose

Compress a file.

---

## Syntax

```bash
gzip filename
```

---

## Example

```bash
gzip sample.fastq
```

Output

```text
sample.fastq.gz
```

Original file is replaced by the compressed version.

---

# 📌 gunzip

## Purpose

Decompress a gzip file.

---

## Syntax

```bash
gunzip sample.fastq.gz
```

Output

```text
sample.fastq
```

---

# 📌 Keep Original File

Compress while keeping the original.

```bash
gzip -k sample.fastq
```

---

Decompress while keeping the compressed file.

```bash
gunzip -k sample.fastq.gz
```

---

# 📌 View Compressed Files Without Decompressing

## zcat

Display the contents of a compressed file.

```bash
zcat sample.fastq.gz
```

---

## View First Reads

```bash
zcat sample.fastq.gz | head
```

---

## Count Reads

```bash
zcat sample.fastq.gz | grep "^@" | wc -l
```

---

# 📌 zless

View compressed files page by page.

```bash
zless genome.fa.gz
```

Exit

```
q
```

---

# 📌 zgrep

Search inside compressed files.

```bash
zgrep "^>" genome.fa.gz
```

Search for BRCA1.

```bash
zgrep "BRCA1" annotation.gtf.gz
```

---

# 📌 tar

## Purpose

Combine multiple files into one archive.

---

## Create Archive

```bash
tar -cvf RNASeq_Project.tar RNASeq_Project/
```

Options

```
-c

Create

-v

Verbose

-f

File
```

---

## List Archive Contents

```bash
tar -tvf RNASeq_Project.tar
```

---

## Extract Archive

```bash
tar -xvf RNASeq_Project.tar
```

Options

```
-x

Extract
```

---

# 📌 Create tar.gz

Archive and compress together.

```bash
tar -czvf RNASeq_Project.tar.gz RNASeq_Project/
```

---

Extract

```bash
tar -xzvf RNASeq_Project.tar.gz
```

---

# 📌 zip

Compress multiple files.

```bash
zip project.zip *.txt
```

Compress folder.

```bash
zip -r project.zip RNASeq_Project/
```

---

# 📌 unzip

Extract ZIP archive.

```bash
unzip project.zip
```

---

# 📊 Common Commands

| Command | Purpose |
|---------|---------|
| gzip | Compress |
| gunzip | Decompress |
| gzip -k | Compress and keep original |
| zcat | Display compressed file |
| zless | Browse compressed file |
| zgrep | Search compressed file |
| tar | Archive |
| tar -czvf | Archive + Compress |
| unzip | Extract ZIP |

---

# 🧬 NGS Workflow Connection

Downloaded sequencing files.

```text
sample_R1.fastq.gz

sample_R2.fastq.gz
```

Inspect without decompressing.

```bash
zcat sample_R1.fastq.gz | head
```

Search FASTA headers.

```bash
zgrep "^>" genome.fa.gz
```

Archive project.

```bash
tar -czvf RNASeq_Project.tar.gz RNASeq_Project/
```

Transfer archive to HPC.

```bash
scp RNASeq_Project.tar.gz user@server:/data/
```

---

# 📌 Understanding .gz vs .tar.gz

## .gz

One compressed file.

```
sample.fastq

↓

gzip

↓

sample.fastq.gz
```

---

## .tar.gz

Many files packed together and compressed.

```
RNASeq_Project/

↓

tar

↓

RNASeq_Project.tar

↓

gzip

↓

RNASeq_Project.tar.gz
```

---

# 📌 Bioinformatics File Types

| File | Usually Compressed? |
|------|----------------------|
| FASTQ | Yes (.fastq.gz) |
| FASTA | Often (.fa.gz) |
| GTF | Often (.gtf.gz) |
| BED | Sometimes |
| VCF | Yes (.vcf.gz) |
| BAM | Already compressed |
| CRAM | Already compressed |

---

# 🧬 Real NGS Dataset Challenge

## Challenge 1

Inspect a compressed FASTQ.

```bash
zcat sample_R1.fastq.gz | head
```

---

## Challenge 2

Search chromosome headers.

```bash
zgrep "^>" genome.fa.gz
```

---

## Challenge 3

Create project archive.

```bash
tar -czvf RNASeq_Project.tar.gz RNASeq_Project/
```

---

## Challenge 4

Extract archive.

```bash
tar -xzvf RNASeq_Project.tar.gz
```

---

## Challenge 5

Search BRCA1.

```bash
zgrep "BRCA1" annotation.gtf.gz
```

---

# 💪 Practice Exercises

## Exercise 1

Compress a file.

```bash
gzip notes.txt
```

---

## Exercise 2

Decompress it.

```bash
gunzip notes.txt.gz
```

---

## Exercise 3

Create a project archive.

```bash
tar -czvf Project.tar.gz RNASeq_Project/
```

---

## Exercise 4

List archive contents.

```bash
tar -tvf Project.tar.gz
```

---

## Exercise 5

Extract the archive.

```bash
tar -xzvf Project.tar.gz
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Decompressing very large FASTQ files when you only need to inspect them. Use `zcat`, `zless`, or `zgrep` instead.
> - Assuming `.tar` files are compressed. A `.tar` file is only an archive; `.tar.gz` is compressed.
> - Trying to use `gunzip` on ZIP archives. Use `unzip` for `.zip` files.
> - Attempting to decompress BAM or CRAM files with `gunzip`; they use different formats.

---

# 🧠 Interview Corner

### ❓ Why are FASTQ files usually stored as `.fastq.gz`?

Because raw sequencing data is very large, and gzip compression significantly reduces storage space and transfer time.

---

### ❓ What is the difference between `.gz` and `.tar.gz`?

`.gz` compresses a single file, while `.tar.gz` archives multiple files into one package and then compresses it.

---

### ❓ How do you inspect a compressed FASTQ without decompressing it?

```bash
zcat sample.fastq.gz | head
```

---

### ❓ How do you search inside a compressed GTF file?

```bash
zgrep "BRCA1" annotation.gtf.gz
```

---

### ❓ Is a BAM file usually compressed?

Yes. BAM is the compressed binary version of a SAM file, while CRAM is an even more space-efficient reference-based compressed format.

---

# 📝 Lesson Summary

- Compression reduces file size.
- Archiving combines multiple files.
- Most NGS datasets are distributed as `.gz` files.
- `zcat`, `zless`, and `zgrep` allow you to work directly with compressed files.
- `tar` is commonly used to package complete bioinformatics projects.

---

# ⚡ Quick Revision

| Command | Purpose |
|---------|---------|
| `gzip file` | Compress |
| `gunzip file.gz` | Decompress |
| `gzip -k` | Keep original |
| `zcat file.gz` | View compressed file |
| `zless file.gz` | Browse compressed file |
| `zgrep pattern file.gz` | Search compressed file |
| `tar -cvf` | Create archive |
| `tar -czvf` | Archive + compress |
| `tar -xzvf` | Extract archive |
| `zip -r` | Create ZIP archive |
| `unzip` | Extract ZIP archive |

---

# 📚 References

- GNU Gzip Manual
- GNU Tar Manual
- Ubuntu Documentation
- Bioinformatics Data Skills (Book)

---

# ➡️ Next Lesson

**Downloading Data & Remote Transfer (`wget`, `curl`, `scp`, `rsync`)**
