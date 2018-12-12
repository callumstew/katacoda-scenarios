# Downloading data
To set us up for the next few sections, let's download some data files.

*wget* is a tool for downloading files through HTTP or FTP. It can be used to download entire websites or download multiple files matching a pattern. For now, we will just use it to fetch A. thaliana genome fasta files from ensembl FTP.

Make a directory to download the files into:

```mkdir c_elegans```{{execute}}

Change to that directory:

```cd c_elegans```{{execute}}


Download all files (*) in the chromosomes folder of C. elegans on UCSC:

```wget ftp://ftp.ensemblgenomes.org/pub/plants/release-41/fasta/arabidopsis_thaliana/dna/*```{{execute}}


