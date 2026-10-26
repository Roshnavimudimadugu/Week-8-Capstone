# RNA-seq Differential Expression Capstone

## Objective

Perform RNA-seq differential expression analysis, starting from a gene count matrix and sample metadata through statistical analysis and biological interpretation.

## Workflow

1. Dataset description and metadata review
2. Quality-control assumptions
3. Differential expression analysis using DESeq2
4. Principal component analysis (PCA)
5. Heatmap and volcano plot
6. Top differentially expressed genes
7. Functional enrichment analysis
8. Biological interpretation
9. Limitations and assumptions
10. Reproducibility instructions

## Repository Contents

| File | Description |
|---|---|
| `dataset_description.md` | Dataset and sample metadata review |
| `qc_assumptions.md` | Quality-control assumptions |
| `deseq2_workflow.md` | Differential expression workflow |
| `PCA_treatment.png` | PCA plot |
| `heatmap_top30_DE_genes.png` | Heatmap of the top 30 differentially expressed genes |
| `volcano_plot.png` | Volcano plot generated from the recreated analysis |
| `full_DESeq2_results.csv` | Complete results from the recreated DESeq2 analysis |
| `top20_differential_expression.csv` | Top differentially expressed genes |
| `GO_enrichment_results.csv` | Gene Ontology enrichment results |
| `top20_GO_terms.csv` | Top 20 GO enrichment terms |
| `biological_interpretation.md` | Biological interpretation |
| `limitations_and_reproducibility.md` | Limitations and reproduction instructions |

## Statistical Analysis

The DESeq2 model uses the design formula:

`~ cell_line + treatment`

The treatment comparison is dexamethasone versus untreated, with untreated as the reference condition. Statistical significance is assessed using an adjusted p-value threshold of 0.05.

## Results Validation Note

The recreated analysis reported 3,974 genes with adjusted p-values below 0.05, whereas the original project README reported 3,541 significant genes. This discrepancy remains unresolved. The recreated results and volcano plot should therefore be considered provisional until the difference is investigated.

## Limitations

The dataset contains eight samples from four airway smooth muscle cell lines. The small sample size limits the estimation of biological variability and the generalisability of findings. Gene Ontology enrichment identifies over-represented biological processes but does not establish causation.

## Status

Documentation, result tables and figures have been added. Validation of the difference between the original and recreated differential-expression results remains pending.
