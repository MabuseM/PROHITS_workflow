# PROHITS Workflow


PROHITS Workflow is an interactive and modular visualization and filtering workflow developed for data-independent acquisition (DIA) proteomics datasets processed using DIA-NN. The workflow was implemented in the open-source KNIME Analytics Platform and was designed to support quality control, peptide- and protein-level visualization, contaminant assessment, quantitative evaluation, and group-level comparative analysis.

The framework integrates configurable filtering strategies, interactive visual components, and export-ready outputs to improve transparency, accessibility, and interpretability of proteomics datasets.

---

# Features

## Quality Control (QC)

* Protein-level QC visualizations
* Peptide precursor retention time distribution analysis
* Peptide length distribution analysis
* Peak width assessment
* Biognosys iRT peptide monitoring
* Interactive QC composites and filtering

## XIC-Based Peptide Filtering

* Consecutive b/y ion-series validation
* Automated extraction of fragment ion features
* Retention of peptides supported by ≥4 consecutive fragment ions
* Improved peptide identification confidence for DIA datasets

## Peptide-Level Analysis

* Peptide-centric export tables
* Visualization of peptides per protein
* Peptide intensity profiling
* Modification-aware peptide annotation
* m/z vs retention time scatter plots

## Protein-Level Analysis

* Protein group overlap visualization
* Interactive Venn diagrams
* Quantitative parallel coordinate plots
* Missing value profiling
* Protein abundance summaries
* Contaminant contribution visualization

## Group-Level Comparative Analysis

* Two- to five-group comparisons
* Configurable missing-value thresholds
* Relative standard deviation (RSD) filtering
* Log2 fold-change visualization
* Export-ready quantitative summaries

## Contaminant Filtering

Integrated contaminant resources include:

* MaxQuant contaminants
* cRAP contaminants
* Hao-group contaminants
* User-defined custom contaminant FASTA files

## Export and Compatibility

* MetaboAnalyst-compatible outputs
* Exportable peptide and protein tables
* Interactive summary tables
* DIA-NN quantitative integration

---

# Workflow Overview

The PROHITS workflow consists of several modular sub-workflows:

1. XICs filter
2. Library choice filter
3. Task selector
4. Quantity filter
5. QC visualization module
6. Peptide visualization module
7. Protein qualitative viewer
8. Protein quantitative viewer
9. Group-level comparative viewer

Each module was implemented using configurable dialog components to simplify workflow interaction without requiring extensive KNIME experience.

---

# Software Requirements

## Required Software

* KNIME Analytics Platform 5.4.3 or later
* DIA-NN processed output files

## Supported Input Formats

* PARQUET
* TSV
* pg.matrix
* DIA-NN XIC reports (optional)

---

# Installation

## 1. Install KNIME

Download and install KNIME Analytics Platform:

[https://www.knime.com/downloads](https://www.knime.com/downloads)

## 2. Install Required KNIME Extensions

Install all required extensions directly through KNIME:

* KNIME Python Integration
* KNIME Statistics Extension
* KNIME Plotly Extension
* KNIME JavaScript Views
* KNIME File Handling Extensions

## 3. Download DEF Workflow



## 4. Open Workflow in KNIME

* Launch KNIME Analytics Platform
* Select:

  * File → Import KNIME Workflow
* Navigate to the downloaded PROHITS workflow directory
* Import the workflow into your workspace

---

# Input Files

The workflow requires DIA-NN output files:

| Input File                       | Required | Description                       |
| -------------------------------- | -------- | --------------------------------- |
| Main DIA-NN report (PARQUET/TSV) | Yes      | Primary DIA-NN output             |
| pg.matrix                        | Yes      | Protein group quantitative matrix |
| XIC report                       | Optional | Required for XIC-based filtration |

---

# XIC-Based Filtering

To enable XIC-based peptide filtering:

1. Enable XIC export in DIA-NN
2. Import the generated XIC report into DEF
3. Activate the “XICs filter” module

The workflow extracts b- and y-ion series and retains peptides supported by at least four consecutive fragment ions.

---

# Protein Inference Strategies

The workflow supports two protein inference approaches:

## Two-Peptide Rule

* Retains proteins supported by >1 unique peptide
* Removes duplicate protein entries

## Proteotypic Peptide Strategy

* Retains proteins supported by proteotypic peptides
* Filters non-proteotypic peptide assignments

---

# Quantitative Filtering

Default quantitative thresholds:

| Metric         | Threshold |
| -------------- | --------- |
| PG.Q.Value     | ≤ 0.05    |
| Lib.PG.Q.Value | ≤ 0.01    |
| Lib.Q.Value    | ≤ 0.01    |

Protein groups failing quantity-quality thresholds are retained but assigned placeholder values to indicate non-quantified identifications.

Quantitative information is derived directly from DIA-NN quantification algorithms, including:

* MaxLFQ
* QuantUMS

---

# Visualization Modules

## Quality Control Viewer

Includes:

* Protein group identification summaries
* Peptide precursor distributions
* Peptide length distributions
* Peak width analysis
* iRT peptide monitoring

## Peptide-Level Viewer

Includes:

* Protein-specific peptide visualization
* Peptide quantity bar plots
* Modification summaries
* m/z vs retention time scatter plots

## Protein-Level Viewer

Includes:

* Interactive Venn diagrams
* Binary parallel coordinate plots
* Quantitative parallel coordinate plots
* Protein abundance summaries
* Contaminant intensity distributions

## Group-Level Viewer

Includes:

* Group mean intensity visualization
* CV% and standard deviation summaries
* Missing value filtering
* Log2 fold-change profiling

---

# Output Files

Generated outputs include:

* Protein group summary tables
* Peptide-level export tables
* Filtered quantitative matrices
* MetaboAnalyst-compatible datasets
* QC visualizations
* Quantitative summary plots

---

---

# Citation

If you use PROHITS Workflow in your research, please cite:

```text
doi:10.1021/acs.jproteome.5c01278
```

---

# License

This project is distributed under the MIT License.

---

# Acknowledgements

The DEF workflow was developed using the KNIME Analytics Platform and DIA-NN proteomics outputs.

Contaminant resources incorporated into the workflow include datasets from:

* MaxQuant
* cRAP
* Hao-group contaminant collections

---

# Contact

For workflow support, bug reports, or feature requests, please open an issue in this repository.
