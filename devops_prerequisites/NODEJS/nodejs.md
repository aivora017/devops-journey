##Nodejs

it is a serverside javascript evn 
it handle large amount of concurrent connections  by implementing non blocking IO model.

# intall nodejs

- curl -sl http://rpm.nodesource.com/setup_13.x  -> it will add repo to the yum to install in out machine
- yum install nodejs -> it installs nodejs in the machine

# Commands

-node -V -> version of node js
-node run file.txt -> it is to run using nodejs


# Node package Manager (NPM)

#commands

- npm -V -> version
- npm search file-name -> it is used to seach the dependencies or lib and packages for node js
- npm install file-name -> it is used to install the packages for nodejs
- node -e "console.log(module.paths)" -> it is all the paths that node searches when we use the search command
- npm install file-name -g -> it is used to install the package gloablly not just inside the folder


# npm have some built-in modules

fs  -> to handle file system
http -> to host an http server
os -> to work with the os
events -> to handle the events
tls -> to implemets tls and ssh
url -> to parse the url string

more modules can be found on
- ls /usr/lib/node_modules/npm/node_modules/

# some external modules

express -> fast, unopionated, minimilistic, web framework
react -> to create user interface
debug -> to debug a program
async -> to work with asyncronous js
lodash -> to work with arry, objects, strings etc


