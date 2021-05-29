---
title: Vim Basics
date: 2020-1-27
tags: 
	- Vim
	- Linux
categories: 
	- Computer Science
	- Tools
	- Vim
---
# Introduction to vim
##3 modes for vim
+ insert ```i```
+ normal  ```esc```
+ visual ```v```

##


## Search
In the normal mode, type ```/```, then type what you want to search

## Replace
+ replace one character / word:
    + in the normal mode, type ```:s```, then type ```/x```, “x” is what you want to replace, then type ```/y```, “y” is what you want to be replaced with. Then type ```enter```
    + eg: ```:s/hello/hi```, then hello will be replaced with hi.
+ replace all the target characters / words in one line: 
    + in the normal mode, type ```:s```, then type ```/x```, “x” is what you want to replace, then type ```/y```, “y” is what you want to be replaced with, then type ```/g```. Then type ```enter```
    + eg: ```:s/hello/hi/g```, then all the hello in one line will be replaced with hi.
+ replace all the target characters / words in the whole file: 
    + in the normal mode, type ```:%s```, then type ```/x```, “x” is what you want to replace, then type ```/y```, “y” is what you want to be replaced with, then type ```/g```. Then type ```enter```
    + eg: ```:s/hello/hi/g```, then all the hello in the whole file will be replaced with hi.

## Copy and Paste
+ copy one line:
    + in the normal mode, type ```yy``` 
    + start a new line, type ```o``` or ```O``` (here you will enter the insert mode)
    + type ```esc``` and back to normal mode
    + type ```p``` to paste
## Delete
+ delete one line:
    + in the normal mode, delete the line you are in, type ```dd```
+ delete multiple lines:
    + in the normal mode, type numbers, like ```20```
    + then type ```dd```
    
## Revoke
+ backward: return to the stage before some commands
    + in the normal mode, type: ```u```
+ forward: return to the stage before revoking
    + in the normal mode, control: ```control + R```
    
## Loop
+ insert a great number of an indentical word
    + eg: insert 100 “hello”s
        + in the normal mode, type: ```100```
        + then enter the insert mode, type: ```hello```, and then press ```enter```
        + then back to normal mode by pressing ```esc```
## comment
    + comment one line:
        + type ```#```
    + comment multiple line 
        + ```visual block```, ```space```, ```#``` 
## help
+ in the normal mode, type ```:help```
+ in the normal mode, type ```:usr_01.txt```
