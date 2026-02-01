## JAVA Basic

java is a programming langauge that is used to write programs and apps
many softwares that we use daily still run on java

# install java

. wget https//download.java.net   -> we can use the java website to get the latest tar version of java and paste the link with wget it will doanload java to our linux machine
. tar -xvf open.jdk-13.0.2- linux-bin.tar.gz -> the tar -xvf will ectrat and install the java in our machine
. jdk-13.0.2/bin/java -version  or java - version  -> these can be used to know the version of the java



jdk -> java development kit
it consist of various tools used to develop, build, run a program

develop tools

.jdb -> it is a debugger 
.javadoc -> to documnet the code

Build tools

.javac -> it is used to complile the code and build it
.jar -> it is used to archive the code libraries and all into a single file

run tools
.JRE -> java runtime environment  -> it is used to run the jar file
.java -> it is a command line utility where we can write commands to runand config the program

many more tools are present i just listed some of them we can see all the tools at 
ls jdk-13.0.2/bin

to set path for java
. export PATH = $PATH:/opt/jdk-13.0.2/bin

the process of build & packaging

build process -> develop sourave code i.e myclass.java -> compile (javac myclass.java) -> run (java myclass)

when we compile the compiler turns our code into a byte code
the byte code is a machine readbale code it is done inside jvm
jvm is java virtual machine it is different from our standard virtual machine it is javas internal environment where it changes our code to a byte code that is machine reable.

in run we used myclass not myclass.java to specify that myclass is the entry point of our program in the code



## Packaging

- to combine multiple files and dependencies in to one archine we use JAR - > java archive
- if we add some web application in that archive we have to archive it as a WAR -> web archive

commands

. jar cf name.jar file1 file2 file 3... -> this command is used to combine the files into a jar archive the output of this line is
name.jar -> this file contains a file called META-INF/manifest.mf
META-INF/manifest.mf -> this file contains all the meta data of the jar file like enrty points

. java -jar name.jar -> this command is used to run the jar file

. javadoc -d doc file.java -> this is used document the java file in java



## build tools

java have various build tools to create builds that can be distributed across vaiours machine

some of them are.

- Maven   -> it uses build.xml  -> sudo yum install -y maven 
- Gradle  -> sudo yum install -y Gradle
- ANT     -> sudo yum install -y ant

# ANT

. ant compile jar  -> to compile a jar file using ant
. ant -> to run a build
ant uses build.xml files to build a project

# maven

- sudo mvn package
- mvn clean install 
these codes are used to builf using mvn
it uses a pom.xml file to build a project

# Gradle
- ./gradlew build  -> use to build using gradle
- ./gradlew run   -> use to run using gradle
