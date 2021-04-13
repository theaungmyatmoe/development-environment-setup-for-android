# Developement Environment Setup For Android Device

> If someone said "You can do nothing on Android bla bla ..." to you ,you have to say him/her like that "Go fuck yourself 👀".
>
> ~ Aung Myat Moe

# What is this?

This is a manual for setting up the devlopement environment in Android Linux.

This manual is related with [🐈🐾 - `meow`](https://github.com/amm834/meow.git) advanced package manager for Android Linux.


# `Node.js`

```sh
# Recommend 
pkg i nodejs

# Alternatively
pkg install nodejs-lts
```

Check the versions of `node.js` and `npm`.

```sh
node -v && npm -v
v14.15.4
7.6.1
```

Alternatively,you can use yarn as node package manager.

```sh
# `yarn` installation
pkg i yarn
```

# `MongoDB`

MongoDB is not officially support for `aarch64` and some others CPUs of Android.

## Install via `dpkg`

```sh
# Install mongo via `dpkg`
# This debian format file can only run on `aarch64` CPU
dpkg -i mongodb_4.2.9_aarch64.deb
```

## Install via `pkg`

First we need to download `itspointless` repo's `setup.sh` file to setup the environment.

```sh
#  Download `setup-pointless-repo.sh` file
wget https://its-pointless.github.io/setup-pointless-repo.sh

# Setup the environment
bash setup-pointless-repo.sh
```

And we will need to install `mongodb` package.

```sh
# Install `Mongodb`
pkg i mongodb
```
When installation is finished,we need to create path to store data of `MongoDB`.

```sh
# Setup storage directory MongoDB
mkdir $PREFIX/ data
mkdir $PREFIX/data db
```
Testing the `mongodb`.

```sh
# Test mongodb
mongod --version

db version v4.1.13
git version: nogitversion
OpenSSL version: OpenSSL 1.1.1i  8 Dec 2020
allocator: system
modules: none
build environment:
    distarch: aarch64
    target_arch: aarch64
```

If you face some libary errors like below,you will need to compile or download all library files from `libraries/aarch64/icu`.

```sh
# Mongo library error
CANNOT LINK EXECUTABLE "mongod": library "libicudata.so.67" not found 
```

Move all downloaded files to `$PREFIX/lib`.

```sh
mv *.so $PREFIX/lib
```

Manually complilation is  not required when you download libraries files from `libraries/aarch64/icu` but compiled files are only for `aarch64` CPU.
If your CPU is not `aarch64` you should not download it because it is not work for other CPUs.

## Compile The `icu` Library Manually

```sh
# Install related packages
pkg i clang cmake python -y

# install `libicu67` from source code
wget https://github.com/unicode-org/icu/releases/download/release-67-1/icu4c-67_1-src.tgz

# Extract (Unzip) `tar` archieve
tar -xf icu4c-67_1-src.tgz

cd icu/source

# Make rules 
./configure --prefix=$PREFIX

# Check  dependencies are exist or not (it will take some time)
make

# Set `DESTDIR` global variable for `cmake`
export DESTDIR=/data/data/com.termux/files

# Compile the source code of `icu` via `make`
make install

cd lib # `lib` directory stores compiled executable files

# Move all compiled executable files to Termux base `lib` directory because Termux stores shared libary data under `$PREFIX/usr/lib` directory
mv * $PREFIX/usr/lib 

# Start the `mongodb` server
mongod
```

Open new Session via Termux's left sidebar (or) <kbd>CTRL+T</kbd>.

```sh
# Connect with `mongodb` Client
mongo
```

Let's test the `mongodb`.

```sh
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
travel  0.000GB
>
```