# proccaendrexp: Process expression data generated by CaENDR
This repository contains the code used to download and process RNA-seq data generated by CaENDR (Zhang et al Nat Comms 2022).
Data processed using this code underpins the Shiny app https://wildworm.biosci.gatech.edu/cendrexp/

Cite the data:
Zhang, G., N. M. Roberto, D. Lee, S. R. Hahnel and E. C. Andersen, 2022 The impact of species-wide gene expression variation on Caenorhabditis elegans complex traits. Nat Commun 13: 3462.
https://doi.org/10.1038/s41467-022-31208-4

Cite the app:
description currently in development for MicroPublicationBiology; see https://wildworm.biosci.gatech.edu/

## App and app data details
- `app.R`: the code that runs the shiny app at https://wildworm.biosci.gatech.edu/cendrexp/. Note that this app loads a file called `cendr_rna_app_data.RData` which can be re-generated by combining the three chunked data files present here in R (when they are combined, they are too big for github hosting).
- `cendr_rna_app_data_chunk1.RData`, `cendr_rna_app_data_chunk2.RData`, and `cendr_rna_app_data_chunk3.RData` are the data files that can be combined together into the data used by `app.R`; they were created using other scripts in the repository (then chunked into 3 equally-sized chunks).

## Script details
- `downloadworkflow`: directory with nextflow workflow to use SRAToolkit to download the FASTQs, associated config, files used to run it
- `strainspectranscriptome`: directory with nextflow workflow that generates strain-specific salmon indexes. See also workflows in repo https://github.com/averydavisbell/wormstrainrnaiexpr/
- `strainspecsalmon`: directory with nextflow workflow running strain-specific salmon quantification. See also workflows in repo https://github.com/averydavisbell/wormstrainrnaiexpr/
- `cendrrnaseq2022paper_salm2vst.R`: goes from salmon quants to per-gene normalized quantifications.
Run with `--help` to see required inputs.
