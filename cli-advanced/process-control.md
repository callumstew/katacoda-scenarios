# Process control
It is not always clear what processes are running. There are a few tools to display processes and resource usage.

# List processes
The ```ps``` command prints out a list of running processes, by default only those that are run by the current user and controlled by a terminal.

```ps```{{execute}}

The -A flag will list all processes running on the computer.

```ps -A```{{execute}}

There are a variety of columns that can be specified in the output format. To see usage of memory and cpu, we can use %mem and %cpu with the -o argument. A full list of possible columns can be seen in ps's man page.

```ps -A -o "pid comm %cpu %mem"```{{execute}}


# Controlling and stopping processes

## Interrupting a foreground process
Here we will use the ```sleep``` command as a stand in for some other long-running command. Command-C will send an interrupt signal (SIGINT) to the foreground process.

```sleep 8000```{{execute}}

Rather than wait 8000 seconds, press Ctrl-C to interrupt the process.

## Send a process to sleep
To pause a process and return to the command prompt, you can press Ctrl-Z. The process will pause and you will be able to type into the prompt again. 
```sleep 8000```{{execute}}

```Ctrl Z```

To resume the process and bring it back to the foreground, you can use the ```fg``` bash command:

```fg```{{execute}}


## Running a process in the background
Rather than bring it to the foreground, you can use ```bg``` to resume the process in the background

```Ctrl-Z```

```bg```{{execute}}

However, the process is still controlled by the terminal, can be brought back to the foreground using fg, and will stop if the terminal is closed.

```disown```{{execute}} will seperate the process from the terminal. This can be useful if you have run a long-running job on a remote computer, and now wish to disconnect without stopping the job.

## Stopping background processes
Now that the sleep command is disowned from the current session, we can no longer stop it with Ctrl-C. Instead we must use the ```kill <pid>``` command, which send signals to a process with id <pid>. By default, it sends the 'SIGTERM' signal, which tells the process to terminate.

We can find the pid using ps:

```ps -A | grep sleep```{{execute}}

and then run ```kill <pid>```

We could combine a few commands we have learnt to do it for us:

```kill $(ps -A -o "pid comm" | grep sleep | cut -d ' ' -f2)```{{execute}}

This will evaluate the commands in braces first, and then run kill on the output. First the pid and command name of each process is listed in two columns, grep selects only those lines that match 'sleep', and finally cut is used to extract the second (pid) column.

Sometimes programs misbehave and are unresponsive to terminate commands. If that happens, the SIGKILL signal can be sent using '-9' as a flag:

```kill -9 <pid>```

A few more user-friendly tools have been built on top of ```kill```. For instance, ```pkill``` can replace our above command and send a signal based on a process name or user directly:

```pkill sleep```
