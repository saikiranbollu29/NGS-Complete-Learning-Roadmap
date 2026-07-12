# 🗂 ClinVar, gnomAD & COSMIC

> [!NOTE]
> **Module 5 • Lesson 2**
>
> Learn how clinical and population databases are used to interpret genetic variants. These databases provide evidence for disease association, population frequency, and cancer relevance.

---

# 🧬 Pipeline Position

```text
FASTQ
   │
   ▼
Variant Calling
   │
   ▼
Variant Annotation
   │
   ▼
Database Search ← You are here
   │
   ▼
ACMG Classification
   │
   ▼
Clinical Report
```

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand the purpose of major genomic databases.
- Learn the difference between ClinVar, gnomAD, COSMIC, dbSNP and OMIM.
- Interpret population frequency.
- Understand clinical assertions.
- Use databases together during variant interpretation.

---

# 📚 Prerequisites

- Variant Annotation
- ACMG Classification
- Human Genetics

---

# 💡 Why Are Databases Needed?

Suppose we identify this variant:

```
BRCA1

c.68_69delAG
```

Questions immediately arise:

- Has this variant been reported before?
- Does it occur in healthy people?
- Has it been seen in cancer?
- What disease is associated with it?

Genomic databases help answer these questions.

---

# 📌 Major Variant Databases

| Database | Main Purpose |
|-----------|--------------|
| ClinVar | Clinical significance |
| gnomAD | Population allele frequency |
| COSMIC | Somatic cancer variants |
| dbSNP | Known genetic variants |
| OMIM | Gene-disease relationships |
| HGNC | Official gene names |
| Ensembl | Gene and transcript annotation |

---

# 📌 ClinVar

Developed by

```
NCBI
```

Purpose

Collects clinical interpretations of human genetic variants submitted by diagnostic laboratories and researchers.

Example

```
Variant

BRCA1 c.68_69delAG

Clinical Significance

Pathogenic
```

---

## ClinVar Classifications

| Classification |
|----------------|
| Pathogenic |
| Likely Pathogenic |
| VUS |
| Likely Benign |
| Benign |
| Conflicting Interpretations |

---

## ClinVar Review Status

Different variants have different levels of evidence.

Examples

```
Practice Guideline

★★★★★
```

```
Expert Panel

★★★★
```

```
Multiple Submitters

★★★
```

```
Single Submitter

★★
```

```
No Assertion Criteria

★
```

Variants with stronger review status generally have more reliable interpretations.

---

# 📌 gnomAD

Purpose

Population allele frequency database.

Contains sequencing data from large numbers of individuals.

Used to determine whether a variant is common or rare.

Example

```
Allele Frequency

0.45
```

Common variant

↓

Likely benign for most rare Mendelian disorders.

---

Example

```
Allele Frequency

0.00001
```

Rare variant

↓

May warrant further evaluation.

Population frequency alone does not determine pathogenicity.

---

# 📌 COSMIC

Purpose

Catalogue of Somatic Mutations in Cancer.

Contains:

- Cancer-associated mutations
- Tumor types
- Mutation frequencies
- Literature references

Example

```
TP53

p.R175H
```

Observed in multiple cancer types.

COSMIC is primarily used for **somatic (tumor) variants**, not inherited germline variants.

---

# 📌 dbSNP

Purpose

Repository of known genetic variants.

Example

```
rs121913529
```

dbSNP indicates that a variant has been observed before, but it does **not** determine whether it is pathogenic.

---

# 📌 OMIM

Purpose

Online Mendelian Inheritance in Man.

Provides information about:

- Genetic diseases
- Gene function
- Inheritance patterns
- Phenotypes

Example

```
Gene

CFTR

Disease

Cystic Fibrosis
```

---

# 📌 Comparing Databases

| Database | Answers This Question |
|----------|------------------------|
| ClinVar | Is the variant clinically significant? |
| gnomAD | How common is it in the population? |
| COSMIC | Has it been observed in cancer? |
| dbSNP | Has it been reported before? |
| OMIM | Which disease is associated with this gene? |

---

# 📌 Example Workflow

Variant

```
BRCA1 c.68_69delAG
```

↓

Search ClinVar

```
Pathogenic
```

↓

Search gnomAD

```
Very Rare
```

↓

Search OMIM

```
Hereditary Breast and Ovarian Cancer Syndrome
```

↓

Apply ACMG Criteria

↓

Clinical Interpretation

---

# 📌 Population Frequency Example

| AF | Interpretation |
|----|---------------|
| 0.40 | Common |
| 0.05 | Relatively common |
| 0.001 | Rare |
| 0.00001 | Very rare |

Remember:

A common variant is less likely to cause a rare Mendelian disorder, but frequency should always be interpreted in the context of the disease, ancestry, and other evidence.

---

# 📌 Germline vs Somatic Databases

| Germline | Somatic |
|-----------|----------|
| ClinVar | COSMIC |
| gnomAD | TCGA (research) |
| OMIM | Cancer-specific resources |

---

# 📊 Clinical Interpretation Example

Variant

```
TP53 p.R175H
```

Check

```
ClinVar

↓

Pathogenic
```

Check

```
COSMIC

↓

Frequently observed in tumors
```

Check

```
gnomAD

↓

Very rare
```

Interpretation

The combined evidence supports further clinical evaluation, but the final interpretation depends on the clinical context and whether the variant is germline or somatic.

---

# 🧬 Clinical Workflow

```text
VCF

↓

Variant Annotation

↓

ClinVar

↓

gnomAD

↓

OMIM

↓

COSMIC (if cancer)

↓

ACMG Classification

↓

Clinical Report
```

---

# 🤖 Practical Workflow

```text
VCF

↓

VEP

↓

ClinVar Annotation

↓

gnomAD Annotation

↓

Literature Review

↓

ACMG Evidence

↓

Clinical Interpretation
```

---

# 🧪 Clinical Case Study

### Patient

```
40-year-old woman

Early-onset breast cancer
```

Detected Variant

```
BRCA1

c.68_69delAG
```

Questions

1. Which database would you use to determine if this variant has already been clinically classified?

2. Which database would you use to check population frequency?

3. Which database would you consult to understand the associated inherited syndrome?

4. Would you also check COSMIC? Why or why not?

Think through these questions before reading the literature or making an ACMG assessment.

---

# 🧠 Interview Questions

### ❓ What is ClinVar?

A public database that stores clinical interpretations of human genetic variants.

---

### ❓ What is gnomAD?

A population genetics database that provides allele frequencies from large-scale sequencing datasets.

---

### ❓ Why is gnomAD important?

Because variants that are common in the general population are less likely to be responsible for rare Mendelian diseases.

---

### ❓ What is COSMIC?

A database of somatic mutations identified in human cancers.

---

### ❓ Does dbSNP indicate that a variant is pathogenic?

No.

It only indicates that the variant has been observed and catalogued.

---

### ❓ Can ClinVar entries disagree?

Yes.

Different submitters may provide different interpretations, which is why review status and supporting evidence are important.

---

# 📝 Lesson Summary

- ClinVar provides clinical interpretations.
- gnomAD provides population allele frequencies.
- COSMIC focuses on somatic cancer variants.
- dbSNP catalogs known variants.
- OMIM links genes with inherited diseases.
- Clinical interpretation integrates evidence from multiple databases rather than relying on a single source.

---

# ⚡ Quick Revision

| Database | Main Use |
|----------|----------|
| ClinVar | Clinical significance |
| gnomAD | Population frequency |
| COSMIC | Cancer mutations |
| dbSNP | Known variants |
| OMIM | Gene-disease associations |

---

# 📚 References

- ClinVar Documentation
- gnomAD Documentation
- COSMIC Documentation
- OMIM
- NCBI dbSNP
- ACMG/AMP Variant Interpretation Guidelines

---

# ➡️ Next Lesson

**HGVS Nomenclature – Understanding Genetic Variant Naming (DNA, RNA & Protein)**
