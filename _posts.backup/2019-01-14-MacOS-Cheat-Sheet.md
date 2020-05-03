---
layout: post
title:  "Welcome to MacOS!"
permalink: mac-os-tricks
---
## Tested Out On MacOS: Mojave
Read [this](https://docstore.mik.ua/orelly/unix3/mac/)

## System Related Info
### File System Structure is customized for each OS but certain commonality is shared
* /: root directory, shared by all users
* /etc: configuration files for Unix applications and services & startup scripts
* /Library: system-level customization
* /System/Library: should not modify
* /var: transient or volatile files
* /dev: device files
    * tty: Standard output stream of the current Terminal or remote login
    * null: redirect output here and it disappears
    * stdin/stdout?

### Homebrew: MacOS package manager
* `man brew` gives all need info:
    * brew info [formula...]: check installed formula status OR uninstalled dependency
    * brew --prefix [formula...]: check location of installed formula -> `which cmd`
* brew installs all packages in /usr/local

## User Related Info
* ~ or /Users/user-name/: home directory, modified by one user
* ~/Library - user-specific setting, such as Terminal, Messages etc
* source .bash_profile OR restart terminal: stores $PATH extension. 
    * If .bash_profile is messed up: $PATH is no longer valid: `/usr/bin/vi ~/.bash_profile`
* 

## File System
<img src="/assets/root-fs.jpg" alt="root-fs" style="width:500px;"/>
### APFS: Apple File System
* Type of files: 
    * [Frameworks](https://developer.apple.com/library/archive/documentation/MacOSX/Conceptual/BPFrameworks/Concepts/WhatAreFrameworks.html#//apple_ref/doc/uid/20002303-BBCEIJFI): bundle of resources

### Unix File System 
* inodes: 
* links: a file pointer 
    * Every file in the File System is a "hard link" to the inode Look Up Table?
    * Hard links are equal file pointers to the same inode. Deleting a file/hardlink will not affect the file if there's at least one more hard link to the file -> **same inode**, same accessibility, affect link # in `ls -l`
    * Soft links are **new** files pointing to the original file. Deleting a softlink will not affect the file -> different inode, same accessibility, doesn't affect link # in `ls -l`
    * If all hardlinks are lost: the file is "deleted" and disk space is claimed by the OS. softlinks become invalid: the softlink file still exists but can no longer be used to access anything.
    * 
* file descriptor: 

### HFS/HFS+
