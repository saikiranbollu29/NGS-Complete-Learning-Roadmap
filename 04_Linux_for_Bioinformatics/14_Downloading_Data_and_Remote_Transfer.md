# 🌐 Downloading Data & Remote Transfer (wget, curl, scp, rsync)

> [!NOTE]
> **Module 3 • Lesson 14**
>
> Learn how to download genomic datasets from public databases, resume interrupted downloads, and transfer files securely between computers and remote servers.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Download files using `wget` and `curl`.
- Resume interrupted downloads.
- Download complete genomes and annotation files.
- Transfer files using `scp`.
- Synchronize data using `rsync`.
- Verify downloaded files.
- Understand best practices for handling large sequencing datasets.

---

# 📚 Prerequisites

- Linux Navigation
- Compression & Archiving
- Basic Terminal Commands

---

# 💡 Real-Life Analogy

Imagine ordering laboratory reagents.

You:

- Place an order.
- Download documentation.
- Send data to collaborators.
- Synchronize updates.

Linux performs similar tasks for sequencing data.

---

# 🧬 Bioinformatics Scenario

Suppose you need:

- Human reference genome
- Gene annotation
- FASTQ datasets
- Variant databases

Instead of downloading them manually from a browser,

Linux downloads everything automatically.

---

# 📌 Command 1 — wget

## Purpose

Download files from the internet.

---

## Syntax

```bash
wget URL
```

---

## Example

```bash
wget https://example.com/file.txt
```

---

## Resume Interrupted Download

Large sequencing downloads may stop due to network issues.

Resume with:

```bash
wget -c URL
```

`-c`

↓

Continue

---

## Save with Another Name

```bash
wget -O genome.fa.gz URL
```

---

## Download into a Specific Folder

```bash
wget -P reference URL
```

---

# 🧬 Example: Download Human Reference Genome

```bash
mkdir -p reference

cd reference

wget -c https://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_human/release_50/GRCh38.primary_assembly.genome.fa.gz
```

---

# 📌 Command 2 — curl

## Purpose

Transfer data to or from a server.

Unlike `wget`, `curl` can also send data (for APIs, uploads, etc.).

---

## Syntax

```bash
curl -O URL
```

---

## Example

```bash
curl -O https://example.com/file.txt
```

---

## Follow Redirects

```bash
curl -L -O URL
```

`-L`

↓

Follow redirects

---

# wget vs curl

| Feature | wget | curl |
|---------|------|------|
| Download files | ✅ | ✅ |
| Resume downloads | ✅ | Limited (depends on server) |
| Upload data | ❌ | ✅ |
| APIs | Limited | Excellent |
| Recursive downloads | ✅ | ❌ |

---

# 📌 Command 3 — scp

## Purpose

Securely copy files between computers.

Uses SSH.

---

## Syntax

```bash
scp source destination
```

---

## Upload File to HPC

```bash
scp sample.fastq.gz user@server:/data/
```

---

## Download from HPC

```bash
scp user@server:/data/results.vcf .
```

`.`

↓

Current directory

---

## Copy Folder

```bash
scp -r RNASeq_Project user@server:/projects/
```

---

# 📌 Command 4 — rsync

## Purpose

Synchronize files efficiently.

Only transfers changed portions of files.

Ideal for large sequencing datasets.

---

## Syntax

```bash
rsync options source destination
```

---

## Example

```bash
rsync -av RNASeq_Project/ backup/
```

---

## Upload to Server

```bash
rsync -av RNASeq_Project/ user@server:/projects/RNASeq_Project/
```

---

## Explanation

```
-a

Archive Mode

-v

Verbose
```

---

## Show Progress

```bash
rsync -av --progress RNASeq_Project/ user@server:/projects/
```

---

# 📌 Verify Downloaded Files

## Check File Size

```bash
ls -lh
```

---

## Check File Type

```bash
file genome.fa.gz
```

---

## Count Downloaded FASTQ Files

```bash
find raw_data -name "*.fastq.gz" | wc -l
```

---

# 📌 Verify File Integrity (Checksum)

Many repositories provide checksum files.

Generate an MD5 checksum:

```bash
md5sum genome.fa.gz
```

Generate a SHA-256 checksum:

```bash
sha256sum genome.fa.gz
```

Compare the output with the checksum provided by the data source.

---

# 🧬 NGS Workflow Connection

Create project folders.

```bash
mkdir -p RNASeq_Project/{raw_data,reference}
```

Download reference genome.

```bash
cd RNASeq_Project/reference

wget -c URL
```

Download FASTQ files.

```bash
cd ../raw_data

wget -c URL
```

Verify downloads.

```bash
ls -lh
```

---

# 📌 Common Public Genomics Resources

| Resource | Data Available |
|----------|----------------|
| NCBI SRA | Raw sequencing reads |
| ENA | Sequencing reads |
| Ensembl | Reference genomes |
| GENCODE | Gene annotations |
| UCSC | Genome assemblies |
| GDC | Cancer genomics |
| GEO | Gene expression datasets |

---

# 🧬 Real NGS Dataset Challenge

## Challenge 1

Create project directories.

```bash
mkdir -p WGS_Project/{raw_data,reference,results}
```

---

## Challenge 2

Download a genome.

```bash
wget -c URL
```

---

## Challenge 3

Resume an interrupted download.

```bash
wget -c URL
```

---

## Challenge 4

Verify file size.

```bash
ls -lh
```

---

## Challenge 5

Generate an MD5 checksum.

```bash
md5sum genome.fa.gz
```

---

## Challenge 6

Copy project to HPC.

```bash
scp -r WGS_Project user@server:/projects/
```

---

## Challenge 7

Synchronize project.

```bash
rsync -av --progress WGS_Project/ backup/
```

---

# 💪 Practice Exercises

## Exercise 1

Create a downloads folder.

```bash
mkdir downloads
```

---

## Exercise 2

Download a small practice file.

```bash
wget URL
```

---

## Exercise 3

Display file information.

```bash
file filename
```

---

## Exercise 4

Generate an MD5 checksum.

```bash
md5sum filename
```

---

## Exercise 5

Count downloaded FASTQ files.

```bash
find . -name "*.fastq.gz" | wc -l
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Restarting large downloads instead of resuming them with `wget -c`.
> - Skipping checksum verification after downloading reference genomes or sequencing data.
> - Using `scp` repeatedly for large projects when `rsync` is more efficient.
> - Forgetting the `-r` option when copying directories.

---

# 🧠 Interview Corner

### ❓ What is the difference between `wget` and `curl`?

- `wget` is mainly designed for downloading files.
- `curl` supports downloads, uploads, APIs, and more advanced network interactions.

---

### ❓ Why use `wget -c`?

It resumes interrupted downloads instead of starting again from the beginning.

---

### ❓ Why is `rsync` preferred over `scp` for large datasets?

Because `rsync` transfers only changed data, reducing transfer time and bandwidth usage.

---

### ❓ How do you verify that a downloaded genome file is intact?

Generate an MD5 or SHA-256 checksum and compare it with the checksum provided by the data source.

---

### ❓ Which command securely copies files between systems?

```bash
scp
```

---

# 📝 Lesson Summary

- `wget` downloads files and resumes interrupted transfers.
- `curl` supports downloads and advanced web requests.
- `scp` securely copies files between systems.
- `rsync` efficiently synchronizes large datasets.
- Always verify downloaded genomic files using checksums.

---

# ⚡ Quick Revision

| Command | Purpose |
|---------|---------|
| `wget URL` | Download file |
| `wget -c URL` | Resume download |
| `wget -O file URL` | Save with new name |
| `curl -O URL` | Download file |
| `curl -L -O URL` | Follow redirects |
| `scp file user@server:/path/` | Upload file |
| `scp user@server:/path/file .` | Download file |
| `rsync -av source dest` | Synchronize files |
| `md5sum file` | Generate MD5 checksum |
| `sha256sum file` | Generate SHA-256 checksum |

---

# 📚 References

- GNU Wget Manual
- cURL Documentation
- OpenSSH Documentation
- rsync Documentation
- NCBI SRA Documentation

---

# ➡️ Next Lesson

**Environment Variables, PATH & Software Installation (`PATH`, `export`, `source`)**
