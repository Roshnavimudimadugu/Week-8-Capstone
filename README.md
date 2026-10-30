# Week 8 — Bioinformatics Capstone Projects

## RNA-seq Differential Expression Analysis and Variant Annotation

This repository contains two bioinformatics capstone projects demonstrating the application of computational approaches to analyse sequencing data, identify biologically relevant findings and interpret genomic variants.

The projects integrate data processing, statistical analysis, functional annotation, biological interpretation and reproducible computational workflows.

---

## Capstone Projects

### Capstone 1 — RNA-seq Differential Expression Analysis

**From Count Matrix to Biological Interpretation**

The objective of this project is to perform RNA-seq differential expression analysis, starting from a gene count matrix and sample metadata through statistical analysis and biological interpretation.

**Key components:**

- Dataset description and sample metadata review
- Quality-control assumptions
- Differential expression analysis using DESeq2
- Principal Component Analysis (PCA)
- Heatmap and volcano plot
- Identification of top differentially expressed genes
- Gene Ontology (GO) enrichment analysis
- Biological interpretation
- Limitations and reproducibility

**Statistical model:**

`~ cell_line + treatment`

The treatment comparison is dexamethasone versus untreated, with untreated as the reference condition. Statistical significance is assessed using an adjusted p-value threshold of 0.05.

**Results validation status:**

The recreated analysis reported 3,974 significant genes, compared with 3,541 reported in the original project README. This discrepancy remains unresolved. The recreated results and volcano plot are therefore considered provisional pending further investigation.

**Project folder:** `RNA-seq/`

[View RNA-seq Differential Expression Capstone](RNA-seq/README.md)

---

### Capstone 2 — Variant Annotation Workflow

**From VCF Record to Evidence-Based Interpretation**

This project demonstrates a trio-based variant annotation and prioritisation workflow using genomic variant data from a mother, father and proband.

**Key components:**

- VCF normalisation using bcftools
- Functional annotation using SnpEff
- Family-based variant filtering using GEMINI
- Autosomal recessive inheritance-pattern assessment
- Candidate variant prioritisation
- Population frequency assessment using gnomAD
- Clinical database review using ClinVar and dbSNP
- Biological interpretation and evidence assessment
- Limitations and reproducibility

**Prioritised candidate:**

- **Gene:** CA2
- **Variant:** chr8:86385980 G>A (GRCh37/hg19)
- **Corresponding GRCh38 coordinate:** chr8:85473751
- **dbSNP:** rs1173332839
- **Predicted consequence:** stop_gained
- **Impact:** HIGH

The candidate is retained as a preliminary finding based on its predicted consequence, trio genotype pattern and population-frequency evidence. Further clinical and functional validation is required.

**Project folder:** `Variant-Annotation/`

[View Variant Annotation Capstone](Variant-Annotation/README.md)

---

## Tools and Technologies

| Category | Tools |
|---|---|
| Statistical analysis | R |
| Programming and data analysis | Python |
| RNA-seq differential expression | DESeq2 |
| Variant normalisation | bcftools |
| Functional variant annotation | SnpEff |
| Variant prioritisation | GEMINI |
| Population frequency database | gnomAD |
| Variant database | dbSNP |
| Clinical database | ClinVar |
| Workflow environment | Galaxy |
| Version control | Git and GitHub |

---

## Repository Structure

```text
Week-8-Capstone/
│
├── README.md
│
├── RNA-seq/
│   ├── README.md
│   ├── dataset_description.md
│   ├── qc_assumptions.md
│   ├── deseq2_workflow.md
│   ├── PCA_treatment.png
│   ├── heatmap_top30_DE_genes.png
│   ├── volcano_plot.png
│   ├── full_DESeq2_results.csv
│   ├── top20_differential_expression.csv
│   ├── GO_enrichment_results.csv
│   ├── top20_GO_terms.csv
│   ├── biological_interpretation.md
│   └── limitations_and_reproducibility.md
│
└── Variant-Annotation/
    ├── README.md
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

---

## Learning Outcomes

Through these capstone projects, the following bioinformatics skills were applied:

- Analysis and interpretation of high-throughput sequencing data
- RNA-seq differential expression analysis
- Statistical interpretation of gene expression results
- Data visualisation using PCA, heatmaps and volcano plots
- Functional enrichment analysis
- Genomic variant processing and annotation
- Inheritance-based variant prioritisation
- Population frequency and clinical database evidence assessment
- Biological interpretation of computational findings
- Documentation and organisation of reproducible workflows using GitHub

---

## Project Status

| Project | Status |
|---|---|
| RNA-seq Differential Expression Analysis | Documentation and results available; validation discrepancy pending |
| Variant Annotation Workflow | Computational workflow, candidate review, results and evidence documented |

**Week 8 — Two bioinformatics capstone projects.**

These projects demonstrate the application of computational and analytical approaches to RNA-seq differential expression analysis and evidence-based genomic variant prioritisation. All interpretations are presented within the limitations of the available data and supporting evidence.

The findings are intended for research and educational purposes and do not represent clinical diagnostic interpretations.
