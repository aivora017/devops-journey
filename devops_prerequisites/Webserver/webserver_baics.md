## Web servers

webservers are servers and programs that handles the server side process
webframework handles the interaction between the client side and the server side 

e.g ecom websites have clint side where they show all the products
the clint side requests the procts info
the web freamework flask will handle the process of fetching the info from the web  server
the webserver have all the info and programs that needed by the client

client side code
html, css, java sccripts

server side code
java, python, js


static websites

gallery websides that have moslty images and bit styling
NGINX , Apache servers are good for such websites

dynamic websites

ecom that has various working and communication modles like payment support etc
Gunicorn, Apache tomcat, UWSGI are good for such websites


## Apache web server

commands

- yum install httpd -> install httpd apache is known as httpd server
- service start httpd -> to start an httpd service
- service status httpd -> to know the status of an httpd services
- systemctl start httpd -> to start an httpd servive when system uses a systemd 
- systemctl stop httpd -> to stop a service when server usesd a systemd
- firewall -cmd --permenant -- add-service =http firewall  -> adds httpd to firewall to allow services

#view logs
-> cat /var/log/httpd/acess_log
-> var/log/http/error_log

#Config File

/etc/httpd/conf/httpd.conf - it is a config file where configuration for the apache file is stored
default port 80 -  apache listens on this default port
the parameters in http.conf file

listen 80         - > default port apache listens too
document root "/var/www/"  -> defult directory where apps need to be stored to host
servername www.xyz.com:80 -> name to acess the app

we can deploy multiple app in a webserver but using
<virtualhost*80>
servername
document root 
</virtaulhost>

we can save easy virtual host config in a different file under /etc/httpd/conf
as name.conf
and then we can include these like in the  /etc/httpd/conf/httpd.conf as
include conf/name.conf
now we can acess the virtal host throught these server


## Apache Tomcat

- java is a pre requisite for apache tomcat
- wget <url to download apache tom cat>  -> it is used to download apache tomcat
- tar -xvf apachetomcat_filename  -> it is used to extract the doawnloaded file
- ./apache-tomcat-8.5.53/startup.sh -> it is used to start server
- http://localhost:8080 -> it is used to check the appache server running
- ls -l apache-tomcat-8.5.53/bin - > it is the folder where all the scripts and file to interact with the web server

- the bin had .sh and .bat files the .sh files are used for linux and .bat files are used for windows.
- in this file the startup and shutdown scripts are available
* Conf folder
server.xml -> the conf folder has the xml file where we can config the apache server like ports and etc

* webapps
- here we deploy the packages and app that we need to deploy on apache tomcat.


## deply a python flask app

- flask had a default port 5000
to deplay a flask app we ahve vaious tools 
- gunicorn : to delop with gunicorn commands (gunicon main:app)  -w can be used at end to add worker like -w 3 we can add  worker to run 4 instances of main app.
- uWSGl
- Gevent
- Twisted web


## Nodejs deploy express app
to  deploy a nodejs app
we used these commands 

- npm install -> install all the dependencies of the file
- node main.js -> to run the file as main it the entry poin do we use main.js

most of the apps has a pacakge.json file where thier are pre desined data to run the app like entry point and node_ env 
for that we can use 
-npm run start 
-npm run start:dev 
it will change apps behaviour according to suggested in node_env in package.json

it works well during dev phase but during deploying in prodction we need more robust maager so we use

PM2 -it is a production grade product process manager
it comes with aload balancer
commands 

- pm2 start app.js  -> it is used to run an app using pm2
- pm2 start app.js -i 4  -> it runs app using pm2 but with multiple instances in this case 4
-f can be used to force the process

- npm run start -> to run the 
 
## IP and PORTS

ip addr show - show the ip of the interface
ip addr add -  used to add ip address

when no host address is provided the host is redirected to a default address that is known as
loopback address
-ip a
 will give info about it
the default address for all the hosts is 172.0.0.1  and the standard name for it is localhoast

to edit a server.xml file when the acess is restricted we use

sudo sed -i 's/5000/8000/g' /apache-tomcat-11/conf/server.xml

sudo -(root privilages)
sed - strem editor
-i - insrest mode
s - substitue
5000 - what to substitue
8000 - what word to be placed as substitue
g - global occurance in the file
location of the file
