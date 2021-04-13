# Getting Start

> When you want to touch the advanced of Linux,you should know the CLI (Command Line Interface).
> When you know the CLI,you will love it.

# First Step

Open the `Termux` and then run the following commands to install the core utilities.

```sh
apt update && apt upgrade -y
```

You will need to wait some several minute that depends on your Internet Connection speed.

# Linux Package Manager

`apt` is a Linux Package Manager that can download and install the Linux Packages that are `Termux` support.

# Bash Shell

Bash is default SHELL of Termux that can run the Linux Commands.

The following command will give you the Shell that you are using.
In my case, I'm using `zsh` Shell.

```sh
echo $SHELL
/data/data/com.termux/files/usr/bin/zsh
```

# Text Editor

Text editor is very important for Linux.
Default text editor of `Termux` is `nano` text editor.
If it is not exist you can install via `apt`,in the next chapters we will use `meow` or `pkg` as a package manager

```sh
apt install nano -y
```

# Essential Commands

## `touch`

`touch` is a command that can create a file.

```sh
touch greeting.txt
```

## `ls`

`ls` is a command that will show the list of all files and directoties.

Let's check `greeting.txt` is exist or not via `ls`.

```sh
ls
greeting.txt
```

## `nano`

`nano` is a text editor that I explained above.

```sh
nano greeting.txt
```
Type some text. <kbd>CTRL+S</kbd> to save the text file.
<kbd>CTRL+X</kbd> to exist.

## `cat`

When we want to read some data from text file or source code we can use `cat` command to get data from the file.

```sh
cat greeting.txt
Hello Guys and Gals
```
`less`

You can use `less` to read data from files.

```sh
less greeting.txt
```
You can scroll to read the text.
<kbd>q</kbd> to exist.

## `tail`

You can also use `tail` to read data.

```sh
tail greeting.txt
```

## `mkdir`

`mkdir` is a command  that can create a new directoty.

```sh
mkdir hello

ls # list all files and dirs
greeting.txt
hello
```

## `mv`

`mv` is a command that can move files and directoties.

```sh
mv greeting.txt hello

ls # list files & dirs
hello

ls hello # list files from hello directory
greeting.txt
```

## `cd`

`cd` stand for `Change Directory` that can change to another directory.

```sh
cd hello
```

## `pwd`

`pwd` is a command that let you know where your are?

```sh
pwd
/data/data/com.termux/files/home/hello
```

