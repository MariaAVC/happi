
<!-- README.md is generated from README.Rmd. Please edit that file -->

# HAPPI <img src="vignettes/logo.JPEG" align="right" width="165px"/>

<span style="font-family:Arial; font-size:10em;"> `happi`: a
**H**ierarchical **Ap**proach to **P**angenomics **I**nference</span>

## What is `happi`?

`happi` is a method for modeling gene presence in pangenomics that
leverages information about genome quality to improve inference. `happi`
models the association between an experimental condition and gene
presence where the **experimental condition** is the **primary
predictor** of interest and **gene presence** is the **outcome** while
incorporating user-chosen information on genome quality metrics
(e.g. mean coverage, contamination, completion, etc…).

You might be interested in using `happi` to conduct your pangenomics
hypothesis testing if you work with fragmented genomes such as
metagenome assembled genomes (MAGs). `happi` is currently distributed as
an `R` package and can be installed using the instructions below.

## Where does `happi` fit into my workflow?

If you’re new to shotgun metagenomics we understand that things can feel
overwhelming! On top of all the tools and names floating around you’re
probably wondering where does `happi` fit into the vast suite of
bioinformatics tools for metagenomics data and how can you use it in
your work? `happi` can be used *after* you have assembled, binned,
annotated, and refined your genomes or metagenome-assembled genomes
(MAGs) and as such it can be used with any bioinformatics workflow that
conducts assembly, binning, annotation, and refinement.

We highly recommend checking out Mike Lee’s
[resources](https://astrobiomike.github.io/genomics/) on genomics to
orient yourself to the breadth of metagenomics tools for building a
bioinformatics pipeline/workflow from raw reads to assembled genomes. We
recommend spending time to understand the pros and cons of the tools
you’re using at each step of your workflow, particularly as software and
methods continue to improve.

If you’re looking for a platform that wraps a lot of these tools into
its code base to conduct assembly, binning, annotation, and refinement
of MAGs we suggest checking out the [anvi’o](https://anvio.org)
platform: metagenomics workflow
[here](https://merenlab.org/2016/06/22/anvio-tutorial-v2/) and
pangenomics workflow
[here](https://merenlab.org/2016/11/08/pangenomics-v2/). Future work for
our development team is to integrate `happi` into the anvi’o platform
for a seamless user experience. In the meantime, please refer to the
format of your data in the following data input section for what is
required to utilize `happi`.

## Installation

    if (!require("devtools", quietly = TRUE))
        install.packages("devtools") # check that devtools is installed
    devtools::install_github("statdivlab/happi", build_vignettes = TRUE) # install happi using devtools
    library(happi)

## Data Input: What data format is needed to run `happi`?

You will need two pieces of information:

1.  Information on the presence/absence of your genes in your
    MAGs/genomes; example
    [here](https://github.com/statdivlab/happi/blob/main/workflows/TM7_genes_presence_table.csv)
2.  Metadata/covariate information for the MAGs/genomes that you’d like
    to use for hypothesis testing; example
    [here](https://github.com/statdivlab/happi/blob/main/workflows/TM7_metadata.csv)

## Usage

The vignettes provide detailed information of how to use `happi` and all
its main functions through the `R` interactive session. You can follow
the vignettes by running the following code in `R`:

    utils::browseVignettes(package = "happi")

An example snakemake workflow of `happi`’s usage has been made available
under the `workflows/` folder of this github directory. To run the
example workflow you’ll need to install snakemake. We recommend creating
a conda environment with your snakemake installation:

    conda install -n base -c conda-forge mamba
    conda activate base
    mamba create -c conda-forge -c bioconda -n snakemake snakemake

You can activate your snakemake conda environment and check it:

    conda activate snakemake
    snakemake --help

Once your snakemake has been installed in a conda environment and
activated you can download the contest in the `workflows/` folder and
run the following to execute the workflow from within the folder:

    snakemake --cores 6

The Snakefile is customizable for your own input data and parameters.
Please refer to the sample data files that have been provided in
`workflows` for formatting of your input data.

## How do I export data from anvi’o for use in `happi`?

## Citation

If you use `happi` please cite our work:

An open-access preprint is available
[here](https://www.biorxiv.org/content/10.1101/2022.04.26.489591v1.full).

## Issues/Requests

If you have any issues using our software or further questions please
submit an issue [here](https://github.com/statdivlab/happi/issues).
