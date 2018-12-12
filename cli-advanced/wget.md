# Downloading data
To set us up for the next few sections, let's download some data files.

*wget* is a tool for downloading files through HTTP or FTP. It can be used to download entire websites or download multiple files matching a pattern. For now, we will just use it to fetch C. elegans genome files from the UCSC FTP.

```mkdir c_elegans```{{execute}}
```cd c_elegans```{{{execute}}
```wget ftp://hgdownload.cse.ucsc.edu/goldenPath/ce11/chromosomes/*```{{execute}}


