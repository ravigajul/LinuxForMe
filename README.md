# LinuxForMe
    Echo $SHELL  result /bin/bash

# Home Directory
    /home/rgajul 

# 1. Print to screen
    Echo Hi

# 2. List files & Directories
    Ls
# 3. Change Directory
    CD Test

# 4. Present Working Directory
    PWD
# 5. Directory
## 0. create a new directory
    Mkdir test

## 1. Run multiple Commands
    Cd new_directory; mkdir www; pwd

## 2. Create a directory tree
    Mkdir -p /tmp/asia/india/hyderabad

## 3. Remove a directory and all of subdirectories too
    Rm -r tmp

## 4. Copy directory and all of its content
    Cp -r   my_dir1 /tmp/my_dir1
#  6. Vi Editor
    Command Mode (Default/ESC)
    Insert Mode(i)
## 1. Commands
	1. Move Around use arrow keys
	2.  Delete a character -X
	3.  dd - deletes entire line
	4.  yy - copy a line 
	5.  p - paste
	6. CTRL+U/D - scroll up/down
	7. :wq! //write save and exit
	8.  :q! //quit
## 2. Find
	1. /of   //highlights all occurrences of 'of' and cursor is positioned at first occurrence. To move to next occurrence press n key and again n for other occurrences.
# 7. UserAccounts
	1. Whoami  //to find the user logged in
	2. Id // give more details of user
	3. Su ravi //switch from one user to another 
	4. Ssh username@ipaddressofanothersystem //connecting to other linux system.
	5. If you see permission error on running a command say ls, run it as sudo ls …this way we are running the ls command with a root privilege by adding an entry into /etc/sudoers. The user is still a regular but elevataed privilege
# 8. Download Files from Internet
	1. curl http://example.download.com/somefile.txt -O outputdirectory // curl command to download a file from internet, -O is to save the result to a file.
	2. wget http://example.download.com/somefile.txt -O outputdirectory // curl command to download a file from internet, -O is to save the result to a file.
# 9. Check OS Version
	Cat /etc/*release*
# 10. Package Managers
    Centos uses RPM (Red Hat Package Manager)
    1. Rpm -I telnet.rpm // Install a package
    2. rpm -e telnet.rpm //Uninstall a package
  	3. Rmp -q telnet.rpm //query a package
    4. Rpm -qa  // to display the list of all packages installed.
    5. Rpm -qa | grep ansible //will fetch ansible packages installed.
    6. Yum repolist //this will list all the repositories
    7. These repositories are present in /etc/yum/repos.d
    Drawback is that rpm will not download the dependent package by itself. So the solution is another package manager YUM which uses RPM underneath.
	1. The repositories that yum searches for is at  /etc/yum/etc.repos.d directory
	2. Cat /etc/yum/etc.repos.d/
	3. cat /etc/yum.repos.d/CentOS-Linux-Devel.repo //will show the urls that this repo is using.
	4. Yum list ansible //list of packages installed.
	5. Yum remove ansible //to remove an installed package
	6. Yum --showduplicates list ansible //list of all versions of ansible packages
# 11. Services
## 1. Start HTTPD Service 
    Service httpd start  or 
    Systemctl start httpd
## 2. Stop the service
    Systemctl stop httpd 
## 3. check status of the service
    Systemctl status httpd
## 4. configure https to start at startup
    Systemctl enable httpd
## 5. disable the service start at bootup
    Systemtl disable httpd
## 6. Setup your app as a service.
    /etc/systemd/system/my_app.service
    [service]
    ExecStart=/usr/bin/python3 /opt/code/my_app.py

    [Install]
    WantedBy=multi-user.target

    System Reload
    Systemctl daemon-reload
    Systemctl start my_app
 
 # Shell Scripting
 export PATH = $PATH:/home/ravi

