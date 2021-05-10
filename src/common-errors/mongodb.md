# Common Errors of Mongo DB

> Common error of Mongo DB

# ICU Libiary Error

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
```

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