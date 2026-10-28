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

| File | Description |
|---|---|
| `README.md` | Overview of the workflow, results, limitations, and reproducibility |
| `Galaxy31-[bcftools norm on dataset 30](2).vcf` | Normalized VCF output from the existing Galaxy workflow; retained in Galaxy history |
| `Galaxy35-[SnpEff eff_ on dataset 31 and 33](2).vcf` | SnpEff-annotated VCF output; retained in Galaxy history |
| `Galaxy36` SnpEff statistics | HTML summary of variant annotation statistics; retained in Galaxy history |
| `Galaxy38` autosomal-recessive results | Filtered candidate-variant table from GEMINI; retained in Galaxy history |

*Note: The Galaxy dataset names above identify existing workflow outputs. They are not necessarily files stored in this GitHub folder.*

## Variant Annotation Workflow

The existing Galaxy workflow includes VCF normalization with bcftools, variant-effect annotation with SnpEff, and candidate filtering using GEMINI under an autosomal-recessive inheritance model.

The resulting candidate table provides variant coordinates, reference and alternate alleles, predicted effects, gene names, genotype information, population-frequency fields, and available clinical-annotation fields.

## Preliminary Candidate Review

One candidate in the existing GEMINI output is annotated to **CA2**.

- **Variant:** chr8:86385979 G>A (GRCh37, as currently recorded)
- **Predicted consequence:** `stop_gained`
- **Maximum allele frequency field:** approximately 0.0000325
- **ClinVar significance field:** `None` in the current candidate table

These are preliminary annotations from the existing analysis. The exact variant identity, transcript consequence, population frequency, clinical evidence, and inheritance interpretation require verification before a disease-related conclusion can be made.

## Clinical and Population Evidence

ClinVar evidence must be checked against the exact variant and genome build. Population frequency must be independently verified using gnomAD, with the relevant population and allele-frequency field documented.

Disease-association evidence should be evaluated alongside the predicted molecular consequence, genotype pattern, inheritance model, and any conflicting or missing evidence.

A predicted high-impact consequence or a low population frequency alone does not establish pathogenicity.

## Limitations

- The candidate-filtering results depend on the quality and completeness of the input VCF and sample genotype data.
- Variant consequences depend on the reference genome, annotation database, transcript, and software versions used.
- Missing clinical annotations do not establish that a variant is benign.
- Population frequency and predicted consequences must be interpreted alongside clinical and inheritance evidence.
- Candidate prioritization is not equivalent to a confirmed clinical diagnosis.

## Reproducibility

The workflow was performed using Galaxy tools, including bcftools normalization, SnpEff annotation, and GEMINI candidate filtering.

To reproduce the analysis, document the input VCF source, reference genome build, tool names and versions, normalization and annotation settings, inheritance-model filtering criteria, and the source and date of external evidence reviews.

The relevant Galaxy history outputs should be retained so that the workflow and candidate table can be traced to their source datasets.

## Status

The initial Galaxy workflow and autosomal-recessive candidate filtering have been completed. External verification of the candidate variant, gnomAD population frequency review, disease-evidence assessment, and final annotation table remain to be completed. The candidate interpretation is therefore preliminary.
