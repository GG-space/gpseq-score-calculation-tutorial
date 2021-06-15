# Requirements

First, download `GPSeq-RadiCal` with the following:

```bash
wget https://github.com/ggirelli/GPSeq-RadiCal/archive/refs/tags/v0.0.6.zip
unzip v0.0.6.zip
rm v0.0.6.zip
cd GPSeq-RadiCal-0.0.6
```

`GPSeq-RadiCal` requires the following packages to run:

* `argparser`
* `data.table`
* `logging`
* `outliers`
* `pbapply`
* `rtracklayer`

If a package is missing, the script should warn the user and stop. For example, running `./gpseq-radical.R -h` without the `argparser` dependency will result in the following:

```bash
 Missing 'argparser' package.
 Install it with 'install.packages("argparser")'.
Error in FUN(X[[i]], ...) : expr is not TRUE
Calls: lapply -> FUN -> stopifnot
Execution halted
```

To install any missing dependencies, run the following in an R shell:

```R
# Basic packages
install.packages(c("argparser", "data.table", "logging", "outliers", "pbapply"))

# BioConductor packages
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install("rtracklayer")
```

If all dependencies are installed, running `./gpseq-radical.R -h` should show the following help page.

```

```