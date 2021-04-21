# LAMP Stack Setup

> LAMP stand for Linux,Apache Web Server,MySQL Database and PHP.

# `pkg`

`pkg` to use `apt` package manager more eaiser.

# Install Dependencies

```sh
->
pkg up # upgrade the system

pkg i php apache2 php-apache mariadb # install the dependencies
```

`php` - to install PHP Interpreter
`apache2` - to install Apache Web Server
`php-apache` - is a `PHP` module for Apache Web Server
`mariadb` - is a Relational Database alternative for `mysql`

# Setting Up The PHP and Apache Server 

When installion is finished,we need to change some config file of `Apache`.
So,go to the `Apache`'s config directory.

```sh
cd $PREFIX/etc/apache2/conf.d
```

Create the `php.conf` file using `nano` text editor.

```sh
nano php.conf
```
Add the following source code to load the module of `php-apache` from `$PREFIX/libexec/apache2/libphp.so` and save file.

**`php.conf`**
```conf
LoadModule php_module libexec/apache2/libphp.so
<FilesMatch \.php$>
   SetHandler application/x-httpd-php
</FilesMatch>
<IfModule dir_module>
    DirectoryIndex index.php
</IfModule>
```

We need to include the new config file to the `httpd.conf`.

```sh
cd $PREFIX/etc/apache2
nano httpd.conf # open apache2 config file
```

Go to the end of `httpd.conf` file and remove comment `#`.

**`httpd.conf`**

```conf
#Include etc/apache2/conf.d/*.conf
```

Find the `worker` Module of PHP that will not need for us.

<kbd>CTRL+W</kbd> and type `worker` and <kbd>Enter</kbd>.

**`php.conf`**

```conf
LoadModule mpm_worker_module libexec/apache2/mod_mpm_worker.so
```
Add comment `#`.

```conf
LoadModule mpm_worker_module libexec/apache2/mod_mpm_worker.so
```

Find `prefork` module and remove `#`.

**`php.conf`**

```conf
#LoadModule mpm_prefork_module libexec/apache2/mod_mpm_prefork.so
```

When we done the setting up of the config file,we will need to restart the `Apache`.

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

To stop the Apache server just run the following command.

```sh
apachectl stop # to stop the server
```

If you got the servername error open `httpd.conf` file and search `ServerName` and edit like below.

**`php.conf`**

```conf
ServerName localhost:8080
```

Restart the server and test again.

Open Browser and search tthe address `localhost:8080` you will see `It work!`.It is the default page.We can change the server's root directory.

Open `httpd.conf` and search the `DocumentRoot` and change the server's directory like below.

**`php.conf`**

```conf
DocumentRoot "/sdcard/htdocs"
<Directory "/sdcard/htdocs">
```

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