# Brace expansion
A useful element of bash is brace expansion and command subsitution. Both evaluate the contents of the parenthesis.

## Sequences
To get a sequence between two numbers or characters, you can write those two characters within curly braces and with two fullstops between them.

E.g.

```echo {1..10}```{{execute}}

```echo {a..z}```{{execute}}

By default it will return a sequence with a increment of 1. The increment can be specified by writing a third number:

```echo {1..10..4}```{{execute}}

```echo {a..z..8}```{{execute}}


Often file naming conventions are named or numbered according to some sequence, and in those cases the sequence brace expansion can come in handy.



## Lists
Characters seperated inside curly braces with commas are expanded into seperate words, which is useful when you have a long string with only minor differences.

E.g. 
```ls /{,usr/,local/usr/}bin```
The above command will list the folders /bin, /usr/bin, and /local/usr/bin. The brace expansion concatenate the surrounding text onto each of the inner strings.


## Command substitution

Sometimes we want to use the output of a command in the command we are writing, but piping and redirection is impossible or too unwiedly. Bash evaluates commands written within ``` ` ` ``` or ```$()``` before the rest of the command.

```echo "The date is: $(date)"```{{execute}}

We could rewrite our for loop from the last page as follows:

```
for value in $(ls *.fa.gz);
do
    echo $value
    zcat $value | head
done
```

The true utility of command subsitution is in the evaluation of more complex commands, which can't be replaced by a simple glob (*.fa.gz)
