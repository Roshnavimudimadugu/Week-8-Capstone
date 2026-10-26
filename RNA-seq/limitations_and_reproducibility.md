# Limitations and Reproducibility

## Limitations

- The dataset contains eight samples from four airway smooth muscle cell lines.
- Each cell line has one untreated sample and one dexamethasone-treated sample, limiting the estimation of biological variability within each cell line.
- The findings are specific to this experimental cell model and should not automatically be generalised to other biological systems.
- Differential-expression results depend on count filtering, model specification and statistical thresholds.
- Gene Ontology enrichment depends on the selected gene set and annotation database.
- Enrichment results indicate over-represented biological processes and do not establish causal mechanisms.
- The original project reported 3,541 significant genes, while the recreated analysis reported 3,974. This difference remains unresolved.

## Reproducibility

The analysis was performed in R using DESeq2.

### Input data

- `clean_count_matrix.csv` — gene-level count matrix.
- `clean_sample_metadata.csv` — sample metadata.

### Model

The differential-expression model uses:

`~ cell_line + treatment`

The treatment comparison is dexamethasone versus untreated, with untreated as the reference condition.

### Filtering and significance

Genes were filtered using `rowSums(counts) > 1`. Statistical significance was assessed using an adjusted p-value threshold of 0.05.

### Outputs

The project includes:

- Full differential-expression results table
- Top differentially expressed genes table
- PCA plot
- Heatmap
- Volcano plot
- GO enrichment results
- Top 20 GO terms
- Biological interpretation

### Reproduction notes

To reproduce the analysis, use the documented input data, confirm that sample identifiers match between the count matrix and metadata, and run the DESeq2 workflow in an R environment with the required packages installed.

The original and recreated results should not be considered equivalent until the difference in significant-gene counts has been investigated.

## Status

Limitations and reproducibility instructions documented.
