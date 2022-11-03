---
title: Linux Bootcamp for Beginners - Session 2
---

## Table of Contents
<!-- toc --> 

# Linus Torvalds
![Linus Torvalds](https://upload.wikimedia.org/wikipedia/commons/e/e8/Lc3_2018_%28263682303%29_%28cropped%29.jpeg)



# Storage Structure of Linux
![](https://paper-attachments.dropbox.com/s_C3F2B19DDBDA0B884AC8A93FEFEB05F933EDFD5E6DDAC52F8195936FA757710F_1654032263623_mermaid-diagram-20220601025416.png)



- In Linux, the file system creates a tree structure. All the files are arranged as a tree and its branches. 
- The topmost directory called the **root (/) directory**. All other directories in Linux can be accessed from the root directory.
- Some Features in Linux include :- 
    - **Specifying paths:** Linux does not use the backslash (\) to separate the components; it uses forward slash (/) as an alternative. 
    - **Partition, Directories, and Drives:** Linux does not use drive letters to organize the drive as Windows does. In Linux, we cannot tell whether we are addressing a partition, a network device, or an "ordinary" directory and a Drive.
    - **Case Sensitivity:** Linux file system is case sensitive. It distinguishes between lowercase and uppercase file names. This is also followed in **Linux commands** 
    - **File Extensions:** In Linux, a file may have the extension '.txt,' but it is not necessary that a file should have a file extension. If we use the graphical file manager, it symbolizes the files and folders.
    - **Hidden files:** Linux distinguishes between standard files and hidden files, mostly the configuration files are hidden in Linux OS. Usually, we don't need to access or read the hidden files. The hidden files in Linux are represented by a dot (.) before the file name (e.g., .ignore). To access the files, we need to change the view in the file manager or need to use a specific command in the shell.
# Linux File Permissions

The basic Linux permissions model works by associating each system file with an owner and a group and assigning permission access rights for three different classes of users:

## **Permission Groups**

- **owner** – The Owner permissions apply only to the owner of the file or directory, they will not impact the actions of other users.
- **group** – The Group permissions apply only to the group that has been assigned to the file or directory, they will not affect the actions of other users.
- **all users** – The All Users permissions apply to all other users on the system, this is the permission group that you want to watch the most.
    

**Permission Types**
Three file permissions types apply to each class of users:

- The `read` permission.
- The `write` permission.
- The `execute` permission.

| permission  | on a file                | on a directory                   |
| ----------- | ------------------------ | -------------------------------- |
| r (read)    | read file content (cat)  | read directory content (ls)      |
| w (write)   | change file content (vi) | create file in directory (touch) |
| x (execute) | execute the file         | enter the directory (cd)         |



# Basic I/O

```bash
echo "Hello Everyone"
```
# Linux Terminal
- The Linux terminal is a text-based interface used to control a Linux computer.
- It's just one of the many tools provided to Linux users for accomplishing any given task, but it's widely considered the most efficient method available.
- It's so popular, in fact, that Apple changed its foundation to Unix and has gained the `bash` and `zsh`
- Microsoft developed PowerShell, its very own open source command line similiar to Linux Terminals
# Linux Commands
- A **command** is a special keyword you can use in a terminal to tell your computer to perform an action.
- Most commands are tiny little applications that get installed with the rest of your operating system ( Even applications like `cat`, `ls` , `curl` )
## Arguments in Linux Commands
- An **argument** is any part of a command that isn't the command
- It directs the command to do a particular task

**Example**

```
    ls Documents
```
## Options in Linux Commands
- Command **options**, also called **flags** or **switches**, are part of command arguments. 
- A command argument is anything that follows a command, and an option is usually (but not always) demarcated by a dash or double dashes.

**Example**

```
    python3 --version
```

# Pipelining in Linux
- A `pipeline` is a sequence of one or more commands separated by one of the control operators ‘|’ or ‘|&’.
- The output of each command in the pipeline is connected via a pipe to the input of the next command. That is, each command reads the previous command’s output.
- `grep` is used to search for patterns or particular word in a list.

`grep` 
```
    cat <file> | grep <something>
```
**Example**

```
    ls -l | grep sample
```
![](https://paper-attachments.dropbox.com/s_C3F2B19DDBDA0B884AC8A93FEFEB05F933EDFD5E6DDAC52F8195936FA757710F_1654029159937_mermaid-diagram-20220601002450.png)

# Redirections in Terminal
- **Input/Output (I/O) redirection** in Linux refers to the ability of the Linux operating system that allows us to change the standard input (`stdin`) and standard output (`stdout`) when executing a command on the terminal.
- By default, the standard input device is your keyboard and the standard output device is your screen.

**Types of Redirection** 

**1. Overwrite**  
It completely overwrites with new data. Any old data present will be lost.


- `>` standard output
- `<` standard input

**2. Appends**  

It appends to the existing/old data. Any old data present will not be lost.

- `>>` standard output
- `<<` standard input

**Error Redirection:** Error redirection is transferring the errors generated by some false commands to a file rather than STDOUT.


    gcc 2>error.txt


    cat error.txt
    gcc: fatal error: no input files
    compilation terminated.


# Linux Shell
- The shell is the **Linux command line interpreter**. It provides an interface between the user and the kernel and executes programs called commands.
- Shell is an environment in which we can run our programs, and shell scripts.
## Types of shell 
- Friendly Interactive Shell - `fish`
- POSIX shell - `sh`
- Bourne Again shell - `bash`
- Z Shell `zsh` 

By Default Ubuntu has `bash` pre-installed

## Shell Scripting 
- A shell script is a computer program designed to be run by the Unix shell(here bash), a command-line interpreter. 
- Every shell script starts with a shebang construct to alert the system that a shell script has been started. For example :


    #!/bin/sh

**Comments** 

- Single Line comments - `#`
- Multi Line comments - `: '` to open and `'` to close.

**Example** 


    #!/bin/bash
    
    # Author : Adarsh Liju Abraham


- `echo` is used to print any string to `stdout`
- `read` is used to accept data from `stdin`

**Example**

    #!/bin/bash
    
    # Author : Adarsh Liju Abraham
    
    


