# HNRNPD isoform binding and RNA responses

Analysis code and documentation for the HNRNPD integrative study in EndoC-βH1 and RPE cells, combining isoform-specific iCLIP-seq, long-read RNA-seq and TRAP-seq.

## Current status

This repository is being prepared to accompany the manuscript. Analysis scripts are being organised and checked against the final figures, supplementary tables and Methods. The publication release is not yet complete.

The folders below describe the intended organisation. Some folders and files may not yet be present. Instructions will be updated as the corresponding scripts are added and verified.

### Release preparation checklist

- [ ] Add the final scripts for each sequencing assay.
- [ ] Record software versions, reference files and analysis parameters.
- [ ] Document sample metadata, replicate structure and experimental contrasts.
- [ ] Reconcile the final integration input lists with the supplementary tables.
- [ ] Add scripts and input specifications for enrichment analyses and plots.
- [ ] Document execution order and expected outputs.
- [ ] Check reproducibility of the reported results.
- [ ] Add the GEO accession when assigned.
- [ ] Specify a code licence and citation information.
- [ ] Create a versioned publication release and archival DOI.

## Study overview

The study examines RNA binding by the four canonical HNRNPD protein isoforms, p45, p42, p40 and p37, and RNA responses following endogenous HNRNPD exon exclusion.

The experimental contrasts are exon 2 exclusion (ΔEx2), exon 7 exclusion (ΔEx7), and combined exon 2 and exon 7 exclusion (ΔEx2&7), each compared with the scrambled ASO control within the corresponding cell type.

The three sequencing assays provide complementary measurements:

| Assay | Analysis scope |
|---|---|
| iCLIP-seq | Reproducible binding sites and target genes for each FLAG-tagged HNRNPD isoform |
| Long-read RNA-seq | Gene- and transcript-level abundance in total RNA |
| TRAP-seq | Gene- and transcript-level abundance in ribosome-associated RNA |

Transcript-level differential abundance is distinguished from differential transcript usage. TRAP-seq abundance is also distinguished from translational efficiency relative to matched total RNA.

## Planned repository structure

```text
HNRNPD_integrative_paper/
├── README.md
├── scripts/
│   ├── iclip/
│   ├── long_read_rnaseq/
│   ├── trap_seq/
│   ├── integration/
│   ├── enrichment/
│   └── figures/
├── config/
├── metadata/
├── example_data/
├── docs/
├── environment/
├── CITATION.cff
└── LICENSE
```

`scripts/` will contain the analyses used for the manuscript. `config/` and `metadata/` will describe input paths, settings, samples and contrasts. `docs/` will document execution order and the correspondence between analyses and manuscript outputs. `environment/` will record software dependencies. A small example dataset will be provided where feasible.

## Analysis details

### Sequencing data processing

The release will include the commands and parameters used for read processing, alignment, quantification and differential abundance analysis. Reference annotations are based on GENCODE v43 and the human GRCh38 reference genome. Exact reference files and software versions will be recorded with the final scripts.

For TRAP-seq, sequencing-service preprocessing used Cutadapt version 4.9 to remove Illumina adapters, with 3′ quality trimming at Q22 and exclusion of reads shorter than 75 nucleotides after trimming. The adapter sequences and available preprocessing records will be documented with the release.

### Response-selection thresholds

The response lists used in the manuscript distinguish nominal significance from Benjamini–Hochberg (BH) adjusted significance.

| Cell type | Assay and level | Response-list threshold |
|---|---|---|
| EndoC-βH1 | Long-read RNA-seq, genes and transcripts | Nominal p < 0.05 |
| EndoC-βH1 | TRAP-seq, genes | Nominal p < 0.05 |
| EndoC-βH1 | TRAP-seq, transcripts | BH-adjusted p < 0.05 |
| RPE | Long-read RNA-seq and TRAP-seq, genes and transcripts | BH-adjusted p < 0.05 |

Nominally significant response lists are exploratory. Input-gene selection thresholds and enrichment-term significance thresholds are separate. Any additional filters used for a particular analysis will be documented in its script and configuration.

### Integration

Candidate selection is performed at gene level. iCLIP targets are grouped by the exon composition of the HNRNPD protein isoforms that bind them:

| Contrast | Exon-present binding group | Exon-absent binding group |
|---|---|---|
| ΔEx2 | p40 and p45 | p37 and p42 |
| ΔEx7 | p42 and p45 | p37 and p40 |
| ΔEx2&7 | p45 | p37 |

For each cell type and contrast, the responsive Venn input list is intersected with the corresponding binding groups. Responsive genes belonging only to the exon-present group or only to the exon-absent group are retained. The central intersection is excluded from these candidate sets.

Membership across all four isoform-binding lists distinguishes exclusive from shared binding. For ΔEx2&7, p45-not-p37 and p37-not-p45 membership does not necessarily imply exclusivity across all four isoforms.

Gene- and transcript-level response directions are annotated separately under the selected genes. Transcript annotations do not constitute a separate transcript-level binding integration.

For the integration-table display, exon-present log2 fold changes are sign-reversed to express scrambled control/exon exclusion. Exon-absent values retain exon exclusion/scrambled control. Nominal and adjusted p-values are unchanged. The release will preserve the original comparison and identify any displayed reversal.

These groups identify binding-associated responsive candidates rather than proving direct regulation by an individual HNRNPD isoform.

### Functional enrichment and figures

The release will document GO and KEGG over-representation analyses, including gene-identifier mapping, input groups, background definitions, database versions and multiple-testing correction. Plotting scripts will be linked to the corresponding manuscript figures and supplementary tables.

## Reproducing the analyses

Execution instructions are being prepared. Each released workflow will specify its required inputs, dependencies, commands and expected outputs. The intended sequence is assay-specific processing and differential analysis, followed by gene-level integration, enrichment and figure generation.

## Data availability

Sequencing-data deposition in GEO is in progress. The accession and links to processed data will be added when available. Raw sequencing files will be distributed through the appropriate data repository rather than stored in this GitHub repository.

## Manuscript and citation

The manuscript citation and DOI will be added when available. The final publication code release will be identified by a release tag and, when available, an archival DOI.

## Maintainer

Maintained by Zhuofan Mou ([FredMou](https://github.com/FredMou)).

This README will be updated as the analysis files and supporting documentation are added.
