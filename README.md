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
## 6.1. Commands
	1. Move Around use arrow keys
	2.  Delete a character -X
	3.  dd - deletes entire line
	4.  yy - copy a line 
	5.  p - paste
		1. exit insert mode
		2. Go to the line that you want to copy and yy
		3. Go to the line where you want to copy and bp
		4. To copy multiple 3 line 3yy and bp
	6. CTRL+U/D - scroll up/down
	7. :wq! //write save and exit
	8.  :q! //quit
## 6.2 . Find
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
 
 # 7. Shell Scripting
	 export PATH = $PATH:/home/ravi
## 7.1 Find and replace all occurences in the file
	:s%/foo/bar/g  #replacing foo with bar globally.search and replace in entire file

## 7.2 user input
	read -p "Enter a value: " variable_name # this will prompt the user with the message to enter a value and is assigned to variable_name

## 7.3 Arithmetic operations
	echo expr $A + $B or
	echo $((A+B))
	echo $((A/B)) | bc -1 # to display the decimal values
## 7.4 Conditional Statement
	if [ expression ] 
	then
		#some statements
	elif
	then
		#some statements
	else
		#some statements
	fi
### 7.4.1 Operators
	[ string1 = string2 ] # notice the spaces between all keywords
	[ "abc" = "abc" ]     # string1 is equal to string 2
	[ "abc" != "abc" ]    # string1 is not equal to string2
	[ 1 -eq 5 ]	      # if number1 is equal to number 5
	[ 5 -ne 6 ]           # if number5 is not equal to number 5
	[ 5 -gt 7 ]           # if number 5 is greater than number 7
	[ 5 -lt 7 ]           # if number 7 is less than number 7
	[ -z $num ]           # check if num is passed as an argument while calling 
### 7.4.2 Logical Operators
	[ expr1 ] && [ expr2 ]
		or
	[[ expr1 && expr2 ]]
	
	[ expr1 ] || [ expr2 ] 
		or
	[[ expr1 || expr2 ]
### 7.4.3 directory exists
	if [ -d "/home/rgajul/mydir" ]
	then
  		echo "Directory exists"
	else
  		echo "Directory not found"
	fi
### 7.4.4 file system
	[ -e FILE ] # if file exists
	[ -d FILE ] # if directory exists
	[ -x FILE ] # if file is executable
	[ -w FILE ] # if file is writable
	[ -s FILE ] # if the file exists and the size is > 0
# 7.5 For Loop
	for num in 1 2 3 4 5
	do
		echo $num
	done
	
		or

	for num in {0..100}
	do 
		echo $num
	done
	
		or
		
	for num in $(cat num.txt)
	do
		echo $num
	done
# 7.6 While
	while true
	do 
		echo "1. Start"
		echo "2. restart"
		echo "3. stop
		read -p "Enter your choice: " choice
		if [ $choice -eq 1 ]
		then
			start 
		elif [ $choice -eq 2 ]
		then 
			restart
		elif [ $choice -eq 3 ]
		then
			break;
		else
			continue
		fi
	done
# 8 Case Statement
	while true
	do 
		echo "1. Start"
		echo "2. restart"
		echo "3. stop
		read -p "Enter your choice: " choice
		case $choice in
		   1) 
		   line 1 ....start
		   line 2 ......
		   line 3........
		   ;;
		   2)
		   line 1 ........
		   line 2 ........
		   ;;
		   3) break;;
		   *) continue;;
		esac
	done
# 9 SHEBANG
	#!/bin/bash # instruction in the first line of script to tell other users which shell the script would work on.Add The shebang line on the top of the script so that 	     even if the script is run from other unsupported shells(sh,dash,etc), it uses the /bin/bash interpreter
# References
	https://kodekloud.com/
