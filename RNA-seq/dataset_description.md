# Dataset Description and Metadata Review

## Dataset Overview

This RNA-seq capstone uses gene-level count data from human airway smooth muscle cells treated with dexamethasone and untreated controls.

## Experimental Design

- **Total samples:** 8
- **Cell lines:** 4
- **Treatment groups:** Untreated and Dexamethasone
- **Design:** Each cell line has one untreated sample and one dexamethasone-treated sample.

## Sample Metadata

The sample metadata file contains the following fields:

| Field | Description |
|---|---|
| `names` | Sample accession identifier |
| `cell_line` | Airway smooth muscle cell line |
| `treatment` | Treatment condition |

The sample accessions include SRR1039508, SRR1039509, SRR1039512, SRR1039513, SRR1039516, SRR1039517, SRR1039520 and SRR1039521.

## Metadata Review

The metadata identifies the sample accession, cell line and treatment condition for each sample. The experimental design includes paired treatment conditions within each cell line.

The differential-expression model uses the formula `~ cell_line + treatment` to account for cell-line differences while evaluating the treatment effect.

## Data Files

- `clean_count_matrix.csv` — gene-level count matrix.
- `clean_sample_metadata.csv` — sample metadata.

## Status

Dataset description and metadata review documented.
