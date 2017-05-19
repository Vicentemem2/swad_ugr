Práctica 4

Certificado SSL

En esta práctica vamos a instalar un certificado SSL autofirmado en nuestros servidores web, para ello ejecutamos los siguientes comandos:
a2enmod ssl
```shell
service apache2 restart
mkdir /etc/apache2/ssl
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt
```
Instalación de SSL:
<img src="https://github.com/Vicentemem2/swad_ugr/blob/master/practica4/img/intalacionSSLM1.PNG">

Después editamos el siguiente archivo: 
```shell
sudo nano /etc/apache2/sites-available/default-ssl
```
Y añadimos las siguientes líneas debajo de donde pone SSLEngine on:
```shell
SSLCertificateFile /etc/apache2/ssl/apache.crt
SSLCertificateKeyFile /etc/apache2/ssl/apache.key
```
Configuración de SSL:
<img src="https://github.com/Vicentemem2/swad_ugr/blob/master/practica4/img/configSSLM1.PNG">

Y finalmente reiniciamos apache:
```shell
a2ensite default-ssl
service apache2 reload
```

