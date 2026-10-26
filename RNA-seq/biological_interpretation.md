# Biological Interpretation of RNA-seq Results

## Overview

The analysis compares dexamethasone-treated and untreated human airway smooth muscle cell samples, accounting for cell-line differences in the statistical model.

## Differential Expression

The recreated DESeq2 analysis identified 3,974 genes with adjusted p-values below 0.05. The original project README reports 3,541 significant genes; this discrepancy remains unresolved, so the recreated result should be treated as provisional.

Examples of highly ranked genes in the original results include:

- MAOA
- DUSP1
- SAMHD1
- SERPINA3
- SPARCL1
- GPX3

These genes are examples from the original results table and are not, by themselves, evidence of a specific biological mechanism.

## Functional Enrichment

The original project reported enriched Gene Ontology Biological Process terms associated with:

- Actin filament organisation
- Extracellular matrix organisation
- Cell-substrate adhesion
- Small GTPase-mediated signalling
- Connective tissue development
- Responses to oxygen levels

These enriched terms provide functional context for the differentially expressed genes. Enrichment indicates over-representation of annotated processes; it does not establish causation.

## Interpretation

The original analysis suggests that dexamethasone-associated expression changes involve processes related to cellular organisation, extracellular matrix, adhesion and signalling.

These findings should be interpreted in the context of the airway smooth muscle cell model and the limited sample size.

## Status

Biological interpretation documented. The discrepancy between the original and recreated differential-expression results must be resolved before final conclusions are confirmed.
