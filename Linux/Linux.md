why linux is important in DevOps because most of the DevOps tools are made for linux
e.g
Docker - it was only available for linux the windows version was release in 2016
Ansible - it requires linux environment to install even if it can manages windows as target system
Kubernetes - master node should be linux.



## Basic ##

linux has 2 inter face CLI and GUI

CLI - command line interface

# CLI Types :- Bourne shell (sh shell)
		C shell (csh or tcsh)
		Z shell (zsh)
		Bourne again shell (bash)
we can find which shell we are using by running
echo $shell
mostly expected output -> /bin/bash

## basic commands

echo hi -> echo command is used to print in linux
ls - list of files and folder in the directory
cd - it is used to change directory
pwd - tells us about the present working directory
mkdir dir_name - use to make new directory
; -  is used to execute multiple commands one after another e.g cd dir; echo file.txt

## Directories Command

mkdir -p /temp/asia/india -> this will create all the parent directories and set the directory structure -p is used for parent
rm -r dir_name -> it is uesd to remove the directory with all the contents in it
cp -r source destination - > it is used to copy the director from source to destination.

## files ComMans

touch file_name.txt -> create new file 
cat > file_name.txt -> it can be used to write inside the file after that ctrl +d is used to save . it can also be used to know the contents on the file
cp source destination -> it is used to copy files from source to destination.
mv source destination ->  it is used to move a file from source to destination is the source and destination is same and file name is different then file name is renamed.
rm file.txt -> it is used to remove a file

## vi Editor

vi file_name.txt - open filein vi editor

2 modes of operation availale in vi editor

command mode:- it is the by default mode we can navigate, can copy, paste and even delete but cannot write
insert moded :- i is pressed to enter insert mode here we can write back to command mode we need to press esc

-> To move around we can use  Arrow keys or K -up, h - left, l - right , j - down.
x -> delete 
yy -> copy
p -> paste
dd -> cut 
ctrl+u -> scroll up
ctrl +d ->scroll down
: -> takes to the last line prompt
:w -> save
:wq -> save and quit
:q -> quit
u -> undo the change
ctrl +r -> redo the changes
ctrl +y -> moves te cursor up
ctrl +x -> exit
/word -> find the word then n -> to find the rest of the word


## User Account commands

whoami -> which user you are 
id- tell you about ur unique id group id and others id
su user_name -> it is used to switch user
ssh username@host_id -> it is used to connect to servers and system using once systems 

* root user -> it has all the acess and can grant acess to other user
* normal user -> it has restricted acess can use sudo to use root acess

## Download Files command

curl http://www.some_site.com/file.txt -o destination/file_name.txt
 
weget http://www.some_site.com/file.txt -o destination/file_name.txt

both used to download file and if -o is not used it will print the content of the file on th prompt and not save it

## Check OSversion

ls /etc/*release* - gives informatoin about the os and its version
cat /etc/*release* - more details about the os

## Package Manager

RPM - red hat package manager

rpm -i package_name - > to install package
rpm -e package_name -> to remove a package
rpm -q package_name -> to query a package

while a package is intalled it required certain dependencies which is not taken care of by rpm so YUM is used
yum is a higher level of package manager that uses rpm underneth it install softwares with required dependencies.

yum install package_name -> to install package

yum Repository -> yum acess rpm from the repo needed for thr package it has a pre exsisting repo but sometime all packages will not be available so sometimes config needs to be changed.

yum repolist - > gives list of all the available repo
ls etc/yum.repos.d/ -> give us list of all the repo that are configures
cat /etc/yum.repos.d/package_name -> shows where  these ropes are configured and give details about the repo 
yum list package_name -> give us a list of all the intalled verions of the package name
yum remove package_name -> to remove a package
yum --show duplicate package_name -> list of all the version of the particular package
yum install package_name-version ->  install particular version of the package
rpm -qa | grep packagename  -> search for a particular package


## Services

services are apps that is used as a servies in other app or program

services name start -> start a service
or
systemctl start name -> starts a service 
systemctl stop name -> stops a service
systemctl status anme -> show status of the service
systemctl enable name -> configue it to start a service at startup
systemstl disable name -> configue it to not start a services at startup
systemctl cat app.services -> shows the apps services unit file

To run an app as a service we need to create a service at (/etc/systemd/system)
the service uses a unit file which consist of various parameter
i.e

[services]
execstart = command to run the services  -> start the service
execstartpre = command to run the services  -> it run before the servies is start like installing prerequisit
execstartpost = command to run the service -> it runs after the services is started like installinf dependencies etc

[Install]
wantedby = multi-user.target  -> if required to install some programs to run the services 

[unit]
Description = m pthon web app  -> use for metadata

restart = always -> if server crasesh and want to restart automatically

