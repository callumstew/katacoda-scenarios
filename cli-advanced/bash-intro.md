# Bash introduction

As a programming language, bash has variables - named references to stored numbers or characters.

We can assign a variable using '=', with the variable name on the left and the value to store on the right.

`VAR='Hello World'`{{execute}}

The value can then be accessed by prepending a '$' to the variable name:

`echo $VAR`{{execute}}

or optionally surrounding it in curly braces - {} - which is useful when following the variable directly with other characters, which would otherwise be confused as part of the variable name:

`echo ${VAR}s`{{execute}}

`echo $VARs`{{execute}}

# Limited variable manipulation
In some cases text manipulation may be more easily achieved through bash directly, rather than sed or awk. Bash includes a number of inbuilt variable manipulations, including:

- Changing case

    `echo ${VAR,}`{{execute}}

    `echo ${VAR,,}`{{execute}}

    `echo ${VAR^}`{{execute}}

    `echo ${VAR^^}`{{execute}}

- Sub-string removal - Use # to match a pattern from the beginning, and % to match a pattern from the end.

    `echo ${VAR#Hel}`{{execute}}

    `echo ${VAR%World}`{{execute}}

    `echo ${VAR#World}`{{execute}}

- Substitution - Use / to replace the first instance or // to replace all instances of a pattern. Particularly useful when renaming things

    `echo ${VAR/o/e}`{{execute}}

    `echo ${VAR//o/e}`{{execute}}


# Environmental variables
Your computer will have various environmental variables already set. Of particular use are '$HOME', a variable pointing to the current users home directory, and $PATH, a variable containing all the paths that bash will look for programs on. Often $PATH must be added to when a user installs a program themself. e.g.
`PATH=$PATH:$HOME/bin` would allow you to run programs from a 'bin' folder in your home directory when you are working in any other directory.
