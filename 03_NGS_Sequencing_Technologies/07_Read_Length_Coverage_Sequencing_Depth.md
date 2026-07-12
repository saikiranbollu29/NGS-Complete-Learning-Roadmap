# 📊 Read Length, Coverage & Sequencing Depth

> [!NOTE]
> **Module 2.5 • Lesson 7**
>
> Learn the fundamental sequencing metrics used to evaluate Next-Generation Sequencing (NGS) experiments.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Explain Read Length.
- Explain Coverage.
- Explain Sequencing Depth.
- Calculate sequencing coverage.
- Differentiate depth and breadth of coverage.
- Answer interview questions confidently.

---

# 📚 Prerequisites

Before starting this lesson, you should know:

- DNA Structure
- NGS Basics
- Single-End and Paired-End Sequencing

---

# 💡 Real-Life Analogy

Imagine painting a wall.

### Read Length

The size of your paint roller.

Longer roller → Covers more area in one stroke.

---

### Coverage

How much of the wall gets painted.

---

### Sequencing Depth

How many times you paint the same spot.

One coat

↓

Two coats

↓

Thirty coats

Higher depth = More confidence.

---

# 📌 What is Read Length?

Read Length is the number of nucleotides sequenced in a single read.

Example

```
ATCGTACGATCGATCG

Length = 16 bp
```

Modern sequencing platforms generate different read lengths.

---

# 📊 Common Read Lengths

| Platform | Typical Read Length |
|----------|---------------------|
| Illumina MiSeq | 2 × 300 bp |
| Illumina NovaSeq | 2 × 150 bp |
| Oxford Nanopore | 10 kb to >100 kb |
| PacBio HiFi | 10–25 kb (typical HiFi reads) |

---

# 📌 What is Coverage?

Coverage (also called **Breadth of Coverage**) is the percentage of the reference genome that has been sequenced at least once.

Example

Genome Size

```
1000 bp
```

Reads Cover

```
950 bp
```

Coverage

```
95%
```

---

# 📌 What is Sequencing Depth?

Sequencing Depth (also called **Depth of Coverage**) indicates how many times a particular base has been sequenced.

Example

```
Position 100

↓

Read 1

↓

Read 2

↓

Read 3

↓

Read 4

↓

Read 5
```

Depth

```
5×

```

---

# 📊 Coverage vs Depth

| Feature | Coverage | Depth |
|----------|----------|-------|
| Meaning | Portion of genome covered | Number of reads covering a base |
| Unit | Percentage (%) | X (10×, 30×, 100×) |
| Example | 98% | 30× |

---

# 📌 Formula for Sequencing Depth

```text
Depth (X)

=

(Total Number of Bases Sequenced)

/

Genome Size
```

Or

```text
Depth (X)

=

(Number of Reads × Read Length)

/

Genome Size
```

---

# 🧮 Example Calculation

Genome Size

```
3,000,000,000 bp
```

Reads

```
600,000,000
```

Read Length

```
150 bp
```

Total Bases

```
600,000,000 × 150

=

90,000,000,000 bp
```

Depth

```
90,000,000,000

/

3,000,000,000

=

30×

```

This is commonly referred to as **30× Whole Genome Sequencing**.

---

# 📊 Recommended Depth

| Application | Recommended Depth |
|-------------|------------------:|
| Whole Genome Sequencing | 30× |
| Whole Exome Sequencing | 80–150× |
| Targeted Panels | 500–1000× (often higher depending on the assay) |
| RNA-Seq | Depends on study goals (commonly discussed in terms of reads per sample rather than × coverage) |
| Single Cell RNA-Seq | Depends on cells and reads per cell |

> [!NOTE]
> RNA-Seq is usually planned by **number of reads per sample** (e.g., 20–50 million reads for many bulk gene expression studies), not by genome coverage.

---

# 📈 Depth Visualization

```text
Genome

A T G C G A T C G

Read1
A T G C G A T C G

Read2
A T G C G A T C G

Read3
A T G C G A T C G

Depth = 3×
```

---

# 📊 Why Higher Depth Matters

Higher sequencing depth:

- Improves variant detection.
- Reduces false positives.
- Increases confidence in results.
- Detects low-frequency variants.
- Improves accuracy.

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Confusing coverage with sequencing depth.
> - Assuming 100% coverage means every base has high depth.
> - Ignoring duplicate reads when estimating usable depth.

---

# 🧠 Interview Corner

### ❓ What is Read Length?

The number of nucleotides sequenced in a single sequencing read.

---

### ❓ What is Coverage?

The percentage of the reference genome that has been sequenced at least once.

---

### ❓ What is Sequencing Depth?

The average number of times each base is sequenced.

---

### ❓ Why is 30× commonly used for WGS?

Because it provides a good balance between sequencing cost and reliable germline variant detection for many applications.

---

### ❓ Which is more important: Coverage or Depth?

Both are important.

- Coverage tells **how much of the genome** is represented.
- Depth tells **how confidently each base** is supported.

---

# 📝 Lesson Summary

- Read Length = Number of bases in one read.
- Coverage = Percentage of the genome sequenced.
- Sequencing Depth = Number of times each base is read.
- WGS commonly uses ~30× depth.
- WES and targeted sequencing generally require higher depths because they focus on smaller genomic regions.

---

# ⚡ Quick Revision

| Question | Answer |
|----------|--------|
| Read Length? | Bases in one sequencing read |
| Coverage? | Percentage of genome covered |
| Depth? | Number of reads covering a base |
| WGS Depth? | ~30× |
| WES Depth? | Typically 80–150× |
| Targeted Panels? | Often 500× or higher |

---

# 📚 References

- Illumina Sequencing Coverage Guide
- NHGRI Genome Sequencing Resources
- Nature Reviews Genetics

---

# ➡️ Next Lesson

**Multiplexing, Indexing & Barcoding**
