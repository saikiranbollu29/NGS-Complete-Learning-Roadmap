# 🧬 Variant Annotation – VEP, ANNOVAR & SnpEff

> [!NOTE]
> **Module 4 • Lesson 9**
>
> Learn how genetic variants are annotated to determine their biological function, disease association, and clinical significance. This lesson covers VEP, ANNOVAR, SnpEff, and interpretation using public databases.

---

# 🧬 Pipeline Position

```text
FASTQ
   │
   ▼
FastQC
   │
   ▼
Fastp
   │
   ▼
BWA
   │
   ▼
Samtools
   │
   ▼
GATK / BCFtools
   │
   ▼
Variant Annotation   ← You are here
   │
   ▼
Clinical Interpretation
   │
   ▼
Report Generation
```

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand variant annotation.
- Learn why annotation is essential.
- Use VEP, ANNOVAR and SnpEff.
- Interpret gene consequences.
- Understand pathogenicity prediction.
- Use public variant databases.
- Prepare variants for clinical interpretation.

---

# 📚 Prerequisites

- Variant Calling
- VCF Files
- Basic Human Genetics

---

# 💡 Why Variant Annotation?

Variant calling tells us

```
chr17

43045702

G

A
```

But this alone is not biologically meaningful.

Annotation answers:

✔ Which gene?

✔ Which transcript?

✔ Amino acid change?

✔ Protein effect?

✔ Clinical significance?

✔ Population frequency?

✔ Disease association?

---

# 📌 What is Variant Annotation?

Variant annotation is the process of adding biological information to genetic variants.

Input

```
VCF
```

Output

Annotated VCF or tabular report containing:

- Gene
- Transcript
- Protein change
- Consequence
- Clinical databases
- Population frequency

---

# 📌 Major Annotation Tools

| Tool | Developed By | Main Purpose |
|------|--------------|--------------|
| VEP | Ensembl | Comprehensive annotation |
| ANNOVAR | Wang Lab | Functional annotation |
| SnpEff | Pablo Cingolani | Variant effect prediction |

---

# 📌 Comparison

| Feature | VEP | ANNOVAR | SnpEff |
|----------|-----|----------|---------|
| Ensembl Integration | ✅ | ❌ | Limited |
| ClinVar Support | ✅ | ✅ | ✅ |
| gnomAD | ✅ | ✅ | ✅ |
| HGVS Notation | ✅ | ✅ | ✅ |
| Protein Prediction | ✅ | Limited | ✅ |
| Open Source | ✅ | Free for academic use | ✅ |

---

# 📌 What Information is Added?

Example

Before annotation

```
chr17 43045702 G A
```

After annotation

```
Gene

BRCA1

Transcript

NM_007294

Protein

p.Val1736Ala

Consequence

Missense Variant

ClinVar

Likely Pathogenic

gnomAD AF

0.00002
```

---

# 📌 Variant Consequences

| Consequence | Meaning |
|-------------|----------|
| Synonymous | No amino acid change |
| Missense | Amino acid changes |
| Nonsense | Premature stop codon |
| Frameshift | Reading frame changes |
| Splice Site | Affects RNA splicing |
| Start Lost | Start codon affected |
| Stop Lost | Stop codon removed |
| Intron Variant | Located in intron |
| UTR Variant | Located in untranslated region |

---

# 📌 Installing VEP

```bash
mamba install ensembl-vep -c bioconda
```

Verify

```bash
vep --help
```

---

# 📌 Installing SnpEff

```bash
mamba install snpeff -c bioconda
```

Verify

```bash
snpEff
```

---

# 📌 ANNOVAR

ANNOVAR is downloaded separately after registration from its official website.

It supports annotation using multiple databases such as RefGene, ClinVar, dbSNP, gnomAD, and others.

---

# 📌 Example VEP Command

```bash
vep \
-i variants.vcf \
-o annotated.vcf \
--cache \
--assembly GRCh38
```

---

# 📌 Example SnpEff Command

```bash
snpEff \
GRCh38.109 \
variants.vcf \
> annotated.vcf
```

---

# 📌 Public Databases Used

| Database | Purpose |
|-----------|----------|
| ClinVar | Clinical significance |
| dbSNP | Known variants |
| gnomAD | Population allele frequencies |
| COSMIC | Somatic cancer variants |
| OMIM | Mendelian diseases |
| HGNC | Gene names |
| Ensembl | Gene models and transcripts |

---

# 📌 HGVS Nomenclature

Example

```
BRCA1

c.5266dupC

↓

Protein

p.Gln1756ProfsTer74
```

HGVS provides a standardized way to describe DNA and protein variants.

---

# 📌 Population Frequency

Example

```
gnomAD AF

0.45
```

Common variant

Likely benign

---

Example

```
gnomAD AF

0.00001
```

Very rare

May require further evaluation depending on other evidence.

Population frequency alone does not determine pathogenicity.

---

# 📌 Clinical Databases

## ClinVar

Clinical interpretation

Example

```
Pathogenic

Likely Pathogenic

Benign

Likely Benign

Uncertain Significance (VUS)
```

---

## COSMIC

Cancer mutations

Widely used in oncology.

---

## dbSNP

Known genetic variants.

---

# 📌 Prediction Scores

Many annotation workflows include prediction scores.

Common examples:

| Tool | Prediction |
|------|-------------|
| SIFT | Damaging / Tolerated |
| PolyPhen-2 | Probably damaging / Benign |
| CADD | Deleteriousness score |
| REVEL | Missense pathogenicity |

These predictions provide supporting evidence and should be interpreted together with other clinical and biological information.

---

# 📊 Example Annotation

Input

```
chr17

43045702

G

A
```

Annotated Output

| Field | Result |
|---------|---------|
| Gene | BRCA1 |
| Transcript | NM_007294 |
| Protein | p.Val1736Ala |
| Consequence | Missense |
| ClinVar | Likely Pathogenic |
| gnomAD AF | 0.00002 |
| SIFT | Damaging |
| PolyPhen | Probably Damaging |

---

# 🧬 Clinical Workflow

```
VCF

↓

VEP / ANNOVAR / SnpEff

↓

Gene Annotation

↓

Population Frequency

↓

Clinical Databases

↓

Pathogenicity Evidence

↓

Variant Classification

↓

Clinical Report
```

---

# 🤖 Bash Automation

```bash
#!/bin/bash

mkdir -p annotation

for vcf in variants/*.vcf
do

sample=$(basename "$vcf" .vcf)

vep \
-i "$vcf" \
-o annotation/${sample}.annotated.vcf \
--cache \
--assembly GRCh38

done

echo "Annotation completed."
```

---

# 🧬 Clinical & Research Perspective

Example

```
Patient

↓

DNA Sequencing

↓

Variant Calling

↓

Variant Annotation

↓

ClinVar

↓

gnomAD

↓

Literature Review

↓

ACMG Classification

↓

Clinical Report
```

Annotation provides biological context, but clinical interpretation also considers phenotype, family history, inheritance pattern, and professional guidelines.

---

# 🚨 Common Errors

## Error

```
Cache not found
```

Download the appropriate VEP cache for your genome assembly.

---

## Error

```
Genome version mismatch
```

Ensure your annotation database matches the reference genome (GRCh37 vs GRCh38).

---

## Error

```
Unknown chromosome
```

Check chromosome naming conventions (e.g., `1` vs `chr1`) and ensure consistency between the VCF and annotation database.

---

# 🧠 Interview Questions

### ❓ What is variant annotation?

The process of adding biological and functional information to genetic variants.

---

### ❓ Why is annotation necessary?

Because genomic coordinates alone do not indicate the affected gene, protein consequence, or potential clinical significance.

---

### ❓ What is the difference between variant calling and annotation?

Variant calling identifies differences between the sample and reference genome, while annotation interprets those differences biologically.

---

### ❓ Name three commonly used annotation tools.

- VEP
- ANNOVAR
- SnpEff

---

### ❓ What is ClinVar?

A public database that aggregates information about the clinical significance of human genetic variants.

---

### ❓ Can a rare variant automatically be considered pathogenic?

No. Rarity is only one piece of evidence. Clinical interpretation requires integrating multiple sources of evidence, including functional impact, inheritance, phenotype, literature, and established guidelines.

---

# 📝 Lesson Summary

- Variant annotation adds biological meaning to genetic variants.
- VEP, ANNOVAR, and SnpEff are widely used annotation tools.
- Annotation integrates information from databases such as ClinVar, gnomAD, dbSNP, and COSMIC.
- Functional consequences and prediction scores help prioritize variants.
- Annotation is the bridge between variant detection and clinical interpretation.

---

# ⚡ Quick Revision

| Step | Tool |
|------|------|
| Variant Calling | GATK / BCFtools |
| Annotation | VEP / ANNOVAR / SnpEff |
| Population Frequency | gnomAD |
| Clinical Database | ClinVar |
| Cancer Database | COSMIC |
| Standard Nomenclature | HGVS |

---

# 📚 References

- Ensembl VEP Documentation
- ANNOVAR Documentation
- SnpEff Documentation
- ClinVar
- gnomAD
- COSMIC
- ACMG/AMP Variant Interpretation Guidelines

---

# ➡️ Next Lesson

**ACMG Variant Classification & Clinical Interpretation (Pathogenic, Likely Pathogenic, VUS, Likely Benign, Benign)**
