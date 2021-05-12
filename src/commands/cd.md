# cd

> We use `cd` command to travel between directories.

# Change To Home Directory

`cd` command itself is to go to user's home.

```sh
cd 
```

We can use `cd ~` to go back home directory.


# Change To Other Directory

Assume that we have `hello` folder in our machine.We want to go under the `hello` directory.

```
cd hello
```

# Print Working Directory

We need to know where are we working under?
So, we just need to run `pwd` stand for **Print Working Directory**.

```sh
pwd
/home/hello
```

# Back To Parent Directory

We are under `hello` directory.But we want to go to parent directory of `hello` directory.

```sh
pwd
/home/hello # => `/home` is parent directory of `/hello` directory
cd .. # Go Back To Parent Directory
pwd
/home
```

# Jump To Other Directory

We can travel to other directory not going back to home directory.
Assume that we  have `hi` directory under `/home` directory.
```sh
ls
hello hi
cd hello

pwd
/home/hello
```

We just need to run `cd ~/hi` to go to the `hi` directory.

```sh
cd ~/hi

pwd
/home/hi
```

You can also use `$HOME` as `~`.