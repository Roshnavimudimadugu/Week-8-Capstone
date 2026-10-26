# DESeq2 Differential Expression Workflow

## Objective

Identify genes with differential expression between dexamethasone-treated and untreated airway smooth muscle cell samples.

## Input Data

- Gene-level count matrix: `clean_count_matrix.csv`
- Sample metadata: `clean_sample_metadata.csv`
- Number of samples: 8
- Number of genes before filtering: 31,604

## Experimental Design

The DESeq2 design formula is:

`~ cell_line + treatment`

This model accounts for differences between cell lines while estimating the treatment effect.

The reference treatment is `Untreated`, and the comparison is `Dexamethasone` versus `Untreated`.

## Analysis Steps

1. Load the gene-level count matrix and sample metadata.
2. Match sample identifiers between the count matrix and metadata.
3. Construct a DESeq2 dataset.
4. Filter genes using `rowSums(counts) > 1`.
5. Estimate size factors and dispersions.
6. Fit the negative-binomial model.
7. Perform the treatment comparison.
8. Apply Benjamini–Hochberg adjustment for multiple testing.
9. Export the complete results table.

## Statistical Significance

Genes are considered statistically significant when their adjusted p-value is below 0.05.

## Output

The recreated analysis generated `full_DESeq2_results.csv`, containing gene identifiers, mean expression, log2 fold changes, standard errors, test statistics, p-values and adjusted p-values.

**Note:** The recreated analysis reported 3,974 significant genes, whereas the original project README reports 3,541. This discrepancy requires reconciliation before the recreated result is treated as the final result.

## Limitations

The dataset has eight samples across four cell lines. The small sample size limits statistical power and the estimation of biological variability.

## Status

DESeq2 workflow documented; the difference between the original and recreated results remains unresolved.
