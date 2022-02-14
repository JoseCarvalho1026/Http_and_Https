# APACHE2
◻️ `apt update -y && apt upgrade -y` ;

◻️ `apt install apache2 -y` ;

◻️ `a2enmod ssl` ;

◻️ `a2ensite default-ssl.conf` ;

◻️ `systemctl restart apache2` ;

◻️ `nano /etc/apache2/sites-available/default-ssl.conf` ;
```
Change "DocumentRoot" to "htmls" ;
Change certificate names (see certificates) ;
```
To install the certificates, you must install "easy-rsa" [Certificates_Installation](https://github.com/JoseCarvalho1026/Certificates_Installation).

After installation and configuration do `./easyrsa build-server-full example.com nopass` and copy the "*.crt" and "*.key" to the respective places;

◻️ `cd /var/www/` ;

◻️ `cp -r html/ htmls` ;

◻️ `cd html/` ;

◻️ `nano html/index.html` (you are changing the :80, to make it easier to see the insecure) ;

◻️ `nano htmls/index.html` (you are changing the :443, to make it easier to see the safe) ;

◻️ `systemctl restart apache2` .

◻️ `systemctl status apache2` .
