## Encrypt & Decrypt with OpenSSL

### Basic commads
1. `openssl version`  
version of openssl  
    
2. `openssl list -cipher-commands`  
list cipher commads  
    
3. `nano msg`  
create a file _msg_  
**nano :** create file ,,   ^ == CTRL  
    
4. `cat msg`  
veiw file _msg_  
**cat :** view file  
    
### encrypt&decrypt AES algorithm 

1. `openssl enc -aes-256-cbc -base64 -in msg`  
encript file _msg_  
**algo :** aes-256 , **mod :** cbc (kind of secure)  
**in :** input is..  

-`openssl enc -aes-256-cbc -base64 -in msg -out enc`  
**out :** output is..
to store as a file _enc_

2 . openssl enc -aes-256-cbc -d -base64 -in enc  
decrypt file _enc_  
**d :** decrypt  

-`openssl enc -aes-256-cbc -d -base64 -in enc -k pass -out dec`
you can give key here allso
**k :** password

-`openssl enc -aes-256-cbc -d -base64 -in enc -out dec`
to store as a file _dec_

### encrypt&decrypt RSA algorithm 

**_CREAE NEW FOLDER B WITH IN THAT_**

1. `openssl genrsa -out keypairB.pen 2048`  
genrate rsa keypair   
**genrsa :** genrate rsa keypair
you can store keys with in (.pen file) 2048 bit




