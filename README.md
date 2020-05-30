# sarks_examples

__SArKS__ (Suffix Array Kernel Smoothing) is an algorithm for
identifying sequence motifs correlated with numeric scores (such as
differential expression statistics from RNA-seq experiments). The
paper describing the algorithm may be found at:

https://academic.oup.com/bioinformatics/article-abstract/35/20/3944/5418797

A preprint of the article is also available on biorxiv at:

https://www.biorxiv.org/content/early/2018/10/25/133934

The R version of SArKS is also available via the Bioconductor package
``sarks``:

https://bioconductor.org/packages/release/bioc/html/sarks.html

## Installation 

SArKS is implemented in Java (1.8 or greater) with interactive use
facilitated through an R package built using
[**rJava**](https://cran.r-project.org/web/packages/rJava/index.html).

Once these dependencies have been installed and correctly configured,
you can install ``sarks`` by running the following code within an R
session:

```R
if (!requireNamespace("BiocManager", quietly=TRUE)) {
    install.packages("BiocManager")
}
BiocManager::install("sarks")
```

### Alternative installation: Java only

1. Copy sarks.jar from this repository to convenient location

2. Test the installation by going through the simulated data example
   using sarks.jar as described below

## Using sarks

This project implements the SArKS algorithm in the java package
contained in sarks.jar, which can also be run as part of the R package
sarks.

### Using the R package sarks

For most users, we would recommend trying out the R package, which can
be installed as described above.

The sarks vignette is the best place to start to learn how to use the
R version of sarks; you can find it by running

```R
library(sarks)
browseVignettes("sarks")
```

once you have ``sarks`` installed from Bioconductor.

### Direct command-line usage of jar file

For detailed information on command-line usage of sarks.jar and
associated scripts, consult [user_guide.md](user_guide.md).

The best way to learn how to use sarks is to read through the example
scripts (markdown versions of each of the examples are available as
well) included in this github repository.

These examples are taken from the data sets analyzed in the SArKS
paper, including the toy simulated data set as well as the analyses of
the upstream (5' of transcription start site) and downstream (3' of
transcription start site) DNA regions for mouse genes whose expression
profiles were quantified in the study:

- Mo, Alisa, et al. "Epigenomic signatures of neuronal diversity in the
  mammalian brain." Neuron 86.6 (2015): 1369-1384.

### Simulated data example

The simulated data set consists of the 30 sequences contained in

- simulated_seqs.fa

together with the associated scores contained in

- simulated_scores.tsv

The file

[simulated_example.md](simulated_example.md)

uses the utility scripts also contained herein to analyze these
sequences and scores.

I recommend reading through the example and running the commands
contained within individually at the command line as you get to them.

### Mo 2015 downstream example

After going through the simulated example, try sarks out on the Mo
2015 downstream seqs. An example of how to do this can be found in the

[mo2015\_downstream\_example.md](mo2015_downstream_example.md)

file; again I would recommend reading through the example and running
the commands line-by-line as you get to them.

### Mo 2015 upstream example

The [Mo 2015 upstream example](mo2015_upstream_example.md) is
similar to the downstream example but
1. runs on a larger data set and
2. uses a few more SArKS features, including spatial smoothing.

As a result this example will take more time to run and require more
memory than the other examples included.
