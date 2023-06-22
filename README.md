# LINUX

### Creating an empty file in linux

`touch test.txt`

### Checking permissions on the file
`ls -l`

### Changing permissions in linux for the owner of the file

In Linux, you can change file permissions using the chmod command.

* `chmod +rwx` filename to add permissions
* `chmod -rwx` directoryname to remove permissions. 
* `chmod +x` filename to allow executable permissions.
* `chmod -wx` filename to take out write and executable permissions.


Note that “r” is for read, “w” is for write, and “x” is for execute. 

This only changes the permissions for the owner of the file.

### Changing permissions in linux for the for the group owners and others

The command for changing directory permissions for group owners is similar, but add a “g” for group or “o” for others, 'u' will be for 'user/owner':

* `chmod g+w filename`

* `chmod g-wx filename`

* `chmod o+w filename`

* `chmod o-rwx foldername` '-' removes permissions

To change directory permissions for everyone, use “u” for users, “g” for group, “o” for others, and “ugo” or “a” (for all).

* `chmod ugo+rwx foldername` to give read, write, and execute to everyone.

* `chmod a=r foldername` to give only read permission for everyone.


### Changing Linux permissions in numeric code

You may need to know how to change permissions in numeric code in Linux, so to do this you use numbers instead of “r”, “w”, or “x”.
* 0 = No Permission
* 1 = Execute
* 2 = Write
* 4 = Read

Permission numbers are:

* 0 = ---

* 1 = --x

* 2 = -w-

* 3 = -wx

* 4 = r-

* 5 = r-x

* 6 = rw-

* 7 = rwx

For example:

* `chmod 777 foldername` will give read, write, and execute permissions for everyone.

* `chmod 700 foldername` will give read, write, and execute permissions for the user only.

* `chmod 327 foldername` will give write and execute (3) permission for the user, w (2) for the group, and read, write, and execute for the users.

### Checking the system version

`uname -v` - -v version of the operating system

## What is Bash

Bourne Again SHell
Unix was a text based operating system. Bash is an upgraded version of what was used in Unix.

/bin/bash

#### What is a Shell?

It is a software that basically provides interface to run commands.

There are multiple shells


`cat /etc/shells`   - listing all different shells installed in your os

`ps -p $$`  - shows the processes that we are running (-p $$ specyfing current process)

`history` - history of commands that we have already ran

`!22` - ran the command from history under the number 22

`history -c` - cleaning the history

`ls` - list files and folders

`ls -a` - list all hidden files and directories

Linux treats everything as a file. Even the folder 

`cd` - going to the home directory / cd used to navigate between directories

`pwd` - present working directory

/ - root directory

`cd /` - going to root directory

root directory - separate from the other users directories. It is for super user

. - current directory
.. - parent directory

`ls -l` listing permissions for user, groups and everyone else

blue color is for directories, white for files

`curl <url for something>` - transfering data / saving files


`curl <url> --output <name of the file we want to save the data>` - saving the data to the actual file we specified

`file <file name>` - checking what type of file is this

`mv <file name> <new file name>` moving / transferring file to another file / changing the file. does not duplicate


`cp <file we want to copy> <new file name>` copying the file / duplicating

`rm <file we want to remove>` - removing the file

`mkdir <directory name>` - creating a new directory

`rm -r <directory name>` - removing directory -r means recursive. It will remove wverything inside the folder as well

cd my\ pictures = cd "my pictures"

`touch <file name>` - creating empty file

`nano <file name>` - opens editor on the chosen file

`cat <file name>` - printing the content of the  file to the terminal

`head -2 <name of the file>` - printing first 2 lines of the file to therminal

`tail -2 <name of the file>` - printing last 2 lines of the file to terminal

`nl <name of the file>` - numbers lines in your file

`cat chicken-joke.txt | grep <line or word you are looking for>` - search a file and highligh what it finds

`apt install tree` - to install packages e.g tree package

add `sudo` for super user permission

### tree commands

`tree` - tree structure for files and folders for where you currently are

`sudo apt update -y` - update sources list just in case package is not on the list. -y to agree for the questions 

`mv chicken-joke.txt funny-stuff/funny-jokes/` - moving a file to another directory

`mv ~/funny-stuff/chicken-joke.txt .` - moving a file if you are not in the directory where the file is. '.' stands for current directory

`mv bad-joke.txt ~` or `mv bad-joke.txt ..`  - moving a file to a home directory

## Scripting

Making a script file

`touch provision.sh` - .sh - script files
`nano provision.sh` - open editor to write commands

if you are owner of the file you dont need to use `sudo`

`#!/bin/bash`  - always start to tell which shell we want to use

`# update` - update the sources
`sudo apt update -y`


`# upgrade` - sometimes you dont want upgrade cause its install new packages
`sudo apt upgrade -y`

`# install nginx`
`sudo apt install nginx -y`

`# restart nginx`
`sudo systemctl restart nginx`

`# enable nginx` - make sure when VM is restarted nginx will automatically start with restart
`sudo systemctl enable nginx


`chmod +x provision.sh` - adding execute permission

`./provision.sh `To run a script

Nginx (engine-x) is a popular open-source web server and reverse proxy server. Commonly used in web hosting environments to serve websites and web applications.
  ```bash  
    #!/bin/bash

    # update
    sudo apt update -y

     # upgrade
     sudo apt upgrade -y
     # install nginx
     sudo apt install nginx -y
     # restart nginx
     sudo systemctl restart nginx
     # enable nginx
     sudo systemctl enable nginx
```


systemctl is a command-line tool used to control and manage systemd services in Linux. Systemd is a system and service manager that provides a range of funcionalities including, starting, stopping and monitoring services.

In the given script systemctl is used to interact with Nginx service.

### Environment variables

value stored in memory, it can be accessible by other tools in Linux

`printenv` - printing all environment variables and values e.g USER, PATH, 


`printenv USER` - printing specific variable USER

`MYNAME=krzysztof` - creating variable

`echo $MYNAME`  - printing MYNAME variable to the console

`export MYNAME=krzysztof` - creating ENVIRONMENTAL variable

`unset <name of your variable>` - removes variable

Editing `.bashrc` file to make environmental variables persistent (so they won't dissapear after logging out)

`nano .bashrc` - opening editor with the file

and add at the bottom of the file environmental variable e.g:

`export CATSNAME=Bobby`

`source .bashrc` - reload edited configuration file

After all these steps env variable will be persistent after next time we log in


### Processes

2 types:

* system processes: `ps aux`
* user processes: `ps`

Process is like a program that loaded to RAM. If your CPU has 1 core basically CPU can run 1 process at the time. Multicores can do more.
OS needs to prioritize processes. Which one most important.

PID - process ID (every process has a process ID)