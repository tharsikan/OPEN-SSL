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

1. `openssl enc -aes-256-cbc -base64 -in msg  
encript file _msg_  
**algo :** aes-256 , **mod :** cbc (kind of secure)  
**in :** input is..  

2 . `openssl enc -aes-256-cbc -base64 -in msg -out enc`  
to store as a file _enc_


