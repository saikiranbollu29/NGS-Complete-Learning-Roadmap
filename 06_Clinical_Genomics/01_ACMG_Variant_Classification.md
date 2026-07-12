# 🏥 ACMG Variant Classification & Clinical Interpretation

> [!NOTE]
> **Module 5 • Lesson 1**
>
> Learn how genetic variants are classified according to the ACMG/AMP guidelines. This lesson explains the evidence used for classification and how variants are interpreted in clinical genomics.

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
ACMG Classification   ← You are here
     │
     ▼
Clinical Report
     │
     ▼
Patient Management
```

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand ACMG guidelines.
- Learn the five ACMG variant classes.
- Understand evidence codes.
- Learn how variants are classified.
- Understand VUS.
- Interpret clinical reports.

---

# 📚 Prerequisites

- Human Genetics
- Variant Calling
- Variant Annotation
- ClinVar
- HGVS Nomenclature

---

# 💡 Why Do We Need ACMG Guidelines?

Imagine a patient has the following variant:

```
BRCA1

c.68_69delAG
```

Questions:

- Is it disease-causing?
- Is it harmless?
- Should surgery be recommended?
- Should family members be tested?

Without standardized guidelines,

different laboratories could report different conclusions.

The ACMG/AMP guidelines provide a standardized framework for interpreting germline variants.

---

# 📌 What is ACMG?

ACMG stands for

**American College of Medical Genetics and Genomics**

Together with the Association for Molecular Pathology (AMP), it published guidelines for interpreting germline sequence variants.

---

# 📌 Five ACMG Classes

| Class | Clinical Meaning |
|---------|------------------|
| Pathogenic | Disease-causing |
| Likely Pathogenic | Strong evidence for disease association, but not definitive |
| Variant of Uncertain Significance (VUS) | Insufficient evidence to classify as pathogenic or benign |
| Likely Benign | Strong evidence against disease association |
| Benign | Not disease-causing |

---

# 📌 Clinical Meaning

## Pathogenic

Strong evidence that the variant causes disease.

Example:

```
BRCA1

Pathogenic
```

Clinical management may be influenced by this result when interpreted alongside the patient's phenotype and medical history.

---

## Likely Pathogenic

More than 90% confidence of being disease-causing according to ACMG criteria.

Additional evidence may still emerge.

---

## Variant of Uncertain Significance (VUS)

The most misunderstood category.

It means:

```
We do not currently have enough evidence.
```

A VUS is **not** evidence that a variant causes disease, nor is it evidence that it is harmless.

Clinical decisions should generally not be based on a VUS alone.

---

## Likely Benign

Evidence suggests the variant is unlikely to cause disease.

---

## Benign

Evidence indicates the variant does not cause disease.

---

# 📌 ACMG Evidence Categories

Evidence is divided by strength.

Pathogenic evidence

| Code | Meaning |
|------|----------|
| PVS | Very Strong |
| PS | Strong |
| PM | Moderate |
| PP | Supporting |

Benign evidence

| Code | Meaning |
|------|----------|
| BA | Stand-alone |
| BS | Strong |
| BP | Supporting |

---

# 📌 Important Evidence Codes

## PVS1

Loss-of-function variant

Example

- Nonsense
- Frameshift
- Canonical splice-site variant

in a gene where loss of function is a known disease mechanism.

---

## PS1

Same amino acid change as a previously established pathogenic variant,

but produced by a different DNA change.

---

## PM2

Absent or extremely rare in population databases such as gnomAD.

---

## PP3

Multiple computational prediction tools support a damaging effect.

Examples:

- SIFT
- PolyPhen-2
- CADD
- REVEL

Computational evidence is supportive, not definitive.

---

## BA1

Allele frequency is too high in the general population for the variant to plausibly cause a rare Mendelian disease.

---

# 📌 Example Classification

Variant

```
BRCA1

c.68_69delAG
```

Evidence

```
PVS1

PM2

PP5
```

Possible Classification

```
Pathogenic
```

The final classification depends on evaluating all available evidence according to ACMG criteria.

---

# 📌 Evidence Sources

| Database | Information |
|-----------|-------------|
| ClinVar | Clinical assertions |
| gnomAD | Population frequency |
| OMIM | Gene-disease relationships |
| PubMed | Scientific literature |
| HGMD* | Published disease variants (*subscription required) |
| GeneReviews | Expert clinical summaries |

---

# 📌 How is a Variant Evaluated?

```text
VCF

↓

Annotation

↓

Population Frequency

↓

Disease Database

↓

Literature Review

↓

Inheritance Pattern

↓

Functional Studies

↓

ACMG Evidence

↓

Classification
```

---

# 📌 Reclassification

Variant classifications are **not permanent**.

As new evidence becomes available:

- VUS → Likely Pathogenic
- Likely Pathogenic → Pathogenic
- VUS → Likely Benign

Laboratories periodically review important variants.

---

# 📌 Clinical Example

Patient

```
Early-onset breast cancer
```

Variant

```
BRCA1

Frameshift
```

Evidence

- Rare in gnomAD
- Previously reported in ClinVar
- Loss-of-function mechanism
- Consistent patient phenotype

Possible Outcome

```
Pathogenic
```

---

# 📌 VUS Example

Variant

```
Novel missense variant
```

Evidence

- Rare
- No functional studies
- Not reported in ClinVar
- Computational predictions are conflicting

Classification

```
VUS
```

---

# 📊 ACMG Decision Tree

```text
Variant

↓

Collect Evidence

↓

Pathogenic?

↓

Yes

↓

Report

↓

No

↓

Enough Evidence?

↓

No

↓

VUS

↓

More Evidence Later

↓

Possible Reclassification
```

---

# 🧬 Clinical Workflow

```text
Patient

↓

Sequencing

↓

Variant Calling

↓

Annotation

↓

ACMG Classification

↓

Genetic Counselor / Clinical Geneticist Review

↓

Clinical Report
```

---

# 🤖 Practical Workflow

```bash
VCF

↓

VEP

↓

ClinVar Annotation

↓

gnomAD Annotation

↓

Review Evidence

↓

Apply ACMG Criteria

↓

Generate Clinical Interpretation
```

---

# 🧠 Interview Questions

### ❓ What are the five ACMG variant classes?

- Pathogenic
- Likely Pathogenic
- Variant of Uncertain Significance (VUS)
- Likely Benign
- Benign

---

### ❓ What is a VUS?

A variant with insufficient evidence to classify as either pathogenic or benign.

---

### ❓ Can a VUS become pathogenic?

Yes.

As new evidence becomes available, variants may be reclassified.

---

### ❓ What is PVS1?

Very strong pathogenic evidence for predicted loss-of-function variants in genes where loss of function is a known disease mechanism.

---

### ❓ Is a rare variant always pathogenic?

No.

Rarity alone is not sufficient. Clinical interpretation integrates population frequency, functional evidence, phenotype, inheritance, segregation, literature, and other evidence.

---

### ❓ What is the purpose of ACMG guidelines?

To provide a standardized framework for consistent and evidence-based interpretation of germline genetic variants.

---

# 📝 Lesson Summary

- ACMG/AMP guidelines standardize germline variant interpretation.
- Variants are classified into five categories.
- Multiple evidence types are combined for classification.
- VUS indicates insufficient evidence, not a diagnosis.
- Variant classifications can change as new evidence becomes available.

---

# ⚡ Quick Revision

| Category | Meaning |
|----------|----------|
| Pathogenic | Disease-causing |
| Likely Pathogenic | Strong evidence |
| VUS | Uncertain |
| Likely Benign | Probably harmless |
| Benign | Harmless |

---

# 📚 References

- Richards et al. (2015). Standards and Guidelines for the Interpretation of Sequence Variants (ACMG/AMP).
- ClinGen Variant Curation Expert Panels
- ClinVar
- gnomAD
- GeneReviews

---

# ➡️ Next Lesson

**ClinVar, gnomAD & COSMIC – Understanding Clinical Variant Databases**
