# Loops
One of the most useful aspects of bash is its ability to glue together the many useful and varied unix tools - we've already seen pipes and redirection in the previous scenario. Using loops helps automate away many of the tedius and repetitive tasks we have to do on a computer!

There are three types of loops:
- *For* loops run a command as it goes through each element of a list or range.
- *While* loops run commands while a condition is true
- *Until* loops run commands until a condition is met

## For loops
A for loop takes iterates over a list of words, in the following form:

```
for var in list;
do
    command $var
done
```

As you type the command, you can press enter and bash will keep the same prompt until the loop is closed, or you can use ';' to split commands instead of new lines to keep everything on a single line.


An example that echos the file name and first few lines of the given files:
```
files="Arabidopsis_thaliana.TAIR10.dna.chromosome.1.fa.gz Arabidopsis_thaliana.TAIR10.dna.chromosome.2.fa.gz"
for value in $files
do
    echo $value
    zcat $value | head
done
```{{execute}}

```zcat``` is just the same as ```cat```, but works on compressed (.gz) files.

Having to predefine the file names we want to look at in a variable probably takes even more time than just running the command without a loop. In the next section we will see how to use brace expansion and command substitution to speed things up, but first we will look at a ```while``` loop, which is capable of using ```read``` to iterate through a piped input.

## While loops

A while loop takes the following form:

```
while [ condition ];
do
    command
done
```

To view the first few lines of each file, similarly to above, we could use ```ls``` to list our files, and then pipe it to the while loop.

```
ls *.fa.gz | while read value;
do
    echo $value
    zcat $value | head
done
```{{execute}}


