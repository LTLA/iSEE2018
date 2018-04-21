# Interactive visualization with iSEE

This repository contains the code required to construct the tours described in the _iSEE_ paper by Rue-Albrecht _et al._

**Note:** these tours can be resumed from within their respective iSEE application instance, using the _question mark_ icon in the top-right corner of the _Shiny_ application.

# Setting up the tours

## TCGA

This tour is launched by the `tcga_app.R` script.
The only pre-requisite to run this script is that the current working directory is set to the `tours/` folder.

The script fetches the TCGA data set from the Bioconductor [ExperimentHub](http://bioconductor.org/packages/release/bioc/html/ExperimentHub.html) in the form of an `ExpressionSet`, and performs a small number of preprocessing steps (e.g., PCA, _t_-SNE) before launching the app and the tour.

**Note:** the first time that the script is run, it may take a few extra minutes, as it downloads and caches a copy of the data set if you haven't one already. Subsequent runs of the script will launch the tour significantly faster, as they will use the locally cached data set. Refer to the documentation of the [ExperimentHub](http://bioconductor.org/packages/release/bioc/html/ExperimentHub.html) for further details.

## PBMC 4K

This is somewhat more involved as the relevant data, while publicly available, need to be processed and analyzed.
This can be achieved by following these steps:

1. Download and unpack the PBMC 4K dataset from the [10X Genomics website](http://cf.10xgenomics.com/samples/cell-exp/2.1.0/pbmc4k/pbmc4k_raw_gene_bc_matrices.tar.gz).
2. Run the [analysis script](https://github.com/MarioniLab/EmptyDrops2017/tree/master/analysis/pbmc4k/analysis.Rmd).
Modify the `fname` variable according to the path to the unpacked PBMC data files.
3. Move the generated `sce.rds` object into `tours/` and run `pbmc4k_app.R`.
