# 💊 Pharmacogenomics

> [!NOTE]
> **Module 5 • Lesson 6**
>
> Learn how genetic variation influences drug metabolism, efficacy, toxicity, and personalized treatment decisions.

---

# 🧬 Pipeline Position

```text
Patient

↓

DNA Sequencing

↓

Variant Calling

↓

Variant Annotation

↓

Pharmacogenomic Analysis ← You are here

↓

Drug Selection

↓

Personalized Medicine
```

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand Pharmacogenomics.
- Learn why patients respond differently to drugs.
- Understand drug-metabolizing enzymes.
- Learn important pharmacogenes.
- Understand PharmGKB and CPIC.
- Interpret pharmacogenomic reports.

---

# 📚 Prerequisites

- Human Genetics
- Variant Annotation
- Clinical Genomics

---

# 💡 Why Pharmacogenomics?

Imagine two patients receive exactly the same drug at the same dose.

Patient A

```
Excellent response

No side effects
```

Patient B

```
Severe toxicity

Hospitalization
```

Why?

Sometimes the difference is explained by genetic variation affecting drug metabolism or drug targets.

---

# 📌 What is Pharmacogenomics?

Pharmacogenomics is the study of how inherited genetic variation influences an individual's response to medications.

Its goals include:

- Selecting appropriate drugs
- Optimizing dose
- Reducing adverse drug reactions
- Improving treatment outcomes

---

# 📌 Pharmacogenetics vs Pharmacogenomics

| Pharmacogenetics | Pharmacogenomics |
|------------------|------------------|
| Focuses on one or a few genes | Considers many genes or the whole genome |
| Traditional approach | Genome-wide approach |
| Example: CYP2D6 | Example: Whole PGx panel |

---

# 📌 Drug Response

Drug response depends on many factors:

- Genetics
- Age
- Liver function
- Kidney function
- Drug interactions
- Lifestyle
- Disease status

Genetics is one important contributor.

---

# 📌 Drug Metabolism

Many drugs are metabolized by liver enzymes.

```
Drug

↓

Liver Enzyme

↓

Active Drug

↓

Clinical Effect
```

If enzyme activity changes,

drug response may also change.

---

# 📌 Cytochrome P450 (CYP450)

The CYP450 family metabolizes many commonly prescribed drugs.

Important genes:

| Gene | Common Drugs |
|------|--------------|
| CYP2D6 | Codeine, Tamoxifen, Antidepressants |
| CYP2C19 | Clopidogrel, Proton Pump Inhibitors |
| CYP2C9 | Warfarin, Phenytoin |
| CYP3A5 | Tacrolimus |
| CYP2B6 | Efavirenz |

---

# 📌 Metabolizer Phenotypes

| Phenotype | Enzyme Activity |
|------------|-----------------|
| Poor Metabolizer (PM) | Very low |
| Intermediate Metabolizer (IM) | Reduced |
| Normal Metabolizer (NM) | Normal |
| Rapid Metabolizer (RM) | Increased |
| Ultrarapid Metabolizer (UM) | Very high |

These phenotypes are inferred from genotype using established guidelines.

---

# 📌 Example

Drug

```
Codeine
```

Gene

```
CYP2D6
```

Poor metabolizer

↓

Reduced conversion of codeine to morphine

↓

Reduced pain relief

Ultrarapid metabolizer

↓

Increased conversion to morphine

↓

Higher risk of toxicity

Clinical decisions should follow current prescribing guidelines.

---

# 📌 Important Pharmacogenes

| Gene | Clinical Relevance |
|------|--------------------|
| CYP2D6 | Drug metabolism |
| CYP2C19 | Drug metabolism |
| CYP2C9 | Drug metabolism |
| TPMT | Thiopurine toxicity risk |
| DPYD | Fluoropyrimidine toxicity risk |
| SLCO1B1 | Statin-associated muscle toxicity |
| VKORC1 | Warfarin sensitivity |
| HLA-B | Certain severe drug hypersensitivity reactions |

---

# 📌 PharmGKB

PharmGKB is a curated knowledgebase containing information about:

- Gene–drug relationships
- Clinical annotations
- Drug labels
- Variant annotations
- Dosing recommendations

It is widely used in pharmacogenomics research and clinical implementation.

---

# 📌 CPIC

CPIC

Clinical Pharmacogenetics Implementation Consortium

Provides peer-reviewed guidelines describing how genotype information can be used to inform prescribing when genetic test results are already available.

Examples:

- CYP2C19 – Clopidogrel
- CYP2D6 – Codeine
- TPMT – Azathioprine
- DPYD – Fluoropyrimidines

---

# 📌 Example Workflow

```text
Patient DNA

↓

NGS

↓

Variant Calling

↓

Annotation

↓

Pharmacogenes

↓

CPIC Guideline

↓

Drug Recommendation

↓

Clinical Decision
```

---

# 📌 Bioinformatics Workflow

```text
FASTQ

↓

Variant Calling

↓

VCF

↓

Annotation

↓

PharmGKB

↓

CPIC

↓

Clinical Report
```

---

# 📌 Example Pharmacogenomic Report

| Gene | Genotype | Phenotype | Drug |
|------|----------|-----------|------|
| CYP2D6 | *4/*4 | Poor Metabolizer | Codeine |
| CYP2C19 | *1/*17 | Rapid Metabolizer | Clopidogrel |
| TPMT | *1/*3A | Intermediate Metabolizer | Azathioprine |

The report summarizes genotype and predicted phenotype. Medication decisions should be made by qualified healthcare professionals using current guidelines and the patient's clinical context.

---

# 📌 Common Databases

| Database | Purpose |
|-----------|----------|
| PharmGKB | Gene-drug knowledge |
| CPIC | Clinical prescribing guidelines |
| PharmVar | Pharmacogene allele definitions |
| DrugBank | Drug information |
| FDA PGx Tables | Pharmacogenomic information in drug labeling |

---

# 🧪 Clinical Case Study

### Patient

```
52-year-old male

Requires antiplatelet therapy
```

Genetic Result

```
CYP2C19 Poor Metabolizer
```

Questions

1. Which gene is involved?

2. Which database would you consult for gene–drug information?

3. Which guideline resource would you use to review genotype-based prescribing recommendations?

4. Why might genotype be relevant when selecting therapy?

Discuss these questions using current pharmacogenomic guidelines rather than making assumptions.

---

# 🧠 Interview Questions

### ❓ What is Pharmacogenomics?

The study of how inherited genetic variation influences drug response.

---

### ❓ What is the difference between Pharmacogenetics and Pharmacogenomics?

Pharmacogenetics usually focuses on individual genes, while pharmacogenomics considers multiple genes or genome-wide effects.

---

### ❓ Name two important pharmacogenes.

- CYP2D6
- CYP2C19

---

### ❓ What is PharmGKB?

A curated knowledgebase of pharmacogenomic information, including gene–drug relationships and clinical annotations.

---

### ❓ What is CPIC?

An organization that publishes guidelines describing how to use existing genetic test results to inform drug prescribing.

---

### ❓ Why is pharmacogenomics important?

It can help optimize medication selection and dosing while reducing the risk of adverse drug reactions when integrated with clinical evaluation.

---

# 📝 Lesson Summary

- Pharmacogenomics studies how genetic variation influences drug response.
- Drug metabolism often depends on pharmacogenes such as CYP2D6 and CYP2C19.
- PharmGKB and CPIC are key pharmacogenomic resources.
- Genotype contributes to personalized medicine but is interpreted alongside clinical factors.
- Pharmacogenomics is increasingly integrated into precision medicine.

---

# ⚡ Quick Revision

| Topic | Key Point |
|--------|-----------|
| Pharmacogenomics | Genetics and drug response |
| CYP2D6 | Drug metabolism |
| CYP2C19 | Drug metabolism |
| PharmGKB | Gene–drug database |
| CPIC | Prescribing guidelines |
| Goal | Personalized medicine |

---

# 📚 References

- CPIC Guidelines
- PharmGKB
- PharmVar
- FDA Table of Pharmacogenetic Associations
- DrugBank
- Clinical Pharmacogenetics Implementation Consortium Publications

---

# ➡️ Next Lesson

**Clinical Genomics Report Interpretation – Reading, Understanding & Explaining NGS Clinical Reports**

---

# ✅ Commit Message

```text id="3r5v1n"
Add Module 5 Lesson 6: Pharmacogenomics
```

---

## 🌟 Repository Enhancement (Professional Level)

After completing **Module 5**, your repository will cover the full journey from **sequencing to clinical interpretation**.

For the next module, I recommend focusing on **real-world clinical reporting**, including:

- How to read an NGS clinical report
- Understanding report sections
- Variant interpretation workflow
- Quality metrics in clinical reports
- Incidental findings
- Reporting limitations
- Real anonymized case studies
- Common interview scenarios for Clinical Genomic Variant Analyst roles

This will make your repository highly relevant for both academic learning and industry interview preparation.
