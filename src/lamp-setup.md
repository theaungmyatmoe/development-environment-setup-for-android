# LAMP Stack Setup

> **LAMP** stand for **L**inux,**A**pache Web Server,**M**ySQL Database and **P**HP.

# pkg

`pkg` to use `apt` package manager more eaiser.

# Installation of LAMP Dependencies

```sh
pkg up # upgrade the system

pkg i php apache2 php-apache mariadb # install the dependencies
```

`php` - for  PHP Interpreter

`apache2` - for Apache Web Server

`php-apache` - is a `PHP` module for Apache

`mariadb` - alternative of `MySQL`

# Setting Up The PHP and Apache

When the installion is finished, we will change some config file of `Apache`.
So,change to the `Apache`'s config directory.

```sh
cd $PREFIX/etc/apache2/conf.d
```

Create the `php.conf` config file.

```sh
nano php.conf
```

Add the following source code to load the `PHP` module from `$PREFIX/libexec/apache2/libphp.so` and save it.

```conf
LoadModule php_module libexec/apache2/libphp.so
<FilesMatch \.php$>
   SetHandler application/x-httpd-php
</FilesMatch>
<IfModule dir_module>
    DirectoryIndex index.php
</IfModule>
```
<file>php.conf</file>

We will include the new config file to the `httpd.conf`.

```sh
cd $PREFIX/etc/apache2
nano httpd.conf
```

Go to the end of `httpd.conf` file and remove `#`.

**Note** - `#` is a comment.

```conf
#Include etc/apache2/conf.d/*.conf
```
<file>httpd.conf</file>

Find the `worker` module of `PHP` that does not need for us.

<kbd>CTRL+W</kbd> and type `worker` and <kbd>Enter</kbd>.

```conf
LoadModule mpm_worker_module libexec/apache2/mod_mpm_worker.so
```
<file>php.conf</file>

Add `#`.

```conf
LoadModule mpm_worker_module libexec/apache2/mod_mpm_worker.so
```

Find `prefork` module and remove `#`.

```conf
#LoadModule mpm_prefork_module libexec/apache2/mod_mpm_prefork.so
```
<file>php.conf</file>

When we did the setting up of the config files, we will need to restart the `Apache`.

```sh
apachectl restart # restart the Apache Server
```

If we got the following error,

```sh
~ apachectl restart
httpd not running, trying to start
```
Start the `Apache` Server.

```sh
apachectl start # to start the server
apachectl restart # to restart the server
```

By default,Apache Server is running on `localhost:8080` (or) `127.0.0.7:8080`.

To stop the Apache just run the following command.

```sh
apachectl stop # to stop the Apache
```

If you got the servername error open `httpd.conf` file and search `ServerName` and edit like below.

```conf
ServerName localhost:8080
```
<file>php.conf</file>

Restart the server and try again.

Open Browser and search the address `localhost:8080` you will see `It work!`.It is the default page of `Apache`. We can change the server's root directory.

Open `httpd.conf` and search the `DocumentRoot` and change the server's directory like below.

```conf
DocumentRoot "/sdcard/htdocs"
<Directory "/sdcard/htdocs">
```
<file>php.conf</file>

`/sdcard/htdocs` - is a directory in the **Internal Storage** of Android device.

You can edit the directory path any time what you like but you must not add the `/` at the foreward of closing double quote.

You will need to mount the internal storage by running this command.

```sh
termux-setup-storage # mount the internal storage
```

Create the new directory named `htdocs` in the internal storage and create a new php file like below.

```bash
cd /sdcard/htdocs # go to the htdocs that is under the internal storage
echo "<?php echo 'Hello World!' ?>" > index.php 
```

Restart the server and search `localhost:8080` in the browser and you will see `Hello World!`.

# Rewrite Rule

Sometime,we will need to use `.htaccess` to rewrite the `cgi scripts`.So,we should open the `rewrite` module of apache.

Find `Rewrite Module` and remove `#`.

**`httpd.conf`**

```conf
#LoadModule rewrite_module libexec/apache2/mod_rewrite.so
```

# Setting Up The MySQL

To start the `mysql` just run the following command.

```sh
mysql # to start the mysql server
```

So,we got the following error.

```sh
~ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/data/data/com.termux/files/usr/tmp/mysqld.sock' (2)
```

Run the following command to start the `MySQL` server.

```sh
mysqld_safe # to start mysql  server
```

Open new terminal and run `mysql` command again.

To stop the `Mariadb` server just run the following command.

```sh
killall -9 mysqld_safe
```

If above command is not work, you can use the following command.

```sh
kill $(ps aux | grep '[m]' | awk '{print $2}')
```

# Create `root` Priviliage for MySQL

Run `Mariadb` and just type the `SQL` commands.

```mysql
CREATE USER 'root' IDENTIFIED BY '';
GRANT ALL ON db.* TO root@localhost IDENTIFIED BY '';
FLUSH PRIVILEGES;
```

Default port of `mysql` is `3306`.

When you want to connect with backend programming language you should know the following adresses.

- **Host** - `localhost:3306` (or) `127.0.0.1:3306`
- **User Name** - `root`
- **Password** - `''`