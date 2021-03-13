# Developement Environment Setup For Android Device 


## `MongoDB` Setup In Android

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

# install libicu67 from code.

wget https://github.com/unicode-org/icu/releases/download/release-67-1/icu4c-67_1-src.tgz

tar -xf icu4c-67_1-src.tgz

cd icu/source

./configure --prefix=$PREFIX

make

export DESTDIR=/data/data/com.termux/files

make install

cd lib
mv * $PREFIX/usr/lib

mongod

# Open new Session (CTRL+T)

mongo

```