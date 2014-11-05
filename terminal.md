%title: Use the Terminal and Become a Wizard
%author: Colin Chan
%date: 5 November 2014
% vim: tw=60:

-> # Title Slide

I wanted to have a title slide, but I don't actually have
any content for a title slide.

This is Software Development Club.

------------------------------------------------------------

-> # Why use the terminal?

It's fast.

It's powerful.

It's fun!

    $ awk <terminal.md '6<=NR && NR<13' | cowsay

------------------------------------------------------------

-> # Terminal Basics

## Prerequisites

Linux

* Use any terminal emulator.

Mac

* Use *Terminal* or install *iTerm*.

Windows

* Install *Cygwin* or use *Git Bash* (comes with Git).

------------------------------------------------------------

-> # Terminal Basics

## Very Basics

 1. Type the name of a program, maybe followed by options
    and arguments.

 2. Press enter.

 3. See the program's output appear.

 4. GOTO 1

## Getting help

Most programs have a "man page" (manual page).

    $ man head

Most programs also have a help option, commonly `-h` or
`--help`.

    $ head --help

------------------------------------------------------------

-> # Terminal Basics

## The Prompt

The _prompt_ is printed by the shell to indicate that it is
ready for you to type a command.

`$` is frequently the last character in the prompt. It is
often used in examples to signify that what follows is a
command you should type in the terminal.

Ubuntu default prompt:

    username@hostname:wd $ 

Colin's prompt:

    username@hostname:wd (gitstuff)
    [n]$ 

`wd` stands for _working directory_. We'll get to that
later.

------------------------------------------------------------

-> # Terminal Basics

## The Shell

The _shell_ is the program that reads the commands you type,
interprets them, and executes the appropriate programs.

*Bash* is most widely used and is the default shell for most
Linux distributions.

Supports lots of neat features:

* chaining programs using pipes
* redirecting program input/output to files
* ...
* 🍔

------------------------------------------------------------

-> # Terminal Basics

## Working Directories

Every process has a _working directory_. This is the
directory relative to which paths are interpreted.

* If the working directory is `/tmp` and you create a file
  called `blah.txt`, the resulting file is `/tmp/blah.txt`.

You can see your shell's current working directory using
`pwd` (print working directory).

A new process inherits the working directory of its parent
process. Processes started by the shell inherit the shell's
working directory.

A process can change its working directory. You can tell
your shell to change its working directory using `cd`
(change directory).

    $ cd /tmp       # Changes to /tmp
    $ cd            # Changes to your home directory

------------------------------------------------------------

-> # Terminal Basics

## Files, Directories, and Paths

_Files_ are organized into a hierarchy of _directories_. The
hierarchy starts with the _root directory_: `/`

A path that begins with `/` is _absolute_; a path that does
not is _relative_.

    $ wc -w terminal.md
    $ grep -i q[^u] /usr/share/dict/words

`~` is a shorthand notation for your home directory, which
is usually `/home/username`.

## Basic File Management

* move/rename: `mv`
* copy: `cp`
* remove: `rm`
* list contents: `ls`
* create directory: `mkdir`
* remove directory: `rmdir`
* print file tree: `tree` (not usually installed by default)

------------------------------------------------------------

-> # Terminal Basics

## Hidden Files

Files whose names start with `.` are _hidden files_. They
won't show up (by default) in the output of `ls`, in the
results of a _glob_ (e.g., `*.txt`), or in file listings in
most programs.

    $ ls -a   # include hidden files

## . and ..

`.` and `..` are special entries in each directory. `.`
refers to the containing directory, and `..` refers to the
parent directory.

    $ cd ..   # change to the parent dir (go "up" one level)

These act just like normal directories.

    $ ls ./././../././use_the_terminal/../use_the_terminal/

------------------------------------------------------------

-> # Terminal Basics

## File Permissions

Files are owned by both a user and a group. Often each user
has a group automatically created with the name being
his/her username.

Use `ls -l` to see the owner/group and permissions.

    $ ls -l terminal.md

Use `chown` (change owner) to change the owner/group.

    $ chown root:root terminal.md

Use `chmod` (change mode) to change the permissions.

    $ chmod ug=rw,o=r terminal.md

------------------------------------------------------------

-> # Terminal Basics

## The PATH

    $ echo $PATH
    $ env

`PATH` is an environment variable that contains a
colon-separated list of directories. When the shell needs to
execute a program, it looks in each directory listed in
`PATH` for an executable file with the program's name and
executes the first one it finds.

## Executing Programs

If the program is in one of the directories listed in
`PATH`, just type its name.

Otherwise, type a path to the program.

    $ ./test
    $ ./a.out
    $ /tmp/blah/arent-you-glad-you-have-tab-completion.py

------------------------------------------------------------

-> # Terminal Advanced

## stdout, stderr, and stdin

Every process has three file descriptors opened by default.
`stdout` and `stderr` are for output; `stdin` is for input.

Programs that are designed for use in the terminal read
their input from `stdin`, write "normal output" to `stdout`,
and write errors, debugging info, and other messages to
`stderr`.

## Pipes

A _pipe_ connects one program's `stdout` to the next
program's `stdin`.

    $ echo No capes! | wc -c
    $ echo No capes! | tr aeiou iouae

------------------------------------------------------------

-> # Terminal Advanced

## Redirection

_Redirection_ allows you to provide an actual file as
`stdin` or `stdout`.

    $ 

------------------------------------------------------------



------------------------------------------------------------

-> # Terminal Advanced

## EOF

Type `^d` to send EOF.

------------------------------------------------------------

-> # Fun Stuff

## Toilet

    $ toilet Yay, large text!
    $ toilet -f smmono12 Ooh, this is fancy.

------------------------------------------------------------

-> # Fun Stuff

## Python!

    $ python

## Really, you should learn Python.

* It's great!
* maths
* proving people wrong (or right)

## Real-life scenario

Your friend says, “Did you know that you can determine
whether a number is divisible by 11 by alternately adding
and subtracting digits from right to left; if you get 0, the
number is divisible by 11.”

You say, “Ew, nobody likes semicolons,” and then whip out
your Python interpreter to check whether he is right...

------------------------------------------------------------

-> # Fun Stuff

## Web browsing in the terminal??!

    $ w3m google.com

## Video in the terminal??!

    $ CACA_DRIVER=ncurses mplayer -vo caca -framedrop -quiet

    $ mplayer -vo aa:driver=curses -monitorpixelaspect 0.5 \
      -framedrop -quiet

------------------------------------------------------------

-> # Do you have questions?

    $ toilet -w 70 -f graffiti Do you have questions?
