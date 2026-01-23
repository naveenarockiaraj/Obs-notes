curl http://192.170.0.106:8080/pki/vpn-ca/certs/ -X POST > inode.p12
openssl pkcs12 -in inode.p12 -passin pass: -nodes -nokeys -clcerts -out inode.pem -legacy
openssl x509 -in inode.pem -text
to alive the node add code in console![[Pasted image 20240821121959.png]]