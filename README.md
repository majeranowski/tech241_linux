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

### changing owner in linux

`chown new_owner file_or_directory_path`

`chown -R new_owner directory_path` - change owner for the directory and all the files inside

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

### IP addressess:

Public IP address (associated VM)
* static - (default Azure) stays the same even when VM is restarted
* dynamic - (default AWS) - changes IP every restart of your VM

### Processes

2 types:

* system processes: `ps aux`
* user processes: `ps`

Process is like a program that loaded to RAM. If your CPU has 1 core basically CPU can run 1 process at the time. Multicores can do more.
OS needs to prioritize processes. Which one most important.

PID - process ID (every process has a process ID)

#### How to start and kill the process

`sleep <number of seconds>` - puts terminal to sleep (puts foreground) for certain amount of time

`sleep 5000 &` - puts terminal to sleep for 5000 sec but in the background

`jobs` - lists processes running in the background

`jobs -l` - list of processes with the process ID

`kill -1 <process ID>` - kills the proecss in the most gentle way (signal 1) - hanging up

`kill <process ID>` - kill the process, terminating (signal 15) - it will kill parent process and also child processes

`kill -9 <process ID>` - the harshest way of killing the process. Brute force stubborn process.  (signal 9) - it will kill the parent process but child processes will turn up zombie processes that might still running and taking up the memories

`ps -ef` - shows parent process ID

`sudo systemctl` - way to control system processes

### Sparta test app

* Node js app
* port 3000
* 2 features
  - a front page (no database if we just want to display front page)
  - posts page that shows some information from database

Requirements to run Sparta app
* Linux VM - Ubuntu 18.04 LTS
* web server - nginx
* right version node js - version 12.x works fine (dependency)
* app folder
* in app folder, run 2 commands:
  - npm install
  - node app.js or npm start

### getting folder to VM azure

* git clone

    - create a gitrepo - tech241-sparta-app
    - create a folder "tech241-sparta-app" on your local machine
    - copy app folder to your local reo
    - sync with your remote repo on GitHub
    - SSH into VM & git clone

* scp command
  
    - will need the private key
    - path to folder
    - adminuser@IP address

`scp -i ~/.ssh/tech241-krzysztof-az-key -r ./app adminuser@40.120.57.73:/home/adminuser/tech241-sparta-app`
  
* rsync 

### deploying app

```bash 
sudo apt update -y

sudo apt upgrade -y

# get from url needed version of node
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -

#install nodejs
sudo apt install -y nodejs

#installing pm2 that helps run apps in the background
sudo npm install pm2 -g 

#go to the app folder until you see content
npm install

# get the app going
npm start # or node app.js
```

You need to add port 3000 to your VM. add a security rule to VM

On Azure portal it is in 'Networking' tab and then 'Add inbound port rule'

after ctrl + z the app won't start again because it will be keep ocuppying the port 3000

2 services can't use the same port

Use ctrl+c instead 


### running db on the VM

create new VM for db

Requirements to get the db running for sparta app:

* Linux VM - Ubuntu 18.04 LTS
* update and upgrade
* Install mongo db version 3.2.x (non relational db)
  - download key for the right version
  - source list - specify mongo db version
  - update again
  - install mongo db
* configure mongo db to accept connections from app VM 


```bash 
sudo apt update -y

sudo apt upgrade -y

#to download key for the right version (from mongo db website)
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -

# source list
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

# update again
sudo apt update -y

# install mongo db
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

#configuration
sudo nano /etc/mongod.conf # in network interfaces we change bindIP to 0.0.0.0 to accept connections from any machines

#start mongod
sudo systemctl start mongod

#enabling mongod so it will always start
sudo systemctl enable mongod

```

127.0.0.1 - IP adress of the local host

`sudo systemctl status mongod` - checking if mongodb is running


### connecting app and db

Requirements to run Sparta app
* Linux VM - Ubuntu 18.04 LTS
* web server - nginx
* right version node js - version 12.x works fine (dependency)
* get app folder
* (if we want postpage to work) set DB_HOST env variable
* in app folder, run 2 commands:
  - npm install
  - node app.js or npm start


ON THE APP VM:

`export DB_HOST=mongodb://<IP-ADDRESS>:27017/posts`

```bash
 export DB_HOST=mongodb://20.162.216.138:27017/posts

```

later on npm install and npm run

`http://40.120.57.73:3000/posts` - to access post page

on th DB VM:

* you need to add inboud port security rule from port 27017


![adding-security-rule](Screenshot(6).png)


## Automation Tasks:

* app VM script:

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
# get from url needed version of node
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
# install nodejs
sudo apt install -y nodejs
#installing pm2 that helps run apps in the background
sudo npm install pm2 -g
# getting app folder to the VM
git clone https://github.com/majeranowski/tech241-sparta-app.git app3
#getting inside app folder
cd app3/app
#Creating DB_HOST env variable
export DB_HOST=mongodb://20.162.216.138:27017/posts
# installing the app
npm install
# starting the app
pm2 -f start app.js

```

* db VM script:

```bash
#!/bin/bash

# Update and upgrade the system
sudo apt update -y
sudo apt upgrade -y

#to download key for the right version (from mongo db website)
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -

# source list
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

# update again
sudo apt update -y

# install mongo db
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

# Configure bindIp to 0.0.0.0
sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/g' /etc/mongod.conf

# Start Mongo DB
sudo systemctl start mongod

# Enable Mongo DB
sudo systemctl enable mongod

```


### Running node app in the background using &

```bash
nohup node app.js </dev/null &>/dev/null &
```

without </dev/null> we would get the message:

`nohup:ignoring input and appending output to 'nohup.out'`

nohup means no hang up - which means that process will be still running even if we log out from the terminal. if we don't mention nohup the user processes will hang up when we exit the terminal.


and terminal would be occupied.

ps2 is a better solution because we can force rerunning the app. with nohup keyword port 3000 would be occupied.


when you run a bash script shell in bash it kind of create subshell. after the script finishes it hang up the subshell and all the user processes withing. to prevent that you need to add nohup.



# reverse proxy research and task:

* What are ports?

ports are virtual endpoints that enable communication between different programs or services on a computer or across a network. They allow for the transfer of data packets between applications or devices.

* WHat is proxy?

A proxy, in the context of computer networking, is an intermediary server that acts as a gateway between a client device and a target server. It facilitates communication between the client and the server by forwarding client requests and receiving server responses. The proxy server operates on behalf of the client and provides several benefits, including enhanced privacy, security, and performance optimization.

* What is the reverse proxy 

A reverse proxy is a server or a software application that sits between client devices and web servers. It acts on behalf of the web servers to handle client requests and distribute them to the appropriate backend servers. Unlike a normal proxy, which forwards client requests to remote servers, a reverse proxy accepts requests on behalf of servers and returns the responses to clients.

Here are the key differences between a reverse proxy and a normal proxy:

* Direction of communication: A normal proxy acts as an intermediary between a client device and a remote server. It forwards client requests to the server and relays the server's responses back to the client. In contrast, a reverse proxy acts as an intermediary between clients and backend servers. It receives client requests and forwards them to the appropriate server, then returns the server's responses to the clients.

* Load distribution: One of the primary functions of a reverse proxy is load balancing. It distributes incoming client requests across multiple backend servers to achieve better performance and scalability. By intelligently distributing the workload, a reverse proxy can optimize resource utilization and prevent any single server from becoming overwhelmed. A normal proxy typically does not provide load balancing capabilities.

* Content caching: Reverse proxies often implement content caching, which involves storing copies of server responses locally. When subsequent requests for the same content are made, the reverse proxy can serve the cached copy directly to clients without forwarding the request to the backend server. This can significantly improve response times and reduce the load on the backend servers. Normal proxies may also support caching, but it is not as commonly used.

* SSL termination: Reverse proxies can handle Secure Sockets Layer (SSL) encryption and decryption, relieving the backend servers from this resource-intensive task. The reverse proxy can establish the SSL connection with the client and then communicate with the backend server over an unencrypted connection. This allows the backend servers to focus on processing requests and responses without the overhead of SSL encryption. Normal proxies generally do not perform SSL termination.

Overall, a reverse proxy is specifically designed to handle client requests on behalf of backend servers, providing load balancing, caching, SSL termination, and other features to optimize performance, security, and scalability. In contrast, a normal proxy primarily forwards client requests to remote servers without the additional functionalities typically found in a reverse proxy.

![reverse-proxy](IMG_0897.jpg)


* How Do you setup nginx reverse proxy

- Install Nginx on your Windows or Linux server (prerequisite).
- Add the Nginx proxy_pass setting in a virtual host or the default config file.
- Map a context root to the URL of a backend server.
- Optionally set headers for the Nginx reverse proxy to use with the backend.
- Restart Nginx reverse proxy and test the reverse proxy setup.


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


The most important configuration step in an Nginx reverse proxy configuration is the addition of a proxy_pass setting that maps an incoming URL to a backend server.

```bash
sudo nano /etc/nginx/sites-available/default

```


in the default file we need to change the line in location starting with:

`try_files $uri $uri/ =404;`

for 

`proxy_pass http://localhost:3000;`

after that we need to restart nginx:

`sudo systemctl restart nginx`

Command to setup nginx as a reverse proxy:


`sudo sed -i 's@try_files .*;@proxy_pass http://localhost:3000;@' /etc/nginx/sites-available/default`

### app VM script that automates reverse proxy

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
# setup nginx as a reverse proxy
sudo sed -i 's@try_files .*;@proxy_pass http://localhost:3000;@' /etc/nginx/sites-available/default
# restart nginx again
sudo systemctl restart nginx
# get from url needed version of node
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
# install nodejs
sudo apt install -y nodejs
#installing pm2 that helps run apps in the background
sudo npm install pm2 -g
# getting app folder to the VM
git clone https://github.com/majeranowski/tech241-sparta-app.git app3
#getting inside app folder
cd app3/app
#Creating DB_HOST env variable
export DB_HOST=mongodb://20.162.216.138:27017/posts
# installing the app
npm install
# starting the app
pm2 -f start app.js


```