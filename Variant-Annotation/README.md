# Capstone 2 — Variant Annotation Workflow

## From VCF Record to Evidence-Based Interpretation

## 1. Objective

The objective of this capstone is to demonstrate a trio-based variant annotation and prioritisation workflow, starting from a VCF and progressing through variant normalisation, functional annotation, inheritance-pattern filtering, and evidence review.

The workflow prioritises a candidate variant for further investigation. The result is a preliminary computational interpretation and is **not a clinical diagnosis or a definitive pathogenicity classification**.

## 2. Dataset Description

- **Data type:** Trio variant data (mother, father and proband)
- **Reference assembly used for the Galaxy workflow:** GRCh37 / hg19
- **Input:** Galaxy Dataset 30 VCF (the source for the normalised Dataset 31)
- **Normalised VCF:** Galaxy Dataset 31
- **SnpEff-annotated VCF:** Galaxy Dataset 35
- **GEMINI autosomal-recessive output:** Galaxy Dataset 38

The SnpEff VCF header identifies the reference as hg19 and records SnpEff version 5.4c. The candidate is represented at chr8:86385980 G>A in the VCF (1-based VCF position). The corresponding GEMINI `start` value is chr8:86385979, which is a 0-based start coordinate.

## 3. Workflow Overview

```text
Input VCF (Galaxy Dataset 30)
             |
             v
VCF normalisation — bcftools (Dataset 31)
             |
             v
Functional annotation — SnpEff (Dataset 35)
             |
             v
GEMINI database and family-based filtering
             |
             v
Autosomal-recessive candidate output (Dataset 38)
             |
             v
Candidate review: CA2, chr8:86385980 G>A
             |
             v
Coordinate conversion: GRCh37 to GRCh38
             |
             v
External evidence review: ClinVar / dbSNP / gnomAD
             |
             v
Preliminary evidence-based interpretation
```

## 4. Repository Contents

The repository is organised as follows:

```text
Variant-Annotation/
│
├── README.md
│
├── results/
│   ├── README.md
│   ├── candidate_variant_summary.md
│   ├── final_variant_annotation.csv
│   └── snpeff_summary.md
│
└── evidence/
    ├── README.md
    ├── 01_galaxy_workflow_history.png
    ├── 02_snpeff_candidate_annotation.png
    ├── 03_gnomad_variant_frequency.png
    ├── 04_dbsnp_variant_summary.png
    ├── 05_dbsnp_submissions.png
    ├── 06_clinvar_rsID_search.png
    └── variant_workflow.png
```

The `results/` directory contains the final variant annotation table and supporting result summaries.

The `evidence/` directory contains screenshots documenting the Galaxy workflow, SnpEff annotation, gnomAD population-frequency review, dbSNP records, ClinVar search and variant workflow diagram.

## 5. Variant Annotation Workflow

### 5.1 VCF Normalisation

The source VCF was processed with **bcftools norm** against the hg19 reference. The Dataset 31 output was used as the normalised VCF for subsequent annotation.

### 5.2 SnpEff Annotation

Galaxy Dataset 35 contains SnpEff annotations. Its VCF header records SnpEff version 5.4c and the `hg19` database.

The candidate record is annotated as:

- **Gene:** CA2
- **Transcript:** NM_000067.3
- **Consequence:** stop_gained
- **Predicted protein change:** p.Trp97*
- **HGVS coding change:** c.291G>A
- **Annotation impact:** HIGH

The same record also contains a CA2 intron annotation on another transcript. Transcript-specific consequences should therefore be retained when interpreting the result.

### 5.3 GEMINI Family-Based Filtering

Galaxy Dataset 38 is the output of the GEMINI autosomal-recessive pattern query. The CA2 candidate row reports:

- `impact`: `stop_gained`
- `gene`: `CA2`
- `clinvar_sig`: `None`
- `clinvar_disease_name`: `None`
- `max_aaf_all`: `3.24886289799e-05`
- **Family genotypes:** Mother G/A, father G/A, proband A/A

The `max_aaf_all` value is the field reported by this GEMINI output. It should not be substituted for the independently reviewed gnomAD v4.1.2 allele frequency below.

## 6. Preliminary Candidate Review

The prioritised candidate is a CA2 G>A single-nucleotide variant.

| Parameter | Finding |
|---|---|
| Gene | CA2 |
| GRCh37 / hg19 VCF coordinate | chr8:86385980 |
| Reference / alternate allele | G>A |
| GRCh38 / hg38 coordinate | chr8:85473751 |
| dbSNP identifier | rs1173332839 |
| Transcript | NM_000067.3 |
| HGVS coding change | c.291G>A |
| Predicted protein change | p.Trp97Ter (p.Trp97*) |
| SnpEff consequence | stop_gained |
| SnpEff impact | HIGH |
| Trio genotypes | Mother G/A; father G/A; proband A/A |

The parental and proband genotypes are consistent with a homozygous alternate genotype in the proband and heterozygosity in both parents. This is compatible with a recessive inheritance pattern in this trio, but does not by itself establish disease causality.

## 7. ClinVar and dbSNP Review

The dbSNP record **rs1173332839** reports:

- **GRCh38.p14 position:** chr8:85473751
- **Alleles:** G>A / G>T
- **Gene and consequence:** CA2; stop gained
- **Clinical significance:** Not Reported in ClinVar
- **Publications:** 0 citations on the displayed dbSNP record

The G>A allele is the allele under review in this capstone. The dbSNP record lists G>T as another alternate allele; evidence for G>T must not be combined with evidence for G>A.

The dbSNP Submissions tab displayed three SubSNP submissions and one frequency submission, including submissions from gnomAD and VINODS. These are dbSNP submissions and do not constitute clinical classifications.

The candidate rsID was also searched in ClinVar, but no matching clinical classification was identified in the reviewed search.

**Interpretation:** No clinical classification was identified in the reviewed dbSNP/ClinVar evidence. This must not be interpreted as evidence that the variant is benign.

## 8. gnomAD Population-Frequency Review

The variant was reviewed in **gnomAD v4.1.2** using the GRCh38 coordinate and allele representation `8-85473751-G-A`.

| Parameter | gnomAD result |
|---|---:|
| Overall allele count (AC) | 2 |
| Overall allele number (AN) | 1,612,986 |
| Overall allele frequency (AF) | 0.000001240 |
| Exome AC | 2 |
| Exome AN | 1,460,812 |
| Exome AF | 0.000001369 |
| Genome AC | 0 |
| Genome AN | 152,174 |
| Homozygous alternate individuals | 0 |
| South Asian AC | 2 |
| South Asian AN | 91,046 |
| South Asian AF | 0.00002197 |

The candidate is very rare in the gnomAD dataset. Two alternate alleles were observed overall, and no homozygous alternate individuals were reported. The South Asian subgroup frequency is based on two observed alternate alleles.

Population rarity is supporting evidence only. It does not independently establish pathogenicity, and the small allele count should be considered when interpreting subgroup frequencies.

## 9. Disease-Association Evidence

The GEMINI output's `clinvar_gene_phenotype` field contains the terms `carbonic_anhydrase_ii_variant` and `osteopetrosis_with_renal_tubular_acidosis`.

These terms are recorded here as annotations present in the supplied GEMINI result. They are not, on their own, proof that this specific variant causes the phenotype. A separate, authoritative gene–disease and variant-level evidence assessment would be needed before making a clinical association.

## 10. Conflicting Evidence and Uncertainty

The following evidence and limitations were considered:

- The candidate has a high-impact, stop-gained annotation in the SnpEff output.
- The trio genotypes are compatible with a recessive inheritance pattern.
- The variant is very rare in gnomAD v4.1.2.
- The reviewed dbSNP summary reports no ClinVar clinical significance.
- The dbSNP record includes both G>A and G>T alleles; only G>A is the candidate assessed here.
- Population frequency and predicted consequence do not establish pathogenicity.
- The available computational and database evidence is insufficient for a definitive clinical classification.

## 11. Final Variant Annotation Table

See [`results/final_variant_annotation.csv`](results/final_variant_annotation.csv) for the consolidated machine-readable table.

The candidate is classified in this project as:

**Preliminary candidate — further clinical and functional validation required.**

This is a project-level prioritisation label, not a clinical classification such as pathogenic, likely pathogenic, VUS, likely benign or benign.

## 12. Biological Interpretation

The CA2 candidate is annotated by SnpEff as a stop-gained variant, with the transcript-specific predicted protein change p.Trp97Ter. A premature termination codon may disrupt the encoded protein, but the biological effect should not be assumed from annotation alone.

The observed trio genotypes (mother G/A, father G/A, proband A/A) are compatible with recessive inheritance. The very low gnomAD allele frequency provides population context. However, the absence of a reported ClinVar classification and the lack of variant-specific functional or clinical evidence mean that the candidate remains preliminary.

## 13. Limitations

- The analysis depends on the quality and completeness of the supplied trio VCF and family metadata.
- Variant coordinates differ between genome assemblies. The GRCh37-to-GRCh38 coordinate conversion was performed using UCSC LiftOver; allele identity and strand representation should be checked when transferring variants between assemblies.
- SnpEff predictions are transcript- and database-dependent.
- GEMINI filtering prioritises candidates according to the specified inheritance model and available annotations; it does not establish causality.
- gnomAD represents population reference data and is not a clinical diagnostic database.
- No ClinVar clinical significance was reported in the reviewed dbSNP summary or matching ClinVar search.
- The available evidence does not support a definitive pathogenicity classification.

## 14. Reproducibility

To understand or reproduce the analysis:

1. Start from the original trio VCF in the Galaxy history (Dataset 30).
2. Review the bcftools-normalised VCF (Dataset 31).
3. Review the SnpEff-annotated VCF (Dataset 35), including the SnpEff version and hg19 reference recorded in its header.
4. Review the GEMINI autosomal-recessive output (Dataset 38) and locate the CA2 candidate row.
5. Verify the candidate's transcript-specific annotation in the SnpEff VCF.
6. Convert the candidate coordinate from GRCh37/hg19 to GRCh38/hg38 using UCSC LiftOver.
7. Review the exact G>A allele in gnomAD v4.1.2 and the corresponding dbSNP record.
8. Search ClinVar using the candidate identifier and record whether a matching clinical classification is available.
9. Record database versions, genome assembly, allele representation and evidence limitations when updating the interpretation.

The evidence screenshots and result files are provided in the `evidence/` and `results/` directories.

## 15. Project Status

**Computational workflow and preliminary candidate review documented.**

The CA2 G>A variant is retained as a preliminary candidate because the computational annotation, trio genotypes and population-frequency evidence warrant further review. Clinical pathogenicity has not been established.
