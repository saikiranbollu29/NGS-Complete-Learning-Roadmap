# 🧬 HGVS Nomenclature – Understanding Genetic Variant Naming

> [!NOTE]
> **Module 5 • Lesson 3**
>
> Learn how genetic variants are described using the Human Genome Variation Society (HGVS) nomenclature. This standardized language is used worldwide in research, clinical genomics, and diagnostic reports.

---

# 🧬 Pipeline Position

```text
DNA Sequencing
      │
      ▼
Variant Calling
      │
      ▼
Variant Annotation
      │
      ▼
HGVS Nomenclature ← You are here
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

- Understand HGVS nomenclature.
- Interpret DNA, RNA and protein variant names.
- Read clinical variant reports.
- Identify different mutation types.
- Convert simple variants into HGVS notation.

---

# 📚 Prerequisites

- Human Genetics
- Variant Calling
- Variant Annotation

---

# 💡 Why Do We Need HGVS?

Different laboratories could describe the same variant differently.

Example

```
17:43045702 G>A
```

or

```
BRCA1 mutation
```

These descriptions are incomplete.

HGVS provides one internationally accepted standard.

---

# 📌 What is HGVS?

HGVS stands for

**Human Genome Variation Society**

It publishes international guidelines for naming genetic variants consistently.

---

# 📌 HGVS Prefixes

| Prefix | Meaning |
|----------|----------|
| g. | Genomic DNA |
| c. | Coding DNA |
| n. | Non-coding DNA |
| r. | RNA |
| p. | Protein |
| m. | Mitochondrial DNA |

---

# 📌 Genomic Notation (g.)

Example

```
NC_000017.11:g.43045702G>A
```

Meaning

```
Chromosome 17

↓

Position 43045702

↓

Reference = G

↓

Alternate = A
```

---

# 📌 Coding DNA Notation (c.)

Example

```
NM_007294.4:c.68_69delAG
```

Meaning

```
Transcript

↓

Coding DNA

↓

Bases 68–69

↓

Deleted
```

---

# 📌 RNA Notation (r.)

Example

```
r.76a>g
```

Describes a change in the RNA sequence after transcription.

---

# 📌 Protein Notation (p.)

Example

```
p.Glu23Val
```

Meaning

```
Glutamic Acid

↓

Position 23

↓

Valine
```

---

# 📌 Standard Amino Acid Codes

| Three-letter | One-letter |
|--------------|------------|
| Ala | A |
| Arg | R |
| Asn | N |
| Asp | D |
| Cys | C |
| Gln | Q |
| Glu | E |
| Gly | G |
| His | H |
| Ile | I |
| Leu | L |
| Lys | K |
| Met | M |
| Phe | F |
| Pro | P |
| Ser | S |
| Thr | T |
| Trp | W |
| Tyr | Y |
| Val | V |

---

# 📌 Common HGVS Variant Types

## Substitution

```
c.76A>G
```

One nucleotide changes.

---

## Deletion

```
c.68_69del
```

DNA bases removed.

---

## Insertion

```
c.76_77insA
```

New base inserted.

---

## Duplication

```
c.5266dupC
```

One or more bases duplicated.

---

## Inversion

```
c.100_200inv
```

DNA segment reversed.

---

## Deletion-Insertion

```
c.100_105delinsTT
```

One sequence replaced by another.

---

# 📌 Protein Consequences

## Missense

```
p.Gly12Asp
```

One amino acid replaced.

---

## Nonsense

```
p.Arg97Ter
```

Creates a premature stop codon.

---

## Synonymous

```
p.Gly100=
```

DNA changes but amino acid remains unchanged.

---

## Frameshift

```
p.Gln1756ProfsTer74
```

Reading frame changes, often resulting in a premature stop codon downstream.

---

# 📌 Understanding a Complete HGVS Name

Example

```
NM_007294.4(BRCA1):c.68_69delAG
```

Breakdown

```
NM_007294.4

↓

Reference transcript

↓

BRCA1

↓

Gene

↓

c.

↓

Coding DNA

↓

68–69

↓

Deleted AG
```

---

# 📌 Clinical Example

Variant

```
NM_000546.6(TP53):c.524G>A

↓

Protein

p.Arg175His
```

Interpretation

```
TP53

↓

Codon 175

↓

Arginine replaced by Histidine
```

---

# 📌 HGVS vs VCF

VCF

```
chr17

43045702

G

A
```

HGVS

```
NM_007294.4(BRCA1):c.68_69delAG
```

VCF is optimized for computational analysis.

HGVS is optimized for human-readable clinical reporting.

---

# 📊 Mutation Summary

| HGVS Example | Mutation Type |
|--------------|---------------|
| c.76A>G | Substitution |
| c.68_69del | Deletion |
| c.76_77insA | Insertion |
| c.5266dupC | Duplication |
| c.100_200inv | Inversion |
| p.Arg97Ter | Nonsense |
| p.Gly12Asp | Missense |
| p.Gln1756ProfsTer74 | Frameshift |

---

# 🧬 Variant Interpretation Lab

Variant

```
NM_007294.4(BRCA1):c.68_69delAG
```

Questions

1. Which gene is affected?
2. What does **c.** represent?
3. What type of mutation is this?
4. What protein consequence might result?
5. Which databases would you search?
6. Which ACMG evidence codes could be relevant?

---

# 🧠 Interview Questions

### ❓ What is HGVS?

An international standard for naming genetic variants.

---

### ❓ What does **c.** mean?

Coding DNA sequence.

---

### ❓ What does **p.** represent?

Protein-level change.

---

### ❓ What is a frameshift mutation?

A mutation caused by insertion or deletion of nucleotides that changes the reading frame of the coding sequence.

---

### ❓ What is the difference between VCF and HGVS?

VCF stores genomic coordinates and alleles for computational analysis, while HGVS provides standardized descriptions of variants for reporting and interpretation.

---

### ❓ Why is HGVS important in clinical genomics?

It ensures consistent communication of genetic variants between laboratories, clinicians, researchers, and databases.

---

# 📝 Lesson Summary

- HGVS is the international standard for naming genetic variants.
- Different prefixes describe genomic, coding DNA, RNA, protein, and mitochondrial variants.
- HGVS notation is used in clinical reports and scientific publications.
- Understanding HGVS is essential for interpreting genetic test results.

---

# ⚡ Quick Revision

| Prefix | Meaning |
|---------|----------|
| g. | Genomic DNA |
| c. | Coding DNA |
| n. | Non-coding DNA |
| r. | RNA |
| p. | Protein |
| m. | Mitochondrial DNA |

---

# 📚 References

- HGVS Nomenclature Recommendations
- ClinGen
- ClinVar
- Ensembl VEP Documentation
- ACMG/AMP Variant Interpretation Guidelines

---

# ➡️ Next Lesson

**Germline vs Somatic Variants – Understanding Inherited and Acquired Mutations**
