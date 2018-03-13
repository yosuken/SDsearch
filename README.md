j
# HHliner - a helper tool for high sensitive HMM-HMM search against Pfam using HHsearch and JackHMMER

[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](/LICENSE)
[![size](https://img.shields.io/github/size/webcaetano/craft/build/phaser-craft.min.js.svg)]()

## requirements
* jackhmmer (HMMER3)
* hhsearch, reformat.pl (HHsuite3)
* Ruby (ver >=2.0)

## usage 
```
### HHliner ver 0.1.0 (2018-03-13) ###

[description]
HHliner - a helper tool for high sensitive HMM-HMM search against Pfam using HHsearch and JackHMMER

[reference]
HHsearch  - doi:10.1093/bioinformatics/bti125
JackHMMER - doi:10.1186/1471-2105-11-431

[usage]
$ HHliner [options]

[dependencies]
    - jackhmmer             -- included in the HMMER3 package;
                               http://hmmer.org/
    - hhsearch, reformat.pl -- included in the HHsuite package;
                               HHsuite3 - https://github.com/soedinglab/hh-suite
                               HHsuite2 - http://wwwuser.gwdg.de/~compbiol/data/hhsuite/releases/all/
    - ruby (ver >=2.0)

[options]
  (general)
    -i, --in      [path]  (required) query protein fasta file. To use multiple files as input, this value could be (1) comma-separeted file paths or (2) path of input file list (one file in one line).
                          If many proteins are included in a fasta file, adding "belongTo:" tag in comment lines to generate easy-to-understand output.  e.g. ">protein1 len:200 belongTo:contig1"
    -o, --out     [path]  (required) output directory. It should not exist.
    -J, --jackdb  [path]  (required) protein fasta file to create query HMM with query proteins, used as database sequences for JackHMMER
    -H, --hhdb    [path]  (required) Pfam database for HHsearch available here: http://wwwuser.gwdg.de/~compbiol/data/hhsuite/databases/hhsuite_dbs/
    -h, --help
    -v, --version

  (jackhmmer related)
    -N, --iter    [int]   (default: 5) number of iteration of JackHMMER serach
        --incE    [num]   (default: 0.001) inclusion threshold for sequences
        --incdomE [num]   (default: 0.001) inclusion threshold for domains

  (hhsearch related)
        --evalue  [num]   (default: 1) E-value threshold for inclusion of result table
        --pvalue  [num]   (default: 1e-5) P-value threshold for inclusion of result table
        --prob    [num]   (default: 85) %-Probability threshold for inclusion of result table

  (use GNU parallel)
        --ncpus   [int]   -- number of simaltaneous jobs

  (for icr user)          for computation in the ICR supercomputer system
        --queue   [JP1]   -- queue to calculate

[output files]
info/stats.txt                               -- number of proteins in each file
result/<input file name>/<group>/besthit.tsv -- table of HHserach besthit. Group is what is specified by the "belongTo:" tags or "ungrouped" if not provided (see description of the -i/--in option).
work/<input file name>/<group>/<protein>/    -- The directory includes all the output files of jackhmmer and hhsearch
```

## information
Prototype of this package was used in the studies below.
```
- Nishimura, Y. et al. Environmental viral genomes shed new light on virus–host interactions in the ocean.
mSphere, 2, e00359-16, doi:10.1128/mSphere.00359-16 (2017)
- Yoshida, T. et al. Locality and diel cycling of viral production revealed by a 24 h time course cross-omics analysis in a coastal region of Japan.
ISME J., doi:10.1038/s41396-018-0052-x (2018)
```
