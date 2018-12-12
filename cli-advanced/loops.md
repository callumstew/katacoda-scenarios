# Loops
One of the most useful aspects of bash is its ability to glue together the many useful and varied unix tools - we've already seen pipes and redirection in the previous scenario. Using loops helps automate away many of the tedius and repetitive tasks we have to do on a computer!

There are three types of loops:
- *For* loops run a command as it goes through each element of a list or range.
- *While* loops run commands while a condition is true
- *Until* loops run commands until a condition is met

## For loops
A for loop takes the following form:

```
files="chrI.fa.gz chrII.fa.gz
for value in files
do
    echo $value
    zcat $value | head
done
```

As you type the command, you can press enter and bash will keep the same prompt until the loop is closed, or you can use ';' to split commands instead of new lines to keep everything on a single line.
