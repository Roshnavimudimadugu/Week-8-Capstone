# RNA-seq Quality Control Assumptions

## Objective

Document the quality-control assumptions relevant to the RNA-seq differential-expression analysis.

## Sample and Metadata Checks

- The count matrix contains 8 samples.
- The metadata identifies each sample by accession, cell line and treatment.
- Sample identifiers must match between the count matrix and metadata.
- Each of the four cell lines has an untreated sample and a dexamethasone-treated sample.

## Count Data Assumptions

- The input matrix contains gene-level counts.
- Counts must be numeric, non-negative and suitable for DESeq2 analysis.
- Low-count genes are filtered using the rule `rowSums(counts) > 1`.

## Statistical Assumptions

- DESeq2 models count data using a negative-binomial distribution.
- The design formula `~ cell_line + treatment` accounts for cell-line differences when testing the treatment effect.
- Adjusted p-values are used to account for multiple testing.

## Limitations

The dataset contains only eight samples, with one sample per treatment condition within each cell line. This limits the ability to estimate within-cell-line biological variability independently. The analysis should therefore be interpreted with appropriate caution.

## Status

QC assumptions documented. These statements describe analysis assumptions and checks; they do not replace verification of raw sequencing quality metrics.
