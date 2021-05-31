---
title: Conda Basics
date: 2020-3-17
tags: 
	- Anaconda
categories: 
	- Computer Science
	- Tools
---
# Conda commands

## 1. install

## 2. Setting up Anaconda Environments

### 2.1 set up

```bash
# list all available version in anaconda
conda search "^python$"

# to create a new environment (the latest)
conda create --name gy_env python=3
# to create a specific version environment
conda create --n gy_env36 python=3.6

# activate the new environment
conda activate gy_env

# verify the version of Python
python --version
```

### 2.2 activate / deactivate / update

```bash
# activate
conda activate gy_env
# or
source activate gy_env

# deactive
conda deactivate gy_env
# update the version (from 3.6.1 to 3.6.2)
conda update python
# environment information
conda info --envs
```

### 2.3 install packages

```bash
# install
conda install --name gy_env36 numpy
# when creating:
conda create --name gy_env python=3 numpy

# remove
conda remove --name gy_env36 --all
```

## 3. Update Anaconda

```bash
conda update conda
conda update -n base -c defaults conda


conda update anaconda
```

## 4. Uninstall Anaconda

```bash
# start with "anaconda-clean" to remove configuration files
conda install anaconda-clean
# then run the "anaconda-clean", this will create a backup folder called .anaconda_backup
anaconda-clean
# remove the entire diretory
rm -rf ~/anaconda3
# remove the PATH line
vim ~/.bashrc
# Delete or comment out the following lines:
export PATH="/home/ygnmax/anaconda3/bin:$PATH"
```

