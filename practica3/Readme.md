Práctica 3

Para esta práctica hemos creado una nueva máquina virtual, en la cual no hemos instalado Apache, así como se pedía en la práctica, para tener el puerto 80 libre.
Una vez creada esta máquina hemos instalado nginx.
```shell
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get
autoremove
sudo apt-get install nginx
sudo systemctl start nginx
```
Ahora lo que tenemos que hacer es cambiar la configuración de nginx, vamos a usar un algoritmo round-robin para gestionar las peticiones. En un principio todas van a tener la misma prioridad.

<img src="https://github.com/Vicentemem2/swad_ugr/blob/master/practica3/img/configNginx.PNG">
*Captura funcionamiento nginx*

```shell
service nginx restart
```
