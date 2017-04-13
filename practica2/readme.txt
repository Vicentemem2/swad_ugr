Pr�ctica 2
En esta pr�ctica vamos a hacer:

	1. probar el funcionamiento de la copia de archivos por ssh
	2. clonado de una carpeta entre las dos m�quinas
	3. configuraci�n de ssh para acceder sin que solicite contrase�a
	4. establecer una tarea en cron que se ejecute cada hora para mantener
	actualizado el contenido del directorio /var/www entre las dos m�quinas

1.- Haciendo uso de tar czf - directorio | ssh equipodestino 'cat > ~/tar.tgz' podemos pasar mediante
la salida del pipeline la compresi�n del directorio por medio de ssh.

2.- Para clonar una carpeta entre las dos m�quinas hacemos uso de chown y rsync:
	-> sudo chown vicente:vicente -R /var/www para hacer que el usuario de la otra m�quina sea due�o
	del nuevo directorio.
	-> rsync -avz -e ssh 192.168.182.131:/var/www/ /var/www/ as� clonamos la carpeta de una m�quina
	a otra.

3.- Ahora vamos ha configurar ssh para que no haga falta introducir la contrase�a para acceder 
desde una m�quina a otra.
	-> ssh-keygen -b 4096 -t rsa (con esto tenemos la clave p�blica de ssh.)
	-> chmod 600 ~/.ssh/authorized_keys (copiamos la clave p�blica al equipo remoto
					    a�adi�ndola al fichero ~/.ssh/authorized_keys)
	->ssh-copy-id 192.168.182.131 (as� copiamos la clave a la m�quina deseada)
	->ssh 192.168.182.132 (ya no nos pedir� la contrase�a)
Esto lo he realizado para las dos m�quinas.

4.- Por �ltimo vamos a crear una tarea programada con el demonio cron para as� tener siempre
vinculados las carpetas /var/www de las dos m�quinas:
	-> creamos un script para ejercutarlo desde cron y le damos permisos de ejecuci�n.
	-> vamos a cron con: sudo crontab -e y escribimos al final del archivo:
		45 * * * * vicente /home/vicente/p2sync.sh (con esto conseguimos que cada hora a 
							   y 45 se ejecute el script)
