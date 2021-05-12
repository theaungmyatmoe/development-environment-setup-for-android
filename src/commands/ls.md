# ls

> We use `ls` when we wnat to know the list of files (or) folders.

# Listing Files

List all normal files and folders.

```sh
ls
```

List of normal files and folders including hidden files and folders startimg with dot `.`.

```
ls -a
```

# Long List Format

We can use `ls -l` to show files with long list format.

```sh
ls -l
```

# Human Readable Format

We can use `-h` option to list files as human readable format.

```sh
ls -alh
```

# List Files From Individual Directory

We can use `ls <directory_name>` to list of files from `<directory_name>`.

Let's imagine we have `hello` directory.Under the `hello` directory we have `README.md` and other files.So,the directory structure of `hello` looks like below.

```
hello
└── README.md
```

We want to know the list of files under `hello` directory.
So,we just need to use `ls` command like below.

```sh
➜  ~ ls hello
README.md
```
You can add other options as you like.

# Understanding Long Format

Let's create `hello.txt` file by using `touch hello.txt`.

```sh
touch hello.txt
```

List the long format of `hello.txt` file.

```sh
ls -l hello.txt
-rw------- 1 root root 0 May 12 12:30 hello.txt
```

`-` => Indicate the file

`rw` => Read and write access for owner

`-------` => There is no access for group and other user

`root` => Owner

`root` => Group

`1` => Hardlink

`0` => File size

`May 12 12:30` => File created date

`hello.txt` => File name

You can use `apt --help` for other options.