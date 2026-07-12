# 🏥 Clinical Genomics Report Interpretation

> [!NOTE]
> **Module 5 • Lesson 7**
>
> Learn how to read, interpret, and explain clinical genomics reports generated from NGS data. This lesson covers report structure, variant interpretation, quality metrics, limitations, and clinical communication.

---

# 🧬 Pipeline Position

```text
Patient Sample

↓

NGS

↓

Variant Calling

↓

Annotation

↓

ACMG Classification

↓

Clinical Genomics Report ← You are here

↓

Clinical Decision
```

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Read an NGS clinical report.
- Understand each section of the report.
- Interpret variant information.
- Explain report findings.
- Recognize report limitations.
- Prepare for clinical genomics interviews.

---

# 📚 Prerequisites

- Variant Calling
- Variant Annotation
- ACMG Classification
- HGVS Nomenclature
- ClinVar
- Pharmacogenomics

---

# 💡 Why Clinical Reports Matter?

The laboratory performs sequencing.

Bioinformaticians analyze the data.

Variant analysts interpret the findings.

Clinicians use the final report to support patient care.

The report is the bridge between bioinformatics and clinical practice.

---

# 📌 Typical Clinical NGS Workflow

```text
Patient

↓

Blood / Tumor Sample

↓

DNA Extraction

↓

NGS

↓

FASTQ

↓

Alignment

↓

Variant Calling

↓

Annotation

↓

ACMG Classification

↓

Clinical Report
```

---

# 📌 Sections of an NGS Clinical Report

Most reports include:

- Patient Information
- Sample Information
- Test Details
- Sequencing Quality
- Variant Findings
- Interpretation
- Recommendations
- Limitations

---

# 📌 Patient Information

Example

```
Patient ID

Age

Sex

Clinical Indication

Ordering Physician
```

Patient identifiers should be handled according to privacy regulations.

---

# 📌 Sample Information

Example

```
Blood

Saliva

Tumor Tissue

FFPE

Collection Date
```

---

# 📌 Test Details

Example

```
Whole Exome Sequencing

Targeted Gene Panel

Whole Genome Sequencing
```

Reference genome

```
GRCh38
```

---

# 📌 Sequencing Quality Metrics

Common metrics include:

| Metric | Meaning |
|----------|----------|
| Mean Coverage | Average sequencing depth |
| % Bases ≥20× | Percentage of target bases with at least 20× coverage |
| Mapping Rate | Reads aligned to reference |
| Duplication Rate | Duplicate reads |
| Q30 | High-quality bases |

High-quality metrics increase confidence in the technical performance of the assay.

---

# 📌 Variant Findings

Example

| Gene | Variant | Zygosity | ACMG |
|------|----------|----------|-------|
| BRCA1 | c.68_69delAG | Heterozygous | Pathogenic |
| TP53 | c.524G>A | Heterozygous | VUS |

---

# 📌 Variant Interpretation

Each reported variant should include:

- Gene
- HGVS notation
- Variant consequence
- Zygosity
- ACMG classification
- Clinical significance
- Supporting evidence

---

# 📌 Example Interpretation

Variant

```
BRCA1

NM_007294.4:c.68_69delAG
```

Classification

```
Pathogenic
```

Evidence may include:

- ClinVar
- gnomAD
- Published literature
- Functional studies
- ACMG evidence codes

The final interpretation should always be considered in the context of the patient's phenotype and clinical history.

---

# 📌 Zygosity

| Type | Meaning |
|------|----------|
| Homozygous | Both copies carry the variant |
| Heterozygous | One copy carries the variant |
| Hemizygous | Single copy present (e.g., X chromosome in XY individuals) |
| Mosaic | Variant present in a subset of cells |

---

# 📌 Recommendations

Reports may include suggestions such as:

- Genetic counseling
- Family testing when appropriate
- Confirmatory testing (if indicated)
- Clinical follow-up
- Additional laboratory evaluation

Recommendations depend on laboratory policy, clinical guidelines, and physician judgment.

---

# 📌 Report Limitations

No genetic test detects every possible variant.

Common limitations include:

- Low coverage regions
- Structural variants not assessed (depending on the assay)
- Repeat expansions not detected
- Deep intronic variants may not be evaluated
- Low-level mosaicism may be missed

Always read the limitations section carefully.

---

# 📌 Incidental Findings

Occasionally, sequencing identifies variants unrelated to the original reason for testing.

Examples may include variants associated with inherited cancer syndromes or cardiac conditions.

Reporting practices follow laboratory policies, patient consent, and professional guidelines.

---

# 📌 Example Report Summary

```
Patient

↓

Whole Exome Sequencing

↓

BRCA1 Pathogenic Variant

↓

Associated with hereditary breast and ovarian cancer syndrome

↓

Recommendation:

Genetic counseling and clinical follow-up
```

This is an example for educational purposes. Real clinical recommendations depend on the patient's complete clinical context.

---

# 📊 Clinical Interpretation Workflow

```text
Variant

↓

Annotation

↓

Databases

↓

Literature

↓

ACMG

↓

Clinical Report

↓

Physician Review
```

---

# 📌 Quality Checklist

Before finalizing a report, review:

- Sample identity
- Sequencing quality
- Coverage
- Variant quality
- Annotation accuracy
- HGVS correctness
- ACMG classification
- Supporting evidence
- Report formatting

---

# 🧪 Clinical Case Study

### Patient

```
32-year-old female

Strong family history of breast cancer
```

Sequencing

```
Whole Exome Sequencing
```

Finding

```
BRCA1

NM_007294.4:c.68_69delAG
```

Questions

1. What is the gene?

2. What type of variant is reported?

3. Which databases would support interpretation?

4. What ACMG classification might apply?

5. Which additional healthcare professional is commonly involved after receiving this result?

Discuss these questions using the available evidence and clinical context.

---

# 🧠 Interview Questions

### ❓ What are the major sections of a clinical genomics report?

Patient information, sample details, test description, quality metrics, variant findings, interpretation, recommendations, and limitations.

---

### ❓ Why are sequencing quality metrics important?

They indicate whether the sequencing data are of sufficient quality to support reliable interpretation.

---

### ❓ Why should report limitations always be reviewed?

Because every testing method has technical limitations and some variants may not be detectable.

---

### ❓ What is the role of a Variant Analyst?

To review sequencing results, assess evidence, classify variants, and contribute to accurate and evidence-based interpretation.

---

### ❓ What is the difference between variant detection and clinical interpretation?

Variant detection identifies genetic changes, while clinical interpretation evaluates their biological and medical significance using guidelines, databases, and the patient's clinical information.

---

### ❓ Who makes the final clinical decision?

Clinical decisions are made by qualified healthcare professionals in collaboration with the patient, using the genetic report alongside clinical findings and other relevant information.

---

# 📝 Lesson Summary

- Clinical reports translate bioinformatics results into clinically meaningful information.
- Reports include quality metrics, variant findings, interpretation, recommendations, and limitations.
- ACMG guidelines, public databases, and clinical context are essential for interpretation.
- Understanding how to read a clinical report is a key skill for Clinical Genomic Variant Analysts.

---

# ⚡ Quick Revision

| Section | Purpose |
|----------|----------|
| Patient Information | Identify the case |
| Sample Details | Describe specimen |
| Test Details | Sequencing performed |
| Quality Metrics | Technical performance |
| Variant Findings | Genetic changes |
| Interpretation | Clinical significance |
| Recommendations | Suggested follow-up |
| Limitations | Technical constraints |

---

# 📚 References

- ACMG/AMP Variant Interpretation Guidelines
- ClinGen
- CAP Molecular Pathology Checklists
- ClinVar
- GeneReviews
- AMP Clinical Reporting Recommendations

---

# ➡️ Next Module

# **Module 6 – Advanced Genomics & Multi-Omics**

Topics include:

- Copy Number Variations (CNVs)
- Structural Variants (SVs)
- Gene Fusions
- Liquid Biopsy
- Single-Cell RNA-Seq
- Spatial Transcriptomics
- DNA Methylation
- Long-Read Sequencing
- AI in Genomics
- Multi-Omics Integration
