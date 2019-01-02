# Terminal sessions with tmux

tmux is a terminal multiplexer - it creates a command-line session that you can enter in and out of quickly, and allows you to create 'windows' (similar to browser tabs) and 'panes' (splitting the screen into multiple prompts).

Again, this is particularly useful for remote work. Instead of having a program run detached and in the background, it can be run within tmux. It is then easy to jump in and out of tmux to continue working.

## Installation

It is typically not installed by default. Unixes normally have a package manager. One of the most common, used by Debian and Ubuntu, is apt. To install tmux with apt run the following command and press Enter when prompted for confirmation:

```sudo apt install tmux```{{execute}}}

sudo is a tool that allows you to run a command as another user. By default, it will be the administrator (root) user, which is usually necessary to install programs through a package manager.


## Starting out

To start a new tmux session, simply run tmux:

```tmux```{{execute}}

You should be able to tell you are inside a tmux session by the status bar at the bottom of the terminal. Anything run here won't be interrupted if the terminal is closed or network connection is lost. If you want to get out and have only a single pane open, you can type exit.


## Controlling tmux

### Prefix
Naturally, keys entered go to the command prompt. To control tmux, first enter the 'Prefix' key combination ```Ctrl-b```. The key entered next will be sent to tmux instead. Pressing ```:``` will allow you to enter a longer command.

### Detaching and attaching

For example, to detach from the tmux session, enter:

```Ctrl-b```
```d```

Once detached, the tmux session will continue to run along with any commands you ran inside. To view running sessions, run:

```tmux ls```{{execute}}

You likely have just one session, named 0. Tmux will use incrementing numbers to name sessions if a name is not given.

To jump back in to a particular session type:

```tmux a -t 0```{{execute}} where 0 is the name of the session.

```tmux a``` will attach to the last created session. ('tmux a' is short for 'tmux attach').

### Naming a new session
If you are inside a tmux session, detach from it again using ```Ctrl-b d```.
Numbered sessions are fine, but if we have several running at once it is nicer to have names.

To make a new named tmux session, run the following replace [name] with whatever you like:

```tmux new -s [name]```{{execute}}

```tmux ls```{{execute}} should now show our new named session.

If you were outside of it, you could reattach to that specific session using:

```tmux a -t [name]```{{execute}}


### Making windows

Windows in tmux are like tabs. After entering the prefix, the key to open a new one is ```c```:

```Ctrl-b c```

You may notice the windows are listed on the bottom status bar, with a number and then the name of the command currently running in that window. You should have two windows, likely both running bash (0: bash and 1: bash). The current window is signified by a '*'.

To switch between windows, enter the prefix and then the number of the window.

```Ctrl-b 0```

### Making panes

Windows can be split into panes.

To split a window horizontally, use ```%```:

```Ctrl-b %```

To split a window vertically, use ```"```:

```Ctrl-b "```

To switch between panes, use an arrow key in the direction of the pane you want to switch to, or use ```o``` to cycle round.

```Ctrl-b o```

### Cursor control

Mouse support is available if you would prefer to switch between windows/panes and resize panes with a cursor, but only if the terminal you are using also supports it. Most do, but because this is in a web browser we can't try it out here.
