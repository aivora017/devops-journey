
Commands

pushd/popd - it used to remember the main directory. 
e.g
pushd /etc   - this will set the pointer to /etc and get inside it then we can go to n number of directories inside the /etc and then when we type poopd we will again come to /etc directly

-r - flag can be used for recursive operations

cat > -> is used to write in a file directly
e.g
cat > file.txt - it will get to a new line for the input and then press ctrl+d it will write the like to the file.txt

touch file.txt -> it is used to create a new empty file

Pagers

pagers can be use to see the data in a file

more file.txt -> [space] scroll the diplay, one screeful of data at a time
                 [Enter] scroll the display by one line
                 [b] scroll the display backwards one Screenful of data at a time
                 [/] search te text
                 [q] exit

more is used to paste the full file on the screen.

less file.txt -> [up arrom] scroll up the display one line
                 [Down arrow] scroll the display one line
                 [/] - search text
ls -a - lists all the files including hidden files

. .. .test

. -> main directory
.. -> parent directory


ls -lt - list all the files in the order they were modified.
ls itr - list all the files in the reverse order they were created.


Help in Linux

whatis command - will give one line description about the command.
man command - most of the commands comes with a mannual to give detailed infor about the command.
command --help - it will list all the flags that can be used with the command
aprops command - it will search through the manual of the command and search for instances of the command. It is useful to look for all coammnds with the specific keyword
echo $SHELL - give us /bin/bash - tells us which shell are we currently using 
chsh - it is used to chamge the shell we are working on

BASH Shell Features

BASH has auto completion like typing intital some letters of the command and press tab to auto complete it.
we can add custom ALias in bash
i.e
alias dt= date - dt will now refer to date , insted to date we can directly write dt
history - it will give the list to commands executed

BASH Environment variable

env - to explore all the environment variables in the system

to set enviroment variable we use

export OFFICE = calston - it is used to set the environment variable for the shell and all the process running in the shell
OFFICE = caleston - it is used to set the enironment variable within the shell

To make the environmet variable persistant over the  reload and logins we add them to

~/.profile or ~/.pam_environment 

echo $PATH - paths are set for the commands and programs

which program_name - gives the location of the program set in the path

to set paths for the programs we use

export PATH = $PATH : path of program


Customised Promot

echo $PS1 - what is to disply on prompt

PS1 =  \d -date, \u - user, \h - host, \w - directory e.g PS1 = [\d]\u@]h:[\w]

Linux core Concepts

Kernal 

it is the core component between the harware and application and processes

Linux has a monolithic kernal architecture

Memory management
process management

they are monolithic 

device Drivers
system calls & security

they are modular

uname - disply name of kernal
uname -r to print the kernal version give 4.15.0-72-generic   4- kernal version, 15 - major version 0 - minor version 72 - patch release generic - distro specific info

kernal spcae
- kernal
- device driver

this executes and provides services  

this has the
- kernal code
- kernal extensions
- device driver

User space
application

it has all the programs like
- c
- java
- python
- ruby

user spcae to acess hardware make system calls tp kernal spcae and kernal space makes call th hardware

System calls

- open()
- close ()
- readedir()
- strlen()
- closedir()

dmesg to see the system logs when the system stratup
udevadm - managment tool for udev
udevadm monitor - monitor will print and recice events for udev events

lspci - list info about pci components
lsblk - list info about the disk

major number 
1 - RAM
3 - Harddisk or CDROM
6 - Parallel Printers
8 - SCSI disk

lscpu - list cpu architectures
lsmem --summary - is used to give the given infrastructure about the memory
free -m - total and used memeory in the system  -m -> gives in md, -k -> gives in kb, -G - gives in gb.
lshw - gives info on entire hardware of the system

Linux boot process

BIOS POST -> BOOT LOADER (GRUB2) -> KERNAL INITILIZATION -> INIT PROCESS (SYSTEMD)

POST - owner on self test

To check inti run

ls -l /sbin/init

it is used to check the run level set to what

Run level

5 - boots into graphical mode
3 - boots into a command line mode

In systemd  run levels are called targets

systemctl get-default - gets the defult run level
systemctl set-default - to set default run level in systemd

0 - poweroff.target
1 - rescue.target
2 - multi-user.target
3 - multi-user.target
4 - multi-user.target
5 - grapical.target
6 - reboot.target

File types in linux

Regular files - images, scripts, configuration and data
Directory - /home/bob - stores directory as well as other files
special files

charcter files - these files represent files under /dev file system that allows OS to connect IO devices serially e.g mouse/keyboard
Block files - represnt block devices e.g RAM
links - links have 2 types hard link and softlink
hard link - they are hard pointers to the files if deleted its permenant 
softlinks - these are like shortcuts can be deleted 

file file_name - gives the type of the file
ls -ld file_name - gives details about the file and its permisiions

e.g
drwxr-xr-x

d - Directory
(-) - regular file
c - character devices
l - links
s - socket files
p - Pipe files
b - block devices


File Hierarchy

/home - home directory
/opt - 3rd party apps
/mnt - mounting directory used to mount tempory files
/tmp - temp directory use to store temperory data
/media - all external media is mounted can be seen here -df -hP  -> prints details about the mounted filesystem
/dev - all the special files
/bin - basic program in binary i.e mv, cp,date
/etc - use to store configuration file
/lib - used to store all the shared libray
/usr - it is use to store all user lan aplication data e.g mail clients, browsers 
/var - it is used to store logs

their are many linux distributions in market so we classify them using pacakge managers used by them

.rpm - used by redhat, centos, fedora
.deb - used by ubuntu, mit linux, debian

package managers are softwares that provides a consistent and automated process of installing, upgrading, configuring and removing package in an OS.

Functions of package managers

- packing inegirty and authenticity
- simplified package management
- grouping packages
- managing dependencies

Types of package managers

DPKG
APT
APT-GET
these are used for debian based systems

RPM
YUM
DNF
these are used for redhat based systems

working with .rpm package managers

installing - rpm -ivh package.rpm 
uninstalling - rpm -e pacakage.rpm
upgrading - rpm -Uvh pacakage.rpm
query -  rpm -q package.rpm
verifying - rpm -vf package.rpm

despite all these .rpm doesnt solve the dependency problem

so we used YUM

YUM (yellow dog update modify) package manager

- RPM based distros
- software Repositors
- High level package manager
- automatic Dependency Resolution
it used file.rpo to install
it acess the repo to install packages that bundles with all the dependecies required to run a package
the repo can be stored locally or can be in remote location
local repo is store in - /etc/yum.rep.d

we can add new repos to this 

- yum install pacakge - intalls the package
- yum repolist - all the repos available in the yum repo locally
- yum provides command - used to know what to install for a specific command to run
- yum remove package - to uninstall
- yum update package - particular update a package
- yum update - update all the packages

DPkG UTLITY (DEBIAN PACAKGE MANAGER) (LOW LEVEL)

INSTALL - dpkg -i package.deb
uninstalling - dpkg -r package.deb
lists - dpkg -l package
status - dpkg -s package
verify - dpkg -p path

APT AND APT-GET
APT - advanced package tool 
better than apt get similar to yum

apt update - all update
apt upgrade - all upgrade
apt edit-scource - to update repo of apt
apt install package - to install
apt remove package - to uninstall
apt search package - to search a package in a repo
apt list | grep package - to get details of the package

Apt - gives output aas user friendly
apt search can be used to search all the package

apt-get - give output not user friendly
we have to use another tool apt-cache to search a package in apt-get

Show file size

du -sk file - file side in kb
du -sh file - file side in md
ls -h file - fives details and file size details

Archiving files

tar -cf tape archives

tar -cf file1 file 2 file3
tar -tf file.tar - to see contents a;of the tar ball
tar -xf file.tar  to extract the tar ball
tar -Zcf file.tar - to compress and reduce the file size

Compressing

bzip2 file.img
gzip file.img
xz file.img 

they are use to compress a file

uncompressing

bunzip2 
gunzip
unxz
are used to uncompress the files created by the above zips respectives

zcat - allows to read the contents of the file without uncompressing it

seacrh files and directories

locate filename - it uses a file db where location of all the files are saved and returns the loaction of the file
updatedb - the db uses to locate the file may not be updated so to update it run this command
find directory -name file_name - to search a file in a particular directory we can use find command with directory and -name flage and file name we r serching

to search within the file we use the GREP tool

grep word file.txt - to print with the searched word or pattern the defult search is case sensitive
grep -i word file.txt - it will search the word with case insensitive
grep -r word file.txt - it will search the word recursively inside the file
grep -v word file.txt - it will search the line that doent contain the word
grep -w word file.txt - it will search for the file with the whole word and not just instance i.e word and not wordly or wording
grep -vw word file.txt prints all the lines that have instance of the word and not the whole word
grep -A1 word file.txt - it will print the line with the word and one line that is after that line.
grep -B1 word file.txt - it will print the line with thw word and one line that is before that line the number can be any positive integer 
grep -A1 -B1 word file.txt - it will print the line with the word as well as one line after that line and before that line in total it prints 3 lines

To redirect stdout

-> > - forwrd arrow to write to a file
-> >> - to append to the file

to redirect stderr

2> - only error is written
2>> - it appends and not overwrite
2> /dev/bin - it is a bit bucket where al the garbage data is stored so no error will be printed

Command line pipes

It takes the stdout of the first command for input of the second command
command 1 | command 2
tee - command prints before overwriting
tee -a - appends and not overwrite

