# 🧬 Germline vs Somatic Variants

> [!NOTE]
> **Module 5 • Lesson 4**
>
> Learn the difference between germline and somatic variants, their biological origins, sequencing strategies, clinical significance, and interpretation.

---

# 🧬 Pipeline Position

```text
DNA Sample
      │
      ▼
Sequencing
      │
      ▼
Variant Calling
      │
      ▼
Variant Annotation
      │
      ▼
Germline / Somatic Classification ← You are here
      │
      ▼
Clinical Interpretation
```

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand germline variants.
- Understand somatic variants.
- Compare inherited and acquired mutations.
- Select appropriate sequencing approaches.
- Choose relevant databases.
- Understand their clinical applications.

---

# 📚 Prerequisites

- Human Genetics
- Variant Calling
- ACMG Classification
- HGVS Nomenclature

---

# 💡 Why Is This Important?

Suppose two patients both have a BRCA1 variant.

Patient A

Inherited the variant from a parent.

Patient B

Developed the variant only in tumor cells.

Although the gene is the same,

the biological origin and clinical interpretation are different.

---

# 📌 What is a Germline Variant?

A germline variant is present in:

- Egg or sperm cells
- Fertilized embryo
- Every cell of the body

These variants can be passed from parents to children.

---

## Germline Characteristics

- Present from birth
- Inherited
- Found in blood, saliva, skin and most normal tissues
- Can be transmitted to offspring

---

# 📌 Germline Example

```
BRCA1 Pathogenic Variant

↓

Inherited

↓

Higher lifetime risk of hereditary breast and ovarian cancer
```

---

# 📌 What is a Somatic Variant?

A somatic variant develops after fertilization.

It occurs in specific body cells during life.

These variants are **not inherited** and are generally **not passed to children**.

---

## Somatic Characteristics

- Acquired during life
- Usually restricted to affected tissue
- Common in cancers
- Not present in all body cells

---

# 📌 Somatic Example

```
TP53 Mutation

↓

Occurs in tumor cells

↓

Cancer progression
```

---

# 📊 Germline vs Somatic

| Feature | Germline | Somatic |
|----------|-----------|----------|
| Inherited | ✅ Yes | ❌ No |
| Present at Birth | ✅ Yes | ❌ Usually develops later |
| Found in All Cells | ✅ Yes | ❌ No |
| Passed to Children | ✅ Yes | ❌ Generally No |
| Common Application | Inherited disease testing | Cancer genomics |

---

# 📌 Sample Types

## Germline Testing

Typical samples

- Blood
- Saliva
- Buccal swab

---

## Somatic Testing

Typical samples

- Tumor biopsy
- FFPE tissue
- Fresh tumor tissue

Many cancer studies also sequence a matched normal sample (such as blood) to distinguish inherited variants from tumor-specific variants.

---

# 📌 Sequencing Strategies

| Study | Germline | Somatic |
|--------|-----------|----------|
| WGS | ✅ | ✅ |
| WES | ✅ | ✅ |
| Targeted Panel | ✅ | ✅ |
| RNA-Seq | Sometimes | Frequently in cancer research |
| Tumor-Normal Pair | ❌ | ✅ Common |

---

# 📌 Databases

## Germline

- ClinVar
- gnomAD
- OMIM
- GeneReviews

---

## Somatic

- COSMIC
- CIViC
- OncoKB
- TCGA (research resource)

---

# 📌 Variant Calling

## Germline

Common tools

- GATK HaplotypeCaller
- DeepVariant
- BCFtools

---

## Somatic

Common tools

- GATK Mutect2
- Strelka2
- VarScan2
- FreeBayes (selected use cases)

---

# 📌 Allele Frequency

## Germline

Heterozygous variants are often observed around **50% Variant Allele Frequency (VAF)**.

Homozygous variants are often close to **100% VAF**.

---

## Somatic

VAF varies widely because it depends on:

- Tumor purity
- Tumor heterogeneity
- Copy number changes
- Clonal evolution

---

# 📌 Clinical Examples

## Germline

```
Gene

BRCA1

↓

Hereditary Breast Cancer

↓

Family Screening
```

---

## Somatic

```
Gene

EGFR

↓

Lung Cancer

↓

Targeted Therapy
```

---

# 📌 Clinical Workflow

## Germline

```text
Blood Sample

↓

Sequencing

↓

Variant Calling

↓

Annotation

↓

ACMG Classification

↓

Genetic Counseling
```

---

## Somatic

```text
Tumor Tissue

↓

Sequencing

↓

Tumor-Normal Comparison

↓

Somatic Variant Calling

↓

Cancer Databases

↓

Precision Oncology Report
```

---

# 📌 Germline and Somatic Together

Some genes can contain both inherited and acquired variants.

Example

```
BRCA1

↓

Inherited Variant

↓

Hereditary Cancer Risk
```

and

```
BRCA1

↓

Tumor-Acquired Variant

↓

Tumor Biology
```

The interpretation depends on the biological origin of the variant.

---

# 🧬 Clinical Case Study

### Patient A

```
26-year-old woman

Strong family history of breast cancer
```

Sample

```
Blood
```

Detected Variant

```
BRCA1 Pathogenic Variant
```

Interpretation

Suggests a hereditary cancer predisposition. Family history and genetic counseling are relevant.

---

### Patient B

```
65-year-old man

Lung Adenocarcinoma
```

Sample

```
Tumor Biopsy
```

Detected Variant

```
EGFR L858R
```

Interpretation

A somatic alteration that may help guide targeted therapy decisions, depending on clinical evaluation and treatment guidelines.

---

# 🧠 Interview Questions

### ❓ What is a germline variant?

A variant present from conception that is found in the germline and can be inherited.

---

### ❓ What is a somatic variant?

A variant acquired during life in body cells that is generally not inherited.

---

### ❓ Which sample is commonly used for germline testing?

Blood, saliva, or buccal swab.

---

### ❓ Which sample is commonly used for somatic testing?

Tumor tissue, often together with a matched normal sample.

---

### ❓ Which databases are commonly used for somatic variants?

COSMIC, CIViC, OncoKB, and other cancer-focused resources.

---

### ❓ Can the same gene contain both germline and somatic variants?

Yes. The same gene may harbor inherited variants in one patient and acquired variants in another.

---

# 📝 Lesson Summary

- Germline variants are inherited and present in all cells.
- Somatic variants are acquired during life and are usually restricted to specific tissues.
- Different samples, databases, and variant callers are used for germline and somatic analyses.
- Correctly distinguishing germline from somatic variants is essential for accurate clinical interpretation.

---

# ⚡ Quick Revision

| Feature | Germline | Somatic |
|----------|-----------|----------|
| Origin | Inherited | Acquired |
| Sample | Blood/Saliva | Tumor Tissue |
| Inherited | Yes | No |
| Main Databases | ClinVar, gnomAD | COSMIC, CIViC, OncoKB |
| Common Variant Caller | HaplotypeCaller | Mutect2 |

---

# 📚 References

- ACMG/AMP Variant Interpretation Guidelines
- GATK Best Practices (Germline & Somatic)
- ClinVar
- COSMIC
- CIViC
- OncoKB
- TCGA Publications

---

# ➡️ Next Lesson

**Cancer Genomics – Driver vs Passenger Mutations, Tumor Evolution & Precision Oncology**
