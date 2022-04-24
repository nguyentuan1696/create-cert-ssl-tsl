
## 

## Install OpenSSL

## Command
https://man.openbsd.org/openssl.1

```
openssl req -x509 -newkey rsa:4096 -days 365 -keyout ca-key.pem -out ca-cert.pem
```
The -x509 option is used to tell openssl to output a self-signed certificate instead of a certificate request. In case you don’t know, X509 is just a standard format of the public key certificate.

The -newkey rsa:4096 option basically tells openssl to create both a new RSA private key (4096-bit) and its certificate request at the same time. As we’re using this together with -x509 option, it will output a certificate instead of a certificate request.

The next option is -days 365, which specifies the number of days that the certificate is valid for.

Then we use the -keyout option to tell openssl to write the created private key to ca-key.pem file

And finally the -out option to tell it to write the certificate to ca-cert.pem file.

```
cat ca-key.pem
```


## Private PEM pass phrase

```
demo123
```

## Verify a certificate
```
openssl verify -CAfile ca-cert.pem server-cert.pem
```