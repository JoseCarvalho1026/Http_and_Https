# APACHE

◻️ `yum install httpd -y` "apache" installation ;

◻️ `yum install mod_ssl -y` "ssl" installation;

◻️ `ln -s /etc/pki/tls/private private` creating a "soft link" from `/etc/ssl` pointing to `/etc/pki/tls/private` ;

To install the certificates, you must install "easy-rsa" [Certificates_Installation](https://github.com/JoseCarvalho1026/Certificates_Installation).

After the installation and configuration do `./easyrsa build-server-full example.example.com nopass` and copy the "*.crt" and "*.key" to the respective places;

```
example.example.com.crt file in /etc/pki/tls/certs
example.example.com.key file in /etc/pki/tls/private
```
◻️ `cp -r /var/www/html /var/www/htmls` copy folder "html" to "htmls";

◻️ `nano /etc/httpd/conf.d/ssl.conf` ;

Uncomment, replace the document root, and edit name server:
```
<VirtualHost _default_:443>

# General setup for the virtual host, inherited from global configuration
DocumentRoot "/var/www/htmls"
ServerName example.example.com:443
```
Comment this following lines;
```
#SSLProtocol all -SSLv3
#SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SEED:!IDEA
```
Then edit the certificates:
```
SSLCertificateFile /etc/pki/tls/certs/example.example.com.crt
SSLCertificateKeyFile /etc/pki/tls/private/example.example.com.key
```
◻️ `systemctl restart httpd` restart httpd ;

◻️ `systemctl status httpd` view httpd ;
