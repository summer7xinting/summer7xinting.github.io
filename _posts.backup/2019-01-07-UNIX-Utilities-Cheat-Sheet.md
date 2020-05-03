---
layout: post
title:  "Welcome to UNIX Utilities!"
permalink: unix-util-tricks
---
## Tested Out On MacOS & Ubuntu

## Hardware Information
* 

## CTRL Family
### terminals
* ctrl + c: interrupt kernel
* ctrl + u: clear everything from cursor to beginning of line
* ctrl + k: clear everything from end of line to cursor
* ctrl + h: backspace/delete char by char
* ctrl + w: delete a word
* ctrl + d: EOF
* ctrl + a/e: move to beginning/end
* ctrl + r: history search(use ctrl + r to navigate)
* ctrl + y: recall last input
* alt + b: move backward by a word
* alt + f: move forward by a word
### Vim
* w/e: move forward to the  beginning/end of a word
* 3w/3b: go foward/backward 3 words
* 0/$: move to the beginning/end of current line
* I/A: move to the beginning/end of current line and edit 
* (/): jump backward/forward one sentence
* {/}: jump backward/forward one paragraph
* k/j: jump backward/forward one line
* gg/G: jump to the beginning/end of file
* :42: jump to the 42nd line of file
* /pattern: search for pattern
* d/dd: delete a word/line
* x/X: delete a word/line
* y/Y: copy
* v/V: choose/choose lines
* p/P: paste
* :u: undo changes
* ctrl + r: redo changes

## LAN/Network
* lpr: printer is a device under /dev/? See more at [port 631](http://localhost:631/printers/) and man lpr/cups
* bluetoothctl:
    * > help: find all commands: list, devices, paired-devices, remove, scan, pair etc
    * MacOS can make use of [blueutil](https://github.com/toy/blueutil)
    * Debug Mode on Mac: shift + option + right-click bluetooth icon

## Admin 
* passwd: change password 
* who: list of all running user-terminal pair; finger: list of all users (idle of not)
* finger + username: find specific user info
* Note: create user: use either GUI or dscl 
* su: substitute user
* login:
* logout: ctrl + d, nothing can be done at this point

## File System 
* /bin
* /sbin
* /usr

### Package Manager
* 
* find: recurisively filter FS to match pattern
    * find [path] -name [name]: name is a string, path is a PATH
    * -max/mindepth
    * -link: match number of links
    * -path [path-regex] and -name [name-regex]


### File Related Commands
* ls: list directory: -halt
    * -l: read/write/exec -> long format displays file mode, number of links, owner name, group name, number of bytes in the file, abbreviated month, day-of-month file was last modified, hour file last modified, minute file last modified, and the path name.
    * -t: sort by modification date
    * -a: show hidden file (eg .bash_profile) 
    * -h: human-readable style
    * -i: show inode
* tree: installed by homebrew, list sub-directory structure
* cat: show content
* wc: word count
    * -l: # of newline-delimited item
    * -w: # of space-delimited item
    * -c: # of characters
* rm: remove file/directory: -rf 
* escape for special characters: \' = "'"
* cp: copy a path/file to a new path/file (overwrite when the new name exists)
    * cp -r /some-dir/ = cp -r /some-dir/* will copy everything in the directory (unbundled)
    * cp -r /some-dir will copy the directory (bundled)
* mv: move a path/file to a new path/file (overwrite when the new name exists)
* grep: accepts regex, search the dst file and display all lines containing the pattern
* head/tail: -n 
* sort: sort a file in order by lines
* uniq: skip **adjacent** duplicate lines -> used with sort to achieve **uniqueness**
* whereis/which: whereis finds all instances in the path; which gives the first one: the instance used
    * `PATH` is determined by the system? How to change it?
* compress: tar?
    * uncompress:
    * cat/zcat
* file: determine file type; ls -l: determine file access control
* chmod: change access control: `chmod ug=rx directory/file-name`
    * 4 types of user: **u**ser, **g**roup, **o**thers, **a**ll -> setting u/g/a OR u/g/o is sufficient to cover all users
    * 3 types of access: read, write, exec
    * 3 types of change: + to add access, - to remove access, = to set
* ln: create a link: `ln src targ` for hard links and `ln -s src targ` for soft links
    * soft link: symbolic link: a **new** file containing indirect reference to source_file, different inode, dual access, usually smaller in size
    * hard link: two file names, same inode, dual access, same in size
    * hard copy: two files, two inodes, one-way access, same in size
    * check link status: `ls -li`
* fd: 

## Terminal 
* echo: print to terminal (without re-direction)
* date
* man: display online manual(where)
* talk: current user with established mutual connection
* write: current user without consent
* mail: all users (online/offline), check by typing `mail`
* processed: 
    * top -o cpu/rsize: updated live processes ranked by cpu usage/memory usage
    * ps: 
        * ps aux: 

## Bash Script
### Black Magic, see [here](https://www.tldp.org/LDP/abs/html/)
#### script-wise details: 
* header: "shabang"
    * Usually: #!/bin/bash
    * The sha-bang (#!) at the head of a script tells your system that this file is a set of commands to be fed to the command interpreter indicated. The #! is actually a two-byte magic number, a special marker that designates a file type, or in this case an executable shell script (type man magic for more details on this fascinating topic). Immediately following the sha-bang is a path name. This is the path to the program that interprets the commands in the script, whether it be a shell, a programming language, or a utility. This command interpreter then executes the commands in the script, starting at the top (the line following the sha-bang line), and ignoring comments.
    * 
#### special characters (reserved keywords)
* #: comments: *Lines* beginning with a # (with the exception of #!) are comments and will not be executed.
* ; (space): command separator: 
* ;;: block ender in case statement
* .(dot): 
    * current directory in relative PATH
    * when matching character in regex: a single character
* , (comma space): links together a series of arithmetic operations. All are evaluated, but only the last one is returned.
    * if no space between two operations, the second one will append to the first evaluation
* escape \(backslash): literal interpretation
* /(forwardslash):
    * Filename path separator
    * mathematical division
* null command :(colon): This is the shell equivalent of a "NOP" (no op, a do-nothing operation).
    * can be used in endless loop
    * not sure how to use it at the front of the line???
* 

#### system-wise details: 
* shell sript is interpretted, not compiled: like Python
    * pure text substitution
* Different Shells: de facto standard is Bash
* Invoking shell scipt: 
    * sh script_name
    * chmod a+x scripscript_namet to make it executable, then ./script_name (since script_name is not in $PATH, `script_name` will not work, but abs path: ./script_name will). 
    * move script_name to /usr/local/bin to make it available system-wide: which script_name will work :) 


## Redirection

## Syscalls
* service: run a system init sript
    * sudo service bluetooth restart: ?
    * init scripts are stored in /etc/init.d: 
