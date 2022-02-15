# NGINX
◻️ `apt update -y && apt upgrade -y` ;

◻️ `apt install nginx -y` ;

◻️ `apt install ssl-cert -y` ;

◻️ `cd /etc/nginx/snippets/` ;

◻️ `cp snakeoil.conf example.conf` ;

◻️ `nano example.conf` change certificate names (see certificates) ;

To install the certificates, you must install "easy-rsa" [Certificates_Installation](https://github.com/JoseCarvalho1026/Certificates_Installation).

After the installation and configuration do `./easyrsa build-server-full example.example.com nopass` and copy the "*.crt" and "*.key" to the respective places.

Para aceder à internet, é necessário a configuração das portas do [Iptables](https://github.com/JoseCarvalho1026/Iptables/blob/main/Ubuntu.md).

◻️ `cd ../sites-available/` ;

◻️ `cp default safe` ;

◻️ `nano safe` change so that "htmls" works ;
```
delete lines :80
uncomment the lines :443
uncomment include snippets/snakeoil.conf;
change snakeoil.conf to example.conf
change root to htmls
```
◻️ `cd /var/www/` ;

◻️ `cp -r html/ htmls` ;

◻️ `nano html/index.nginx-debian.html` (you are changing the :80, to make it easier to see the insecure) ;

◻️ `cd htmls/` ;

◻️ `nano htmls/index.nginx-debian.html` (you are changing the :443, to make it easier to see the safe) ;

◻️ `cd /etc/nginx/sites-enabled/` ;

◻️ `ln -s /etc/nginx/sites-available/safe safe` ;

◻️ `systemctl restart nginx` ;

◻️ `systemctl status nginx` .
