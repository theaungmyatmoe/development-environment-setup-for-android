# ME*N Setup

> ME*N stand for <i>**M**</i>ongo Database, <i>**E**</i>xpress JS, <i>**N**</i>ode.JS and * will be Vue (or) Angular (or) React.

# Node.js

Install **Node JS**.

```sh
pkg i nodejs
```

Check the versions of `node.js` and `npm`.

```sh
~ node -v && npm -v
v14.15.4
7.6.1
```

Alternatively,you can use `yarn` as node package manager.

```sh
# to install `yarn`
pkg i yarn 
```

# MongoDB

MongoDB is not officially support for `aarch64` and some CPUs of Android.

First of all , we will download `itspointless` repo's `setup.sh` to install their deps (dependencies) to our environment.

```sh
#  Download `setup-pointless-repo.sh`
wget https://its-pointless.github.io/setup-pointless-repo.sh

bash setup-pointless-repo.sh
```

Install the `Mongodb` by running following command.

```sh
pkg i mongodb # to install mongodb
```

When installation is finished, create path to store data of `MongoDB`.

```sh
# setup the database storage directory for mongodb
mkdir $PREFIX/ data
mkdir $PREFIX/data db
```

**Testing**

```sh
# Test the mongodb
~ mongod --version

db version v4.1.13
git version: nogitversion
OpenSSL version: OpenSSL 1.1.1i  8 Dec 2020
allocator: system
modules: none
build environment:
    distarch: aarch64
    target_arch: aarch64
```

If you face the `icu` libary errors like below,you will need to compile library files from source code.

```sh
~ mongod
CANNOT LINK EXECUTABLE "mongod": library "libicudata.so.67" not found 
```

# Compile The `icu` Library

```sh
# install the deps
pkg i clang cmake python -y

# download `libicu67` archieve
wget https://github.com/unicode-org/icu/releases/download/release-67-1/icu4c-67_1-src.tgz

# Extract (Unzip) `tar` archieve
tar -xf icu4c-67_1-src.tgz

cd icu/source

./configure --prefix=$PREFIX

# Check  dependencies are exist or not (it will take long time be patient)
make

# Compile the source code of `icu`
make install

cd lib # `lib` directory stores compiled executable files

# Move all compiled executable files to the `$PREFIX/usr/lib` directory
mv * $PREFIX/usr/lib 

# start the `mongodb` server
mongod
```

Open new Session.

```sh
# Connect with `mongodb` Client to mongodb server
mongo
```

**Testing**

```sh
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
travel  0.000GB
>
```