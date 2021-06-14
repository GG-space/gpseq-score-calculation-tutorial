# GPSeq score calulation example

<!-- MarkdownTOC -->

- [Introudction](#introudction)
- [Tutorial](#tutorial)
    - [Requirements](#requirements)
    - [Running GPSeq-RadiCal](#running-gpseq-radical)

<!-- /MarkdownTOC -->

## Introudction

Originally calculated with the Python package `gpseqc` ([here](https://github.com/ggirelli/gpseqc)), nowadays we generate GPSeq score tracks using the R script `GPSeq-RadiCal` ([here](https://github.com/ggirelli/GPSeq-RadiCal), faster and with lower storage/memory requirements).

## Tutorial

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

---

### Requirements

`GPSeq-RadiCal` requires the following packages to run:

* `argparser`
* `data.table`
* `logging`
* `outliers`
* `pbapply`
* `rtracklayer`

If a package is missing, the script should warn the user and stop. To install any missing dependencies, run the following in an R shell:

```R
install.packages(c("argparser", "data.table", "logging", "outliers", "pbapply", "rtracklayer"))
```

---

### Running GPSeq-RadiCal

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
