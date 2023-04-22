---
layout:		post
title:		Install TinyOS 2.1.2 on Ubuntu 14.04.06
category:	misc
author:		Tiantian Li
---

## Prerequisites

1. A fully functional virtual machine running on **Ubuntu 14.04.06** with **proper Internet connection**.
2. A clear mind.
3. Basic Linux skills.

## Installation

### 1. Set up Standford repository source

Open `/etc/apt/sources.list` with root privilege:

```shell
$ sudo vim /etc/apt/sources.list
```

Append the following line to the end of the file:

```
deb http://tinyos.stanford.edu/tinyos/dists/ubuntu lucid main
```

Save and exit.

### 2. Install basic toolchains and TinyOS

Install required packages:

```shell
$ sudo apt update
$ sudo apt install build-essential tinyos-2.1.2 python2.7-dev
# Say yes to the following warnings
# Install these packages without verification? [y/N] y
```

Append these lines to `~/.bashrc`:

```
export TOSROOT="/opt/tinyos-2.1.2"
export TOSDIR="$TOSROOT/tos"
export CLASSPATH=$CLASSPATH:$TOSROOT/support/sdk/java/tinyos.jar
export MAKERULES="$TOSROOT/support/make/Makerules"
export PYTHONPATH=$PYTHONPATH:$TOSROOT/support/sdk/python
```

Execute `source ~/.bashrc` to effect immediately. 

Make yourself the owner & group of the TinyOS root directory:

```shell
$ sudo chown -R $USER:$USER $TOSROOT	# Recursively change the owner and group of $TOSROOT 
```

If you don't want Java to later bitch about not finding appropriate JNI support:

```shell
$ cd $TOSROOT/support/sdk/java
$ sudo tos-install-jni
```

## Compile TOSSIM for testing

```shell
$ cd $TOSROOT/apps/Blink
$ make micaz sim
```

You should be able to see the following output:

```
  copying Python script interface TOSSIM.py from lib/tossim to local directory

*** Successfully built micaz TOSSIM library.
```

🎉🎉🎉
