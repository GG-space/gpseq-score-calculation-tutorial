# Requirements

First, download `GPSeq-RadiCal` with the following:

```bash
cd $HOME
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
usage: gpseq-radical.R [--] [--help] [--chromosome-wide]
       [--elongate-ter-bin] [--more-help] [--version] [--debug-info]
       [--opts OPTS] [--cinfo-path CINFO-PATH] [--ref-genome
       REF-GENOME] [--bin-tags BIN-TAGS] [--bin-bed BIN-BED]
       [--bed-outlier-tag BED-OUTLIER-TAG] [--score-outlier-tag
       SCORE-OUTLIER-TAG] [--normalize-by NORMALIZE-BY] [--site-domain
       SITE-DOMAIN] [--site-bed SITE-BED] [--mask-bed MASK-BED]
       [--chrom-tag CHROM-TAG] [--threads THREADS] [--export-level
       EXPORT-LEVEL] bmeta_path output_folder

Provide the path to a 4-columns tabulation-separated metadata file,
containing the sequencing run ID, a condition description, the library
ID, and full absolute path to each BED file (possibly gzipped) from the
GPSeq experiment. The bed files should be reported in order of
condition strength, with the top rows being *weaker* than bottom ones.
Also, the first line should contain the column headers: exid, cond,
libid, and path. An example metadata file would be is available at
https://github.com/ggirelli/GPSeq-RadiCal/blob/master/example_meta.tsv.

Fore more details, use the '--more-help' option.

positional arguments:
  bmeta_path               Path to bed metadata tsv file.
  output_folder            Path to output directory. Stops if it
                           already exists.

flags:
  -h, --help               show this help message and exit
  --chromosome-wide        Use this option to calculate also on
                           chromosome-wide bins.
  --elongate-ter-bin       Use this option to elongate
                           chromosome-terminal bins and have
                           equally-sized bins.
  --more-help              Show extended help page and exit
  -v, --version            Show script version and exit
  -d, --debug-info         Show debugging info and exit

optional arguments:
  -x, --opts               RDS file containing argument values
  -c, --cinfo-path         Path to bed file with chromsome sizes.
                           Queries UCSC if not provided.
  -r, --ref-genome         Used when --cinfo-path is not provided to
                           query UCSC. If the provided reference genome
                           is not found, reverts to 'hg38'. [default:
                           hg19]
  -b, --bin-tags           Comma-separated bin tags. Use --more-help
                           for more details. [default: 1e6:1e5,1e5:1e4]
  --bin-bed                Path to bed with regions on which to build
                           bins.
  --bed-outlier-tag        Method:threshold for input bed outlier
                           removal. [default: chisq:0.01]
  -s, --score-outlier-tag  Method:threshold for output score outlier
                           removal (rescaling). [default: iqr:1.5]
  -n, --normalize-by       Whether rescaling should be performed
                           library-wise ('lib') or chromosome-wise
                           ('chr'). [default: lib]
  --site-domain            Site domain method. Use --more-help for more
                           detail. [default: separate]
  --site-bed               Path to bed file with recognition site
                           locations for the enzyme in use. This is
                           required when using '--site-domain
                           universe'.
  -m, --mask-bed           Path to bed file with regions to be masked.
  --chrom-tag              Two values, column (:) separated: the number
                           of chromosomes, and a string with
                           comma-separated heterosome names. [default:
                           24:X,Y]
  -t, --threads            Number of threads for parallelization.
                           Optimal when using at least one core per bed
                           file. [default: 1]
  -e, --export-level       Limits the amount of output. Use --more-help
                           for more details [default: 0]
```