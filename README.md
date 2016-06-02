# Genomic Origin Through Taxonomic CHAllenge (GOTTCHA)

GOTTCHA is an application of a novel, gene-independent and signature-based metagenomic
taxonomic profiling method with significantly smaller false discovery rates (FDR) that is 
laptop deployable. Our algorithm was tested and validated on twenty synthetic and mock 
datasets ranging in community composition and complexity, was applied successfully to data
generated from spiked environmental and clinical samples, and robustly demonstrates 
superior performance compared with other available tools.

-------------------------------------------------------------------
## SYSTEM REQUIREMENT

Linux (2.6 kernel or later) or Mac (OSX 10.6 Snow Leopard or later) operating system
with minimal 8 GB of RAM is recommended. Python 3.0+ is required. The C/C++
compiling enviroment might be required for installing dependencies. Systems may vary.
Please assure that your system has the essential software building packages (e.g. build-essential
for Ubuntu, XCODE for Mac...etc) installed properly before running the installing 
script.

-------------------------------------------------------------------
## INSTRUCTIONS

```
usage: gottcha.py [-h] (-i [FASTQ] [[FASTQ] ...] | -s [SAMFILE])
                  [-d [BWA_INDEX]] [-l [LEVEL]] [-pm <INT>]
                  [-m {summary,full,tree,class,extract}] [-x [TAXID]]
                  [-r [FIELD]] [-t <INT>] [-o [DIR]] [-p <STR>] [-mc <FLOAT>]
                  [-mr <INT>] [-ml <INT>] [-c] [-v]
```
Genomic Origin Through Taxonomic CHAllenge (GOTTCHA) is an annotation-
independent and signature-based metagenomic taxonomic profiling tool that has
significantly smaller FDR than other profiling tools. This program is a
wrapper to map input reads to pre-computed signature databases using BWA-MEM
and/or to profile mapped reads in SAM format. (VERSION: 2.0 Beta)

optional arguments:

```
-i [FASTQ] [[FASTQ] ...], --input [FASTQ] [[FASTQ] ...]
```
Input one or multiple FASTQ file(s). Use space to separate multiple input files.
```
-s [SAMFILE], --sam [SAMFILE]
```
Specify the input SAM file. Use '-' for standard input.
```
-d [BWA_INDEX], --database [BWA_INDEX]
```
The path of signature database. The database can be in FASTA format or BWA index (5 files).
```
-l [LEVEL], --dbLevel [LEVEL]
```
Specify the taxonomic level of the input database. You can choose one rank from "superkingdom", "phylum","class", "order", "family", "genus", "species" and "strain". The value will be auto-detected if the input database ended with levels (e.g. GOTTCHA_db.species).
```
-pm <INT>, --mismatch <INT>
```
Mismatch penalty for BWA-MEM (pass to option -B while BWA-MEM is running). You can use 99 for not allowing mismatch in alignments (except for extreme cases). [default: 5]
```
-m {summary,full,tree,class,extract}, --mode {summary,full,tree,class,extract}
```
You can specify one of the following output modes:
    -   "summary" : report a summary of profiling result;
    -   "full" : other than a summary result, this mode will report unfiltered profiling results with more detail;
    -   "tree" : report results with lineage of taxonomy;
    -   "class" : output results of classified reads;
    -   "extract" : extract mapped reads; Note that only results/reads belongs to descendants of
TAXID will be reported/extracted if option [--taxonomy TAXID] is specified. [default: summary]
```
-x [TAXID], --taxonomy [TAXID]
```
Specify a NCBI taxonomy ID. The program will only report/extract the taxonomy you specified.
```
-r [FIELD], --relAbu [FIELD]
```
The field will be used to calculate relative abundance. You can specify one of the following fields: "LINEAR_LENGTH", "TOTAL_BP_MAPPED", "READ_COUNT" and "LINEAR_DOC". [default: LINEAR_DOC]
```
-t <INT>, --threads <INT>
```
Number of threads [default: 1]
```
-o [DIR], --outdir [DIR]
```
Output directory [default: .]
```
-p <STR>, --prefix <STR>
```
Prefix of the output file [default:<INPUT_FILE_PREFIX>]
```
-mc <FLOAT>, --minCov <FLOAT>
```
Minimum linear coverage to be considered valid in abundance calculation [default: 0.005]
```
-mr <INT>, --minReads <INT>
```
Minimum number of reads to be considered valid in abundance calculation [default: 3]
```
-ml <INT>, --minLen <INT>
```
Minimum unique length to be considered valid in abundance calculation [default: 60]
```
-c, --stdout
```
Write on standard output.
```
-v, --verbose
```
Enable verbose output
```
-h, --help
```
show this help message and exit