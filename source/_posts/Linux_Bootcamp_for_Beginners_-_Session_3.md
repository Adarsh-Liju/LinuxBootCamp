---
title: Linux Bootcamp for Beginners - Session 3
---
# FOSS
![Richard Stallman](https://paper-attachments.dropbox.com/s_7F2492607B71714A428607E3287D6493F19F9B88906C055C4E199BFBDF802B26_1654201183185_371px-Richard_Stallman_at_LibrePlanet_2019.jpg)

## “Free and Open Source Software”
- The freedom to run the program as you wish, for any purpose .
- The freedom to study how the program works, and change it so it does your computing as you wish . 
- The freedom to redistribute copies so you can help others.
- The freedom to distribute copies of your modified versions to others (freedom 3). By doing this you can give the whole community a chance to benefit from your changes. Access to the source code is a precondition for this


# GNU - GNU’s Not Unix
![](https://paper-attachments.dropbox.com/s_7F2492607B71714A428607E3287D6493F19F9B88906C055C4E199BFBDF802B26_1654201894183_file.png)



# FOSS vs Proprietary software?

Propreitery soft.

- Costly
- Under control of the org
- ppl cant contribute


# Process

A program/command when executed, a special instance is provided by the system to the process. This instance consists of all the services/resources that may be utilized by the process under execution. 

- Whenever a command is issued in Unix/Linux, it creates/starts a new process. For example, pwd when issued which is used to list the current directory location the user is in, a process starts.
- Through a 5 digit ID number Unix/Linux keeps an account of the processes, this number is call process ID or PID. Each process in the system has a unique PID.
- Used up pid’s can be used in again for a newer process since all the possible combinations are used.
- At any point of time, no two processes with the same pid exist in the system because it is the pid that Unix uses to track each process.

**Foreground Process :** Every process when started runs in foreground by default, receives input from the keyboard, and sends output to the screen.  

**Background Process:** It runs in the background without keyboard input and waits till keyboard input is required. Thus, other processes can be done in parallel with the process running in the background since they do not have to wait for the previous process to be completed. 

# Types of process


# Parent Process

All the processes in operating system are created when a process executes the fork() system call except the startup process. The process that used the fork() system call is the parent process. In other words, a parent process is one that creates a child process. A parent process may have multiple child processes but a child process only one parent process.
On the success of a fork() system call, the PID of the child process is returned to the parent process and 0 is returned to the child process. On the failure of a fork() system call, -1 is returned to the parent process and a child process is not created.


# Child Process

A child process is a process created by a parent process in operating system using a fork() system call. A child process may also be called a subprocess or a subtask.
A child process is created as its parent process’s copy and inherits most of its attributes. If a child process has no parent process, it was created directly by the kernel.
If a child process exits or is interrupted, then a SIGCHLD signal is send to the parent process.
A diagram that demonstrates parent and child process is given as follows −

![How parent-child process works](http://www.it.uu.se/education/course/homepage/os/vt18/images/module-2/fork-wait-exit.png)



# Zombie Process

A zombie process is a process whose execution is completed but it still has an entry in the process table. Zombie processes usually occur for child processes, as the parent process still needs to read its child’s exit status. Once this is done using the wait system call, the zombie process is eliminated from the process table. This is known as reaping the zombie process.

![Zombie Process](https://www.tutorialspoint.com/assets/questions/media/12233/Zombie%20Process%20in%20LInux.png)

- All the memory and resources allocated to a process are deallocated when the process terminates using the `exit()` system call. But the process’s entry in the process table is still available. This process is now a zombie process.
- The exit status of the zombie process zombie process can be read by the parent process using the `wait()` system call. After that, the zombie process is removed from the system. Then the process ID and the process table entry of the zombie process can be reused.
- If the parent process does not use the `wait()` system call, the zombie process is left in the process table. This creates a resource leak.
- If the parent process is not running anymore, then the presence of a zombie process indicates an operating system bug. This may not be a serious problem if there are a few zombie processes but under heavier loads, this can create issues for the system such as running out of process table entries.
- The zombie processes can be removed from the system by sending the `SIGCHLD` signal to the parent, using the kill command. If the zombie process is still not eliminated from the process table by the parent process, then the parent process is terminated if that is acceptable.

We can see zombie processes if we type `ps -aux`.

| **STAT** | **Process State**                                                     |
| -------- | --------------------------------------------------------------------- |
| **D**    | uninterruptible sleep (usually IO)                                    |
| **R**    | running or runnable (on run queue)                                    |
| **S**    | interruptible sleep (waiting for an event to complete)                |
| **T**    | stopped, either by a job control signal or because it is being traced |
| **X**    | dead (should never be seen)                                           |
| **Z**    | defunct ("zombie") process, terminated but not reaped by its parent   |
| **<**    | high-priority (not nice to other users)                               |
| **N**    | low-priority (nice to other users)                                    |
| **L**    | has pages locked into memory (for real-time and custom IO)            |
| **s**    | is a session leader                                                   |
| **l**    | is multi-threaded (using CLONE_THREAD, like NPTL pthreads do)         |
| **+**    | is in the foreground process group                                    |



# Orphan Process
- Orphan processes are those processes that are still running even though their parent process has terminated or finished. A process can be orphaned intentionally or unintentionally.
- An intentionally orphaned process runs in the background without any manual support. This is usually done to start an indefinitely running service or to complete a long-running job without user attention.
- An unintentionally orphaned process is created when its parent process crashes or terminates. Unintentional orphan processes can be avoided using the process group mechanism.


# Daemon Process

A daemon process is a background process that is not under the direct control of the user. This process is usually started when the system is started and is terminated with the system shut down.
Usually the parent process of the daemon process is the init process. This is because the init process usually adopts the daemon process after the parent process forks the daemon process and terminates.
The daemon process names normally end with a d. Some of the examples of daemon processes in Unix are −

- **crond**
- This is a job scheduler that runs jobs in the background.
- **syslogd**
- This is the system logger that implements the system logging facility and collects system messages.
- **httpd**
- This is the web server daemon process that handles the Hypertext Transfer Protocol.
- **dhcpd**
- This daemon configures the TCP/IP information for users dynamically.
# ps

ps (Process status) can be used to see/list all the running processes. 

Normal Use:

    ps

For More Info

    ps -f

For a particular process ID

    ps <process id>


![](https://paper-attachments.dropbox.com/s_7F2492607B71714A428607E3287D6493F19F9B88906C055C4E199BFBDF802B26_1654185800241_image.png)


**Fields described by ps are described as:** 

- **UID**: User ID that this process belongs to (the person running it)
- **PID**: Process ID
- **PPID**: Parent process ID (the ID of the process that started it)
- **C**: CPU utilization of process
- **STIME**: Process start time
- **TTY**: Terminal type associated with the process
- **TIME**: CPU time is taken by the process
- **CMD**: The command that started this process 
# kill
- `kill` command in Linux, is a built-in command which is used to terminate processes manually.
- It helps in unwanted congestion or saturation of tasks.

**Basic Syntax**

    kill <signal> <process id>

`**kill -l**` **:**To display all the available signals


![](https://paper-attachments.dropbox.com/s_7F2492607B71714A428607E3287D6493F19F9B88906C055C4E199BFBDF802B26_1654186317333_image.png)

## Usage
    kill -5 1234
    kill -SIGKILL 1234


# `top`
- Displays all tasks presently running.
- It has a CLI for killing, sorting and suspending tasks
- `htop` is an improved version of this software.

**Usage**


    top
![](https://paper-attachments.dropbox.com/s_7F2492607B71714A428607E3287D6493F19F9B88906C055C4E199BFBDF802B26_1654202140380_image.png)

    htop
![](https://paper-attachments.dropbox.com/s_7F2492607B71714A428607E3287D6493F19F9B88906C055C4E199BFBDF802B26_1654202325247_image.png)


`**bashtop**`

- bashtop is a resource monitor that shows usage and stats for processor,memory, disks, network and processes.
    - Easy to use, with a game inspired menu system.
    -  Function for showing detailed stats for selected process.
    -  Ability to filter processes.
    - Easy switching between sorting options.
    -  Send SIGTERM, SIGKILL, SIGINT to selected process.
    - UI menu for changing all config file options.
    - Auto scaling graph for network usage.


![](https://paper-attachments.dropbox.com/s_7F2492607B71714A428607E3287D6493F19F9B88906C055C4E199BFBDF802B26_1654706380412_image.png)


