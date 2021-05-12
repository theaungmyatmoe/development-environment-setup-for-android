# chmod

> `chmod` to manage permission of files and folders.

#  Permissions
Generally,there are three permissions -

-  read
-  write
-  execute

# Give All Permission

Assum that we have `hello.txt`.
We want to give all of the permission to owner and others.
We just need to run like below.


```sh
chmod a+rwx hello.txt
```


# Individually

## Read Access
```sh
chmod +r hello.txt
```

## Write Access
```sh
chmod +w hello.txt
```
## Execute Access

```sh
chmod +x hello.txt
```

# Remove The Permission

## Remove Read Access
```sh
chmod -x hello.txt
```

## Remove Write Access

```sh
chmod -w hello.txt
```

## Remove Execute Access

```sh
chmod -w hello.txt
```

## Remove All Of Them

```sh
chmod a+rwx hello.txt
```

# How to Change Permissions in Numeric Code in Linux

You may need to know how to change permissions in numeric code in Linux, so to do this you use numbers instead of “r”, “w”, or “x”.

- 0 = No Permission
- 1 = Execute
- 2 = Write
- 4 = Read
- 
Basically, you add up the numbers depending on the level of permission you want to give.

Permission numbers are:

- 0 = ---
- 1 = --x
- 2 = -w-
- 3 = -wx
- 4 = r-
- 5 = r-x
- 6 = rw-
- 7 = rwx
 

For example:

`chmod 777 foldername` will give read, write, and execute permissions for everyone.

`chmod 700 foldername` will give read, write, and execute permissions for the user only.

`chmod 327 foldername` will give write and execute (3) permission for the user, w (2) for the group, and read, write, and execute for the users.