# Getting Start

> When you want to touch the Linux,you should know Linux/Unix commands.

# First Step

Open the `Termux` and then run the following commands to install the core utils.

```sh
# install and upgrade the system
apt update && apt upgrade -y
```

You need to wait several minutes that's depending on your Internet Connection's speed.

# Linux Package Manager

`apt` is a Linux Package Manager that can download and install the Linux Packages that are supported by `Termux` matainers.

# BASH Shell

BASH is default shell of Termux that can run the Linux Commands.

The following script will give you the name of default shell that you are using.
In my case, I'm using `zsh` shell.

```sh
echo $SHELL
/data/data/com.termux/files/usr/bin/zsh
```

# Text Editor

Text editor is important for Linux especially when we are using the CLI.
Default text editor of `Termux` is `nano`.
If it is not exist you can install via `apt`.

```sh
apt install nano -y
```

# Essential Commands

## touch

`touch` is a command that can create a file.

```sh
touch greeting.txt
```

## ls

`ls` is a command that will show the list of all files and directories (folders).

Let's check the `greeting.txt` via `ls` to know it's existing or not.

```sh
ls
greeting.txt
```

## nano

`nano` is a text editor that I explained above.

```sh
nano greeting.txt
```
Type some text. <kbd>CTRL+S</kbd> to save the text file.
<kbd>CTRL+X</kbd> to exist.

## cat

When we want to read data from text file or source code we can use `cat` command to read data from the file.

```sh
cat greeting.txt # reading the file
Hello Guys and Gals
```

## less

You can also use `less` command to read data from files.

```sh
less greeting.txt
```

You can scroll down (or) up to read the text.
<kbd>q</kbd> to exist.

## tail

You can also use `tail` to read data.

```sh
tail greeting.txt
```

## mkdir

`mkdir` (Make Directory) command can create a new directory.

```sh
mkdir hello

ls # list of all files and dirs (directoties)
greeting.txt
hello
```

## mv

`mv` (stand for Move) can move files and directoties.

```sh
mv greeting.txt hello # move the greeting.txt to the hello directory

ls # list of all files and dirs
hello

ls hello # list of all files and dirs from hello directory
greeting.txt
```

## cd

`cd` (stand for `Change Directory` ) can change to another directory.

```sh
cd hello
```

## pwd

`pwd` command that let you know where is your current working directory?

```sh
pwd 
/data/data/com.termux/files/home/hello
```

