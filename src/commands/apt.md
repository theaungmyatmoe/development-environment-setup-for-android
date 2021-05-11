# apt

`apt` is a linux package manager that can install and remove the packages and their dependencies.

## Update The Package List And Upgrade The System

`update` - update the list of avaliable packages
`upgrade` - upgrade the packages that are installed in your machine

```sh
apt update && apt upgrade -y
```

## List All Of The Packages

We can list the name of packages that we can install to our machine.

```sh
apt list
```

## Installing The Package

To install package we use `install` option and added `package name` to install.

```sh
➜  ~ apt install php
```

## Installing Multiple Packages

We can install multiple packages like below.

```sh
apt install php apache2 # and many more
```

## Reinstall The Packages

To reinstall the package we can use `reinstall` option.

```
apt reinstall php
```

## Removing Package

To remove the package we can use like below.

```sh
apt remove php
```

## Removing Related Packages

When we remove the package, it remove only one package, but we should remove its related packages and libiaries.

```sh
apt autoremove php
```

##  Show The Package's Detail

We can know the detail of packages.

```sh
apt show php
```

You can use `apt --help` for other options.