# Variant Annotation Results

This folder contains the final candidate variant annotation table and supporting summaries generated during the variant annotation workflow.

## Files

| File | Description |
|---|---|
| `final_variant_annotation.csv` | Consolidated annotation table containing candidate variant coordinates, gene, transcript, HGVS annotation, trio genotypes, population frequency and clinical database evidence. |
| `candidate_variant_summary.md` | Summary of the prioritised CA2 candidate variant, inheritance pattern, population evidence and preliminary interpretation. |
| `snpeff_summary.md` | Candidate-specific SnpEff annotation, including variant consequence, transcript, predicted impact and family genotypes. |

## Candidate Variant

The prioritised candidate is a **CA2 stop-gained variant (G>A)**:

- **GRCh37/hg19:** chr8:86385980
- **GRCh38/hg38:** chr8:85473751
- **dbSNP:** rs1173332839
- **Transcript:** NM_000067.3
- **Predicted consequence:** stop_gained

## Interpretation

The candidate was prioritised based on its predicted high-impact consequence, trio genotype pattern and rarity in the gnomAD population database.

The available evidence supports further investigation but does not establish clinical pathogenicity. Clinical and functional validation would be required.
