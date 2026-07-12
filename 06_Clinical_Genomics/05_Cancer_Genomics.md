# 🧬 Cancer Genomics

> [!NOTE]
> **Module 5 • Lesson 5**
>
> Learn the molecular basis of cancer, the role of driver and passenger mutations, tumor evolution, precision oncology, and how NGS is used in cancer diagnosis and treatment.

---

# 🧬 Pipeline Position

```text
Patient

↓

Tumor Sample

↓

DNA/RNA Extraction

↓

NGS

↓

Variant Calling

↓

Annotation

↓

Cancer Genomics ← You are here

↓

Precision Medicine

↓

Targeted Therapy
```

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand cancer genomics.
- Differentiate driver and passenger mutations.
- Learn oncogenes and tumor suppressor genes.
- Understand tumor heterogeneity.
- Learn clonal evolution.
- Understand precision oncology.

---

# 📚 Prerequisites

- Germline vs Somatic Variants
- Variant Annotation
- ACMG Classification

---

# 💡 What is Cancer Genomics?

Cancer genomics is the study of genetic changes that contribute to the development, progression, and treatment response of cancer.

These changes may include:

- Single nucleotide variants (SNVs)
- Insertions and deletions (Indels)
- Copy number variations (CNVs)
- Structural variants (SVs)
- Gene fusions
- Chromosomal rearrangements

---

# 📌 Normal Cell vs Cancer Cell

Normal Cell

```
Controlled growth

↓

DNA repair

↓

Programmed cell death (Apoptosis)

↓

Stable genome
```

Cancer Cell

```
Uncontrolled growth

↓

DNA damage accumulation

↓

Avoids apoptosis

↓

Genomic instability
```

---

# 📌 What is a Driver Mutation?

A driver mutation provides a growth or survival advantage to the cell and contributes to cancer development.

Characteristics:

- Promotes tumor growth
- Positively selected during tumor evolution
- Often occurs in important cancer genes

Examples:

- EGFR
- KRAS
- BRAF
- TP53
- PIK3CA

---

# 📌 What is a Passenger Mutation?

Passenger mutations occur during tumor development but do not directly contribute to cancer progression.

Characteristics:

- Biologically neutral
- Do not provide selective advantage
- Often numerous in tumor genomes

---

# 📊 Driver vs Passenger

| Feature | Driver | Passenger |
|----------|---------|-----------|
| Contributes to cancer | ✅ Yes | ❌ No |
| Selected during evolution | ✅ Yes | ❌ No |
| Clinical importance | High | Usually low |
| Target for therapy | Often | Rarely |

---

# 📌 Oncogenes

An oncogene is a gene that promotes cell growth when activated by specific mutations or other genomic alterations.

Examples:

| Gene | Common Cancer |
|------|----------------|
| EGFR | Lung cancer |
| KRAS | Colorectal, pancreatic |
| BRAF | Melanoma |
| HER2 (ERBB2) | Breast cancer |
| ALK | Lung cancer |

Oncogenes typically require activation of one allele (gain-of-function).

---

# 📌 Tumor Suppressor Genes

Tumor suppressor genes normally prevent uncontrolled cell growth.

Loss or inactivation can contribute to cancer.

Examples:

| Gene | Function |
|------|----------|
| TP53 | DNA damage response |
| BRCA1 | DNA repair |
| BRCA2 | DNA repair |
| RB1 | Cell cycle regulation |
| PTEN | Cell signaling regulation |

Tumor suppressor genes often require loss of function of both alleles, although mechanisms can vary.

---

# 📌 Hallmarks of Cancer

Common biological capabilities include:

- Sustained proliferative signaling
- Evading growth suppressors
- Resisting cell death
- Enabling replicative immortality
- Inducing angiogenesis
- Activating invasion and metastasis
- Avoiding immune destruction
- Genome instability

---

# 📌 Tumor Heterogeneity

Not all cancer cells within the same tumor are genetically identical.

Example

```
Tumor

↓

Clone A

↓

TP53 mutation

Clone B

↓

TP53 + KRAS mutation

Clone C

↓

TP53 + KRAS + PIK3CA mutation
```

Different subclones may respond differently to treatment.

---

# 📌 Clonal Evolution

Cancer evolves over time through the accumulation of additional mutations.

```
Normal Cell

↓

Driver Mutation

↓

Clone 1

↓

New Mutation

↓

Clone 2

↓

Additional Mutation

↓

Clone 3
```

This process contributes to tumor progression and drug resistance.

---

# 📌 Precision Oncology

Precision oncology aims to tailor cancer treatment based on the molecular characteristics of a patient's tumor.

Example:

```
Tumor

↓

NGS

↓

EGFR Mutation

↓

EGFR-targeted therapy may be considered
```

Treatment decisions depend on clinical evaluation, regulatory approvals, and current evidence.

---

# 📌 Biomarkers

Common genomic biomarkers include:

| Biomarker | Clinical Relevance |
|-----------|--------------------|
| EGFR | Targeted therapy selection in certain lung cancers |
| BRAF V600E | Targeted therapy in multiple tumor types |
| ALK Fusion | ALK inhibitor eligibility in selected cancers |
| HER2 Amplification | HER2-targeted therapies |
| MSI-High | May predict response to some immunotherapies |
| TMB | Investigational/approved biomarker in selected settings |

---

# 📌 NGS in Cancer

Applications:

- Tumor mutation profiling
- Gene fusion detection
- Copy number analysis
- Minimal residual disease (MRD) research
- Liquid biopsy
- Therapy selection
- Clinical trial matching

---

# 📌 Bioinformatics Pipeline

```text
Tumor Sample

↓

DNA Extraction

↓

Library Preparation

↓

Sequencing

↓

FASTQ

↓

FastQC

↓

Alignment

↓

Somatic Variant Calling

↓

Annotation

↓

Cancer Databases

↓

Clinical Interpretation
```

---

# 📌 Common Bioinformatics Tools

| Step | Common Tools |
|------|--------------|
| QC | FastQC, MultiQC |
| Trimming | Fastp |
| Alignment | BWA |
| BAM Processing | Samtools |
| Somatic Variant Calling | Mutect2, Strelka2 |
| Annotation | VEP, ANNOVAR, SnpEff |
| Cancer Databases | COSMIC, CIViC, OncoKB |

---

# 🧪 Clinical Case Study

### Patient

```
62-year-old male

Lung adenocarcinoma
```

NGS Result

```
EGFR L858R
```

Questions

1. Is this germline or somatic?
2. Is EGFR an oncogene or tumor suppressor gene?
3. Which database would you search first?
4. Could this finding influence treatment planning?

Discuss each question using available molecular and clinical evidence.

---

# 🧠 Interview Questions

### ❓ What is a driver mutation?

A mutation that contributes to cancer development by providing a growth or survival advantage.

---

### ❓ What is a passenger mutation?

A mutation that accumulates during tumor evolution but does not directly contribute to cancer progression.

---

### ❓ What is an oncogene?

A gene that can promote cancer when activated or overexpressed.

---

### ❓ What is a tumor suppressor gene?

A gene that normally limits cell growth or maintains genomic stability. Loss of function can contribute to cancer.

---

### ❓ What is tumor heterogeneity?

The presence of genetically distinct populations of cancer cells within the same tumor.

---

### ❓ What is precision oncology?

An approach that uses molecular characteristics of a patient's tumor to help guide diagnosis, prognosis, and treatment decisions.

---

# 📝 Lesson Summary

- Cancer results from accumulated genetic alterations.
- Driver mutations promote tumor development, while passenger mutations generally do not.
- Oncogenes and tumor suppressor genes play central roles in cancer biology.
- Tumors evolve through clonal evolution and exhibit heterogeneity.
- NGS is a key technology for precision oncology.

---

# ⚡ Quick Revision

| Concept | Key Point |
|----------|-----------|
| Driver Mutation | Promotes cancer |
| Passenger Mutation | Usually neutral |
| Oncogene | Activated growth-promoting gene |
| Tumor Suppressor | Growth-inhibiting gene |
| Heterogeneity | Different tumor cell populations |
| Precision Oncology | Molecularly guided cancer care |

---

# 📚 Landmark Research Papers

- Hanahan D, Weinberg RA. *Hallmarks of Cancer: The Next Generation*.
- Vogelstein B et al. *Cancer Genome Landscapes*.
- The Cancer Genome Atlas (TCGA) publications.
- International Cancer Genome Consortium (ICGC) publications.

---

# 📚 References

- COSMIC Documentation
- CIViC Knowledgebase
- OncoKB
- TCGA
- NCI Cancer Genomics
- AACR Precision Medicine Resources

---

# ➡️ Next Lesson

**Pharmacogenomics – How Genetic Variants Influence Drug Response**
