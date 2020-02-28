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

2. `openssl enc -aes-256-cbc -base64 -in msg -out enc`  
**out :** output is..  
to store as a file _enc_  

3. `openssl enc -aes-256-cbc -d -base64 -in enc`    
decrypt file _enc_  
**d :** decrypt  

4. `openssl enc -aes-256-cbc -d -base64 -in enc -out dec`    
to store as a file _dec_  

5. `openssl enc -aes-256-cbc -d -base64 -in enc -k pass -out dec`  
you can give key here allso  
**k :** password  

### encrypt&decrypt RSA algorithm   
_CREAE NEW FOLDER B WITH IN THAT_  
1. `openssl genrsa -out keypairB.pen 2048`       
genrate rsa keypair      
**genrsa :** genrate rsa keypair   
you can store keys with in (.pen file) 2048 bit   

2. `cat keypairB.pen`    	
just view    

3. `openssl rsa -in keypairB.pen -text`    
**text :** view all helper values to generate keypair  
**rsa :** deal with rsa  

4. `openssl rsa -in keypairB.pen -text -noout`  
noout : view key in base 16 formate  

5. `openssl rsa -in keypairB.pen -pubout`  
**pubout :** get the public_key from keypair so we can share it  

6. `openssl rsa -in keypairB.pen -pubout -out publicB.pen`  
just store that  


7. `ln -s /root/Desktop/TestOpenSSL/A/publicA.pen`  
get A's public key (just publicA.pen coppy here..B)  
**ln :** link   
**s :** source  

8. `openssl rsautl -encrypt -in msgg -out encc -inkey publicA.pen -pubin`  
encrypt msg by using A's public key  
**rsautl :** rsa utilities(operations)    
**encrypt :** encrypt msg by using A's public key   
**inkey :** use this key .. this may be certificate/ public_key   
**pubin :** so explicitly tell this is public key    


_CREAE NEW FOLDER A WITH IN THAT_    
1. `cp /root/Desktop/TestOpenSSL/B/encc received`  
coppy encrypted file _encc_ rename it as _received_  

2. `openssl rsautl -decrypt -in received -out msg -inkey keypairB.pen`  
**decrypt :** decrypt _encc_ by using A's private key (but keypaitB.pen)  
		

### sign with RSA algorithm  
1. `openssl rsautl -sign -in msgg -out signed -inkey keypairA.pen`  
**sign :** sign msgg by using own_private_key  


2. `openssl rsautl -verify -in signed -out signedFile -inkey publicA.pen -pubin`  
**verify :** verify the _signed_, by using his_public_key  

#### generate private-key  
1. `openssl rsa -in keypairA.pen -des3 -out privateA.pen`  
**des3 :** algorithm for encrypt privatekey  

2. `openssl rsa -in keypairB.pen -pubout -out publicB.pen`  
**pubout :** get the public_key so we can share it  

3. `openssl rsautl -sign -in msgg -out signed -inkey keypairA.pen`   
when sign you can use this.. private_key(encrypted), than use  keypair(plain text)  
		
