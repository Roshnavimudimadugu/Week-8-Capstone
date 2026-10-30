# SnpEff Annotation Summary

## Tool and reference

The SnpEff-annotated VCF (Galaxy Dataset 35) was used to examine the functional consequences of the candidate variant.

- **SnpEff version:** 5.4c
- **Reference genome:** hg19 (GRCh37)
- **Candidate chromosome:** chr8
- **Candidate VCF position:** 86385980
- **Reference / alternate allele:** G>A

## Candidate annotation

| Field | Annotation |
|---|---|
| Gene | CA2 |
| Transcript | NM_000067.3 |
| Transcript biotype | protein_coding |
| Consequence | stop_gained |
| Impact | HIGH |
| HGVS.c | c.291G>A |
| HGVS.p | p.Trp97* |
| LOF annotation | CA2; 2 transcripts; 0.50 |
| NMD annotation | CA2; 2 transcripts; 0.50 |

The candidate variant is annotated as a **stop-gained variant** in the CA2 protein-coding transcript NM_000067.3. This predicts the introduction of a premature termination codon.

The VCF also contains an `intron_variant` annotation for CA2 on transcript NM_001293675.1. Variant consequences are transcript-specific; therefore, the transcript used for interpretation is explicitly stated.

The LOF and NMD values are annotations recorded in the VCF and should not be considered experimental confirmation of loss of function or nonsense-mediated decay.

## Family genotypes in the SnpEff VCF

The genotype calls for the candidate variant are:

- **Mother:** 0/1 (heterozygous)
- **Father:** 0/1 (heterozygous)
- **Proband:** 1/1 (homozygous alternate)

This genotype pattern is compatible with autosomal recessive inheritance in the trio. However, it does not independently establish disease causality.

## Interpretation

The SnpEff annotation predicts a high-impact stop-gained consequence in CA2. Together with the observed trio genotypes, this supports prioritising the variant for further investigation.

SnpEff provides functional consequence predictions rather than a clinical pathogenicity classification. Further clinical and functional evidence is required before drawing conclusions about pathogenicity.

**Note:** This summary reports the candidate-specific annotation extracted from Galaxy Dataset 35. It is not a genome-wide SnpEff statistics report. Galaxy Dataset 36 contains the overall SnpEff statistics and can be retained as separate workflow evidence.
