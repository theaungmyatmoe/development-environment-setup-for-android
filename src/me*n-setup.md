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

> Mongo is not working correctly at this moment.
> We only have a potential solution as follow:

to install your favourite Linux distribution like Ubuntu in termux (in bottle installation) .

Please use, **Andronix - Linux on Android** (instructions to install your favorite Linux distribution) or you can install arch Linux by following termux documentation.

https://wiki.termux.com/wiki/PRoot#Installing_Linux_distributions

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
mkdir -p /data/data/com.termux/files/usr/data/db
```

**Check Work Well or Not**

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

If work test like below.

```sh
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

If you face libiary error,check the link below.

[Common Errors of Mongo DB](common-errors/mongodb.md)
