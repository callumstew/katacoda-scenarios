# xargs and parallel

Often a loop can be replaced with ```xargs```, a unix tool that iterates over a piped input and runs a command on it.

Using gunzip as an example command, we can uncompress each .gz file in the folder using xargs like this:

```ls *.gz | xargs gunzip```{{execute}}

Again, a simple glob would suffice here (```gunzip *.gz```).

Unix tools are often single-threaded, while any computer you are likely to use today will have multiple CPU cores. One of the advantages of xargs over a simple loop is that it can run jobs on multiple cores - drastically speeding up many tasks.

To recompress all the fasta files using two processes:
```ls *.fa | xargs -l -P 2 gzip```{{execute}}

Unfortunately the katacoda learning environment only has one core - but your actual computer will almost certainly have multiple cores.


```parallel``` is a drop-in replacement for ```xargs```, which will run jobs in parallel automatically, and has a number of extra features.
For example, it can run jobs on external computers - particularly useful when using high performance clusters, and running multiple commands or nested loops is more easily done than in xargs.
It is a program that is worth bearing in mind if you find yourself using time-consuming single-process programs. 
