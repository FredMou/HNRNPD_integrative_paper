# Metadata

Add verified tables as appropriate:

- `samples.tsv`: sample ID, assay, cell type, treatment/isoform, biological replicate and batch.
- `sequencing_files.tsv`: sample-to-file mapping, paired reads, lanes, processing status and accessions.
- `contrasts.tsv`: numerator, denominator, model, covariates, assay, cell type and analysis level.
- `references.tsv`: reference filenames, source URLs, versions and checksums.
- `input_manifest.tsv`: required inputs, download locations/accessions, checksums and consuming scripts.

Use consistent IDs across tables. Do not add identifiable donor details, credentials or confidential reviewer links.
