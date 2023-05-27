
ref: [# Create Your Own SSL Certificate Authority for Local HTTPS Developmen](https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/)

ref: [# Generate an Azure Application Gateway self-signed certificate with a custom root CA](https://learn.microsoft.com/en-us/azure/application-gateway/self-signed-certificates)

# how to generate CA


```bash
# genrate private key
openssl genrsa -des3 -out myCA.key 2048


# generate CA 
openssl req -x509 -new -nodes -key myCA.key -sha256 -days 1825 -out myCA.pem


# add CA to device
# mac os
sudo security add-trusted-cert -d -r trustRoot -k "/Library/Keychains/System.keychain" myCA.pem

# linux 
sudo apt-get install -y ca-certificates
sudo cp ~/certs/myCA.pem /usr/local/share/ca-certificates/myCA.crt
sudo update-ca-certificates
# test
awk -v cmd='openssl x509 -noout -subject' '/BEGIN/{close(cmd)};{print | cmd}' < /etc/ssl/certs/ca-certificates.crt | grep Hellfish

# windows
# **Windows + R** and input mmc..... use search engine to find how to do this

# iOS: send an email to device

```


# how to generate .crt file

```
# use site name as filename is not required, 
# It only helps for manage 
openssl genrsa -out hellfish.test.key 2048

# then create ext file with SAN
# config spec here ->https://www.openssl.org/docs/man1.0.2/man5/x509v3_config.html

cat > heyyou.com.ext  <<EOF
authorityKeyIdentifier=keyid,issuer 
basicConstraints=CA:FALSE 
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment 
subjectAltName = @alt_names 

[alt_names] 
DNS.1 = hellfish.test
EOF



# generate 
openssl x509 -req -in hellfish.test.csr -CA myCA.pem -CAkey myCA.key \ -CAcreateserial -out hellfish.test.crt -days 825 -sha256 -extfile hellfish.test.ext

```

## a script can repeat to generate CRT


```bash
#!/bin/sh

if [ "$#" -ne 1 ]
then
  echo "Usage: Must supply a domain"
  exit 1
fi

DOMAIN=$1

cd ~/certs

openssl genrsa -out $DOMAIN.key 2048
openssl req -new -key $DOMAIN.key -out $DOMAIN.csr

cat > $DOMAIN.ext << EOF
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names
[alt_names]
DNS.1 = $DOMAIN
EOF

openssl x509 -req -in $DOMAIN.csr -CA ../myCA.pem -CAkey ../myCA.key -CAcreateserial \
-out $DOMAIN.crt -days 825 -sha256 -extfile $DOMAIN.ext
```