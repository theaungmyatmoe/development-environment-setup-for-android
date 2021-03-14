# Developement Environment Setup For Android Device 

> If someone said to you something like that "You can do nothing in Android bla bla ..." ,you have to say him/her like that "Go fuck yourself".
>
> ~ Aung Myat Moe

## `MongoDB` Setup

This setup will need more step coz we need to compile `libicui18n.so.67` or download from 

```sh

# Install mongo via `deb` File

dpkg -i mongodb_4.2.9_aarch64.deb

# OR

#  Install from `itspointless` repo

wget https://its-pointless.github.io/setup-pointless-repo.sh

bash setup-pointless-repo.sh

# Install Mongodb

pkg i mongodb

# Setup storage directory MongoDB

# Install necessary packages

pkg i clang cmake python -y

# install `libicu67` from source code

wget https://github.com/unicode-org/icu/releases/download/release-67-1/icu4c-67_1-src.tgz

tar -xf icu4c-67_1-src.tgz

cd icu/source

# Make rules 

./configure --prefix=$PREFIX

# Check  dependencies are exist or not

make

# Set `DESTDIR` global variable 

export DESTDIR=/data/data/com.termux/files

# Compile the source code via `Make File`

make install

cd lib # `lib` directory stores compiled executable files

# Move all compiled executable files to Termux base `lib` directory because Termux stores shared libary data under `$PREFIX/usr/lib` directory

mv * $PREFIX/usr/lib 

# Starting the `mongo` server and waiting the database connections

mongod

```
Open new Session via Termux's left sidebar (or) <kdb>CTRL+T</kdb>

```sh
# Start CLI Shell of MongoDB

mongo
```
