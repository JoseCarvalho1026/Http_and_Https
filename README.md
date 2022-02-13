# NGINX
◻️ `apt install nginx` ;

◻️ `apt install ssl-cert` ;

◻️ `cd /etc/nginx/snippets/` ;

◻️ `cp snakeoil.conf example.conf` ;

◻️ `nano example.conf` change certificate names (see certificates) ;

Para a instalação dos certificados deve instalar "easy-rsa" [Certificates_Installation](https://github.com/JoseCarvalho1026/Certificates_Installation).

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
