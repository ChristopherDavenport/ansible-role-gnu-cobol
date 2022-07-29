# GnuCOBOL Installer

[![Build Status](https://travis-ci.org/ChristopherDavenport/ansible-role-gnu-cobol.svg?branch=master)](https://travis-ci.org/ChristopherDavenport/ansible-role-gnu-cobol)

Install GnuCOBOL on a system. GnuCOBOL is the recent and well
received open source compiler for COBOL code. I would like to make
it easy and seamless for developers on any platform to put this
into out into a production environment.

Hopefully we can move to packaging these for much easier
deployments, however this seems like a simple starting point
for getting COBOL program off proprietary compilers and save
us all some money in the process.

The check pass is failing on version 1 for Ubuntu 16.04 and Fedora 24 however
installation and compilation appears to be working correctly so if anyone
would like to explain/fix this I would be appreciative. So that it can be
added back to the tests. 

## Requirements

None, it will make sure all dependencies are in place on
supported systems.

Unsupported systems need only get me a list
of packages for gcc, g++, make, tar, berkeley db, ncurses,
gmp, and libc along with their dev and lib packages. However if these are already installed this should run fine.

## Role Variables

Available variables are listed below, along with default values
(see ```defaults/main.yml```):



#### GnuCOBOL Version

Default version of GnuCobol is the newer version 2, however if
you would like to run version 1 feel free to run that. If I get
ambitious I might add the nightly into the mix.

```
gnu_cobol_version: 3
```


#### Base Directory For Installation

This is the very logical choice for the software that we are
adding however if you would like to place it somewhere else you
are free to do so.

```
gnu_cobol_base: /usr/local/src
```

#### Install GnuCobol

This is a trigger switch which allows you to install or
uninstall a version of GNUCOBOL. Currently if you have one
version installed and attempt to install another it will throw
an error. (Development is in progress for autoremoval)

The purpose is primarily installation so the default setting
is True.

```
gnu_cobol_install: True
```

#### Recompile On Demand

If everything is installed and you want to force a recompile
anyways. This will do so however is non idempotent as a call to
make recompiles.

```
gnu_cobol_recompile: False
```

## Dependencies

-   None

## Example Playbook

```
- hosts: appservers
  roles:
    - ChristopherDavenport.gnu-cobol
```

### License

MIT

### Author Information

This role was created in 2016 by ChristopherDavenport.
