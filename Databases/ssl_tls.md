### SSL & TLS Basics

ssl - it is known as secured socket layer
TLS - it is known as transfer layer security

Tls is a certificcate ensure that the server says who it is.

thier are 2 main types of encryption 

- symmetric Encryption
- asymmetric Encryption

# Symmetric Encryption

symmetric encryption is where a single key is used to encrypt and decript the data.

# Asymmetric Encryption

Asymmetric Encryption is where 2 keys are used one is public and other is private key 
we encrypt the data using the private key and we decrypt it using public key

why symmetric encryption is not safe as when we use symmetric encryption to communicate we encrypt the data with the key and then send the key with the encrypted data to the server so the server could decrypt using the same key but if someone spoof this communication they will get hold of the encrypt data as well as the key so they can decrypt it easily so we use Asymmetric Encryption.

to generate keys we use openssl

-> commands

. ssh-keygen -t -out id_rsa   - it generates 2 keys one private and one pub
.  ssh -i id_rsa user@server  - we use it to log into the server as a user with the key
. cat ~/.ssh/authorized_key  - here we can paste the keys so the server can use the keys to communicate we can have multiple entires for different keys and user.

to make the symmetric encryption safe we encrypt the data with the key and we use the asymmetric encryption and encrypt the symmetric key with the private key of asymmetric encryption and send it over.

- openssl genrsa -out my_user.key 1024
my_user.key         			- it creates an rsa key with 1024 bits

- openssl rsa -in my_bank.key -pubout > mybank.pem
my_bank.key my_bank.pem

for secure connection of your server server needs to be vailidated to validated the server we need a certificate know as tls certificate.

the certificate are validated using a sign
self signed certificate are not accepted and not safe  so we have authorities to sign a ceertificate know as Certificate Authorities (CA).
some CA e.g. - symatec, global sign digicert
to sign out certificate by CA we send them a CSR - Certificate signing Request

to generate a csr we use 

- openssl req -new -key my-bank.key -out my-bank.csr  -- this will led to a promte where we need to fill details and it gives out 2 files
my-bank.key   my-bank.csr

this is sent tp CA and they validate it using their privte key

the CAs have their public and private keys thier public key is with every browser to validate their signed certificates .

these CAs also alocatte private CAs for personal use
so we can even have a private CA for our own company servers

client certificate

- when we first acess the server a certificate is generated automatically during login to let the server know that you are a valid user.

these keys infrastructure is known as

PKI - public key infrastructure

their is a proper naming resolution for both public and private keys

certificate (public key) .crt and .pem

e.g. server.pem, server.crt, client.crt, clien.pem

certificate (private key)  .key and -key.pem

e.g server.key, server-key.pem, client.key, client-key.pem


commands

. ssh -keygen -t rsa -generate key - it is used to genertae rsa keys

. ssh-copy-id -i /home/thor/.ssh/mykey.pub thor@host  - it is used to copy mykey.pub to a server thor@host
. sudo chown owner:group:other  - it is used to change the ownership 
. sudo openssl req -new -newkey rsa:2048 -nodes -keyout app011key - out app01.csr     -> it is used to generate a csr request that need to be send to CA  i.e open ssl - using openssl , req - generating request for keys, - new -> request for new key, -newkey rsa:2048  -> the new key with rsa 2048 bits , -nodes -> for no parser ,  - keyout app01.key -> the ouput key name, -out app01.csr -> the out csr request
. sudo openssl req -x509 -nodes -days 36 -newkey ras:2048 -keyout app01.key -out app01.crt   -> if their is no CA a self signing can be done using this request i.e openssl req -> openssl request  , -x509 -> to generate a signing request, -nodes -> no parser required , -days 365  -> validity of the key is 36 days, -newkey rsa:2048 -> newkey with rsa 2048 bits, -keyout app01.key -> the key used to sign the certificate  , -out app01.crt  -> the signed certificate
