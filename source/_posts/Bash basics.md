---
title: Bash Basics
date: 2020-3-17
tags:
  - Bash
  - Linux
categories:
  - Computer Science
  - Tools
  - BashFiles
---
# Manipulate Files and Folders

# Files

## cp / scp

```bash
## cp <from path> <to path>
## scp <from path> <to path>
## probabily scp require you to type the password

## -r : copy all the folder, followed by scp
scp -r account@address:~/data/ .
```

# List

## list

### 1. options

```bash
## list the files in time order
ls -alhtr
# -a: all files
# -d: show as a directory, don't show the sub-files
# -l: long information: permission, owner, sizes
# -l --full-time: full time
# -l --full-time --time=atime/ctime/mtime
# -r: recursive
# -h: human-readable
# -si: similar to -h
# -t: order by time
# -v: order by version
# -F or -p: seperate the folders and files
#### mtime: the latest revised time
```

### 2. filter

```bash
ls test*
ls D*
ls -d */
```

```bash
# filter to show the files
ls -F |grep -v /
# filter to show the directories
ls -F |grep /$
```

### 3. order

```bash
ls -lt
```

### 4. useful link:

[linux ls命令](https://www.cnblogs.com/sparkdev/p/7476005.html)

[ls命令](https://www.cnblogs.com/peida/archive/2012/10/23/2734829.html)

## df

```bash
# check the information about the disk
df -h
```

## du

```bash
# check the current folder size
du -h --max-depth=1 <path>
```



# Search

## grep

```bash
ls | grep
```

# Check files

## Vim

```bash
vim test.py
vim ./test.py
```

## head

```bash
head test.py
```

## wc

```bash
wc - lcw <file>

# total number of files in the current folder
ls -l|grep "^-"| wc -l

ls -l *AL* | wc -l
```


# Install and Uninstall
```Bash
dpkg --list

sudo apt-get remove “package-name”
```
or
```Bash
sudo apt-get purge “package-name”
sudo apt-get autoremove
```

# Process Management

## top/htop

```bash
htop
```

## ps

```bash
ps aux | grep ygnmax
# ps = process status
# a = show processes for all users
# u = display the process's user/owner
# x = also show processes not attached to a terminal
```

## fg / bg /&

```bash
# add &, setting process running in the background
stata-mp -e test.do &

# transfer the process from background to foregraound
fg <job ID>

# transfer the process from foreground to backgraound
# first step: ctrl + D
# second step: bg + <job ID>
<ctrl + D>
bg <job ID>
```





# Environment Management

## Modules

### 1. install

```bash
# modules installation dir
INSTALL_PATH=${HOME}/opt/modules-4.2.1/

tar -xvf modules-4.2.1.tar

# enter modules folder
cd modules-4.2.1

# install modules
./configure --prefix=${INSTALL_PATH}
make
make install
```

### 2. usage

```bash
# check the available software
module avail
module avail stata

# load software
module load statamp/15

# list loaded software
module list

# unload software
module unload statamp/15

```

### 3. useful Link

[Environment Modules](http://modules.sourceforge.net/)

[Environment Modules 简明教程](https://zhuanlan.zhihu.com/p/50725572)
