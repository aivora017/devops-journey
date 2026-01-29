## 12 Factor app Methodolog


1. codebase

we should have one codebase only like single place where all the code is stored multiple people can develop code on the respective machine but to avoids stepping and conflits singe codebase repo is used i.e gitbhub gitlab bitbucket

2. Dependencies

Different program has different set of dependecies used to avoid like diffrent tools or different version numbers so python uses requiremnet file to explicitly declare dependencies. the standard parctice is to use docker containers . Dependencies should  be explicitly declared and isolated

3. Concurrency 

Running ur application on multiple servers docker can provide scalabilty to run program for multiple user but it has limitation under incresed load so scalibilty should be horizontal across multiple servers using a load balancer it protects from faults and downtime even in peak load.

4. Processes

programs uses intance or session info it should not be embeded in program it should be stored in backing services which can be acessed by all the instance so their is no inconsistencey in data as programs can concurrently run on multiple instnace.

5. Backing Services

Backing servies are like email services (smtp) or storing images or instance data it should not be in a particular program code and sould be able to accessed from anywhere at any instance when required.

6. Config

Configuration should not be hardcoded it should be stored seperatl and should be dnamic to avoid problems in different intance like stage, dev and prod config is stored seperately to avoid conflits.

7. Build Release and Run

Build phase is converting our code to a binary or image so that it can run on other machices.
Release phase is we combine our image or binary file with config file and released. Each release should be taged or time stamped so it can be rolled back antime and can be tracked when released.
Run is the build artifact the is depeloyed across various environment i.e dev, testing, prod to maintain consistency this uniformity makes it easy  to rollback and rerelease anytime.

8. Port Binding

For environemts that hosts multiple services each services should bind to unique port to avoid conflits in services.

9. Disposability

Application shuld be able to start and stop in a momnets notice. while certain instancese are not in use the services or the instance should bbe able  to stop i.e docker uses sigterm and sigkill to terminate process as sigterm is sent first and some time after if process is not closed sigkill is send it is to give process enough time to close without losing data.

10. Dev Prod Parity

Between dev and prod many problem arises i.e time gap, personal gap, tool gap  to contraint these things the app is designed in such a way where devlopers are in both developing as well as prod watching and different backing services are resisted between dev and prod and a continious development is done to lower the gaps.

11. Logs

Logs should not be strored locally or in a logging instance process should not be concerned with routing or storage output stream. logs should be stored in a centred location and in a structed format so they can be used when required. logging services are used such as fluentd, splunk.

12. Admin Processes

Administrative process should  be kept  seperate from main process. the should be ran in an identical instance and should be scalable and reproducable i.e. reset, migrating db etc.


conclusion : the 12 factor app is a metedology that helps to build a highly reliable and scalabble program let it be a small scale microservice or a large scale enterprise .  
