# Running in the background using nohup
Rather than having to run a process and then disown, it can be good practice to use nohup to detach a process from the onset.

```nohup sleep 5```{{execute}} will disown sleep from the terminal straight away, although nohup will still be in the foreground by default. Any output will be sent to nohup.out by default and if the terminal is closed, the process will continue.

```nohup echo "hello"```{{execute}} will write "hello" to nohup.out (```cat nohup.out```{{execute}})

Any command can be sent to the background immediately by appending '&'. Therefore, it is common to run nohup as ```nohup <commands> &```.

```nohup``` and ```disown``` are particularly useful when running commands on a remote computer, where an interruption to the network would otherwise prematurely terminate the process. ```nohup``` is more widespread because it is an official POSIX (a set of standards for UNIX systems) command, while ```disown``` is specific to bash and a few other shells.

