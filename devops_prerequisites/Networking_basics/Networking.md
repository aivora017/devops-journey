## Switching

. if we want to create a network between 2 or multiple devices it should be connected to using switches. 
. Switch can be physical or virtual.
. when we want to connect 2 or multiple network we us a Router.
. each device in the network has its ip address throught which it can listen or can be accessed.
. a route can have maultiple ip addresses for different networks.

-> Gateways are important for a network to connect to different network
i.e. if thier is network X -> consist of a and b devices and thier is another network Y -> concsist of c and d devices then if a wants to ping to c even if it is connceted to the router it wont be able to access or ping c. if a wants to ping c it requires a gateway. which means the X network should have a gateway ip that will let X network devices to connect to  network devices.
if network is a like a room than gateways are like doors to access.

-> gatways can even be used to connect internet for the network
-> gatway entry has to be does on all the networks that needs to access the others.
-> weather the host can send packets to other network it is governed by settings at 
... cat/proc/sys/net/ipv4/ip_forward
it is default set to 0
 
## Commands

. ip link  -> it is used to see the interface name of the host.
. ip addr add 0.0.0.0 dev interface_name -> it is used to assign ip to the host interface.
. route -> it shows us the kernal table which contains all the interfaces and their ips on the current host. we can see gatway entries hear.
. ip route add 0.0.0.0/24 via 172.0.0.0 -> it is used to add ips and gateways to kernal table of the host interfaces.
0.0.0.0 -> it is a default gatway we can set it as 0.0.0.0 or can be set at default.
. cat/proc/sys/net/ipv4/ip_forward -> to check ip forward is enable 0 -> no 1-> yes
. etc/ system.conf/net.ipv4.ip_forward -> can be set to 1 for ip forwarding by default set to 0 will change to default we rebooted.

## DNS - domain name server

translating an ip address to hostname is called name resolution

. hostname -> this will reveal the host name 
. cat > etc/host -> here we can define the host name and ip that we wan to acess using the host name

A host name assigned in a system is true for only that system other cannot access it throught that host_name.

if others want to acess the same throught the same host name then entries has to be made in that systems host name.

in a network if we want all the systems to access it we will require the make entries in all the system which can cause an issue as a simple change can turn into a long process ao making entries.
to avoid that we commision a name server where we declare all the ips and hostname that is called as  DOMAIN NAME SERVER.

now all the machines will nly need a one entry here

. cat /etc/resolv.conf  
name_server  ip 

this will direct them to the name_server where all the hostname and their corresponding ips are saved.

any new entries can be made to the name server and that will automatically be acessable to all the host with access to the name server.


-> if we want to commission personal server we can still make changes or add entries to our 
>> etc/hosts
ip name 

-> every time we access a domain name first the host will checks it iown host fie and then the name server
but the order can be changed at 

. cat etc/nsswitch.conf
host :   file dns


in www.google.com

. -> root
.com -> is the top level domain
google -> name
maps drive www apps -> these are subdoamin

e.g maps.google.com   , apps.google.com


in a comapny we can have our own internal domain name server to acess compaines internal sites and servers.

e.g mycompany.com

subdomain -> mail, nfs, web, drive, www

dns will have entries like

192.168.1.10  web.mycompany.com
192.168.1.11 db.mycomapny.com
192.168.1.12 nfs.mycmopay.com
192.168.1.13 web-1.maycompany.com
192.168.1.14 sql.mycompany.com
 

to acess the above server we can make enteirs in our system as
cat >> etc/resolv.conf
nameserver 192.168.0.100

this will give acess to all the domain names in the name server

if we ping web from our system it will not reach the web.mycompany.com
when outsider want to acess the web.mycompany.com he will type the full
but if i want to acess it internally and want to use web in short i have to make changes to my resolv.cof file

cat >> etc/resolv.conf
search mycompany.com

now if i ping for web my system will search for web.mycompany.com
i can also say ping db or ping nfs
it will use it as a sub domain for mycompany.com


their are various record types that are stored in dns

			Record Type		Hostname		example Mapping
ip to hostname			A		Web_server		192.168.1.1
ipv6 to hostname		AAAA		web_server		2001:odb8:8sa3:0000:0000:8a2e:0370:7334
name to hostname 		CNAME		food.webserver		point to eat.web-server, hungry.web-server


to test Dns server some tools are used 

.nslookup name -> it queries the DNS server directly by passing the the local host
. Dig name ->  it gives more detailed info about the name in the dns server
