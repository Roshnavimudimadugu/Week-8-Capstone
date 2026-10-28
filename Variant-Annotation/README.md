# Variant Annotation Capstone

## Objective

Develop a reproducible variant annotation workflow, starting from a VCF file and progressing through variant filtering, gene and transcript annotation, population-frequency review, clinical evidence assessment, and evidence-based interpretation.

## Workflow

1. Identify the variant data source
2. Review and normalize the VCF data
3. Filter candidate variants using the selected inheritance model
4. Annotate genes and transcripts
5. Review predicted variant consequences
6. Review ClinVar clinical evidence
7. Review gnomAD population allele frequencies
8. Examine disease-association evidence
9. Assess conflicting or missing evidence
10. Prepare the final variant annotation table
11. Document interpretation limitations
12. Provide reproducibility instructions

## Repository Contents

| File or Dataset | Description |
|---|---|
| `README.md` | Overview of the workflow, preliminary results, limitations, and reproducibility |
| Galaxy Dataset 31 | Normalized VCF output generated using bcftools |
| Galaxy Dataset 35 | SnpEff-annotated VCF output |
| Galaxy Dataset 36 | HTML summary of SnpEff annotation statistics |
| Galaxy Dataset 38 | GEMINI candidate variants filtered under an autosomal-recessive inheritance model |

*Note: These Galaxy datasets are existing workflow outputs and are not necessarily files stored in this GitHub folder.*

## Variant Annotation Workflow

The existing Galaxy workflow includes VCF normalization with bcftools, variant-effect annotation with SnpEff, and candidate filtering using GEMINI under an autosomal-recessive inheritance model.

The resulting candidate table contains variant coordinates, reference and alternate alleles, predicted effects, gene names, genotype information, population-frequency fields, and available clinical-annotation fields.

## Preliminary Candidate Review

One candidate in the existing GEMINI output is annotated to **CA2**.

- **Variant:** chr8:86385979 G>A (GRCh37, as currently recorded)
- **Predicted consequence:** `stop_gained`
- **Maximum allele frequency in Dataset 38:** approximately 0.0000325
- **ClinVar significance field:** `None` in the current candidate table
- **Genotypes:** Mother G/A, father G/A, proband A/A

These are preliminary annotations from the existing analysis. The exact variant identity, transcript consequence, population frequency, clinical evidence, and inheritance interpretation must be verified before a disease-related conclusion can be made.

## ClinVar Review

The existing Dataset 38 output does not contain a ClinVar significance annotation for this candidate.

The exact variant must be checked against ClinVar using the correct genomic position and reference genome build.

- **Candidate variant:** chr8:86385979 G>A (GRCh37)
- **Gene:** CA2
- **Current analysis result:** The `clinvar_sig` field is `None`.
- **Evidence status:** A matching ClinVar record and any associated clinical classification require verification.
- **Interpretation limitation:** The absence of a ClinVar annotation in the current table does not establish whether the variant is benign or pathogenic.

## Clinical and Population Evidence

Clinical interpretation requires more than a predicted variant consequence. ClinVar evidence, population frequency, disease association, inheritance pattern, and potential conflicting evidence must be assessed together.

Population-frequency information should be obtained from gnomAD using the exact variant and a clearly identified genome build and dataset. The relevant allele count, allele frequency, homozygous alternate count, and available quality flags should be recorded.

Disease-association evidence should be evaluated alongside the predicted molecular consequence, genotype pattern, inheritance model, and any conflicting or missing evidence.

A predicted high-impact consequence or a low population frequency alone does not establish pathogenicity.

### gnomAD Population-Frequency Review

- **Candidate:** CA2 chr8:86385979 G>A (GRCh37)
- **External variant reference:** [GeneBe — CA2 variant record](https://genebe.net/variant/hg19/8-86385979-G-A)
- **Reported dataset:** gnomAD v4 exomes
- **Reported allele frequency:** Approximately 6.85 × 10⁻⁷
- **Reported allele count:** 1
- **Reported homozygous alternate count:** 0
- **Evidence caveat:** The external summary flags a strongly skewed allele balance. This requires cautious interpretation and review of the underlying record and quality metrics.
- **Interpretation:** The external summary reports the variant at a very low frequency. This observation alone does not establish pathogenicity.

**Verification status:** The frequency is reported in an external variant summary. The underlying gnomAD record, genome build, and quality flags must be checked before the value is treated as a verified final result.

## Disease-Association Evidence

The CA2 gene and the predicted `stop_gained` consequence provide a starting point for investigating potential disease relevance. However, a gene-level disease association does not establish that this specific variant explains the proband's condition.

The exact variant must be assessed using reliable disease resources, relevant transcript information, inheritance evidence, and any available clinical classification.

**Current status:** A disease-related interpretation remains provisional until the evidence has been independently verified.

## Conflicting Evidence and Uncertainty

The current results include a predicted high-impact consequence and a low population-frequency value reported by an external summary. These observations are not sufficient on their own to establish pathogenicity.

The following points require consideration:

- The ClinVar significance field is `None` in Dataset 38.
- The external population-frequency summary flags an allele-balance concern.
- The exact transcript and protein consequence must be confirmed against the selected reference build.
- The family genotypes and inheritance pattern require evaluation alongside the relevant disease mechanism.
- Missing clinical evidence must not be interpreted as evidence that a variant is benign.

## Final Variant Annotation Table

The final annotation table will consolidate the evidence for each selected candidate.

| Field | Current candidate information |
|---|---|
| Chromosome | chr8 |
| Position | 86385979 |
| Reference allele | G |
| Alternate allele | A |
| Genome build | GRCh37, as currently recorded |
| Gene | CA2 |
| Predicted consequence | `stop_gained` |
| Dataset 38 maximum allele frequency | Approximately 0.0000325 |
| External gnomAD frequency | Approximately 6.85 × 10⁻⁷, pending verification |
| ClinVar classification | Not established from the current candidate table |
| Disease association | Requires further evidence review |
| Interpretation status | Preliminary; not a confirmed clinical classification |

*The final table must be updated when the exact variant identity, transcript annotation, external population-frequency record, and clinical evidence have been verified.*

## Limitations

- The candidate-filtering results depend on the quality and completeness of the input VCF and sample genotype data.
- Variant consequences depend on the reference genome, transcript annotation, database versions, and software settings.
- Missing clinical annotations do not establish that a variant is benign.
- Population frequencies and predicted consequences must be interpreted alongside clinical and inheritance evidence.
- Candidate prioritization is not equivalent to a confirmed clinical diagnosis.
- External database records may differ in genome build, dataset, transcript, and quality metrics.

## Reproducibility

The workflow was performed using Galaxy tools, including bcftools normalization, SnpEff annotation, and GEMINI candidate filtering.

To reproduce the analysis, document:

1. The source and version of the input VCF.
2. The reference genome build.
3. The names and versions of the tools used.
4. The normalization and annotation settings.
5. The inheritance-model filtering criteria.
6. The sources and dates of ClinVar and gnomAD reviews.
7. The method used to assemble the final annotation table.

The relevant Galaxy history outputs should be retained so that the workflow and candidate table can be traced to their source datasets.

## Status

The initial Galaxy workflow and autosomal-recessive candidate filtering have been completed. ClinVar verification, independent confirmation of the gnomAD frequency, disease-association assessment, and final evidence review remain to be completed.

The CA2 candidate is therefore a preliminary result, not a confirmed disease-causing variant.
