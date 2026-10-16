# Repository structure and upload guide

This scaffold provides destinations for checked manuscript scripts. Analysis scripts, metadata, environments and reproducibility validation have not yet been supplied.

## Uploading scripts

1. Identify the version that generated the manuscript result.
2. Put it in the matching `scripts/` subfolder. Keep distinct analyses separate; combine duplicates only after checking that outputs are preserved.
3. Use descriptive names and numeric prefixes where execution order helps. The suggested names in folder READMEs are optional conventions, not existing executable files.
4. Replace personal absolute paths with configurable paths. Remove credentials, private links and unrelated content before uploading.
5. Record inputs, parameters, dependencies and outputs. Link figure/table scripts to the final manuscript numbering.
6. Validate the checked version and document what was reproduced.

## Folder roles

| Folder | Purpose |
|---|---|
| `scripts/iclip/` | iCLIP processing, binding sites and differential binding |
| `scripts/long_read_rnaseq/` | ONT processing and differential abundance |
| `scripts/trap_seq/` | TRAP processing and differential abundance |
| `scripts/integration/` | Response lists and binding/response candidates |
| `scripts/enrichment/` | GO and KEGG analyses |
| `scripts/figures/` | Figure generation and associated motif analyses |
| `scripts/tables/` | Main and supplementary table generation |
| `scripts/lib/` | Optional shared functions |
| `config/` | Portable paths and verified analysis settings |
| `metadata/` | Samples, file mappings, contrasts, references and input manifest |
| `data/` | Input acquisition instructions and suitable small inputs |
| `example_data/` | Optional reduced or synthetic demonstration inputs |
| `environment/` | Dependency specifications and software versions |
| `docs/` | Execution instructions, provenance, figure/table mapping and validation |

## Release preparation

Retain the incomplete-release status in the root README until the workflows are supplied and verified. Add a licence only after the rights holders agree on the choice. Add citation metadata when the authorship and software-release details are established. Do not invent GEO accessions or DOIs.

The repository is currently public: newly committed scripts and results will be publicly visible. Folder placement and an in-progress status do not restrict access.
