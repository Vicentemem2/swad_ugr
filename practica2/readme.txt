Práctica 2
En esta práctica vamos a hacer:

	1. probar el funcionamiento de la copia de archivos por ssh
	2. clonado de una carpeta entre las dos máquinas
	3. configuración de ssh para acceder sin que solicite contraseña
	4. establecer una tarea en cron que se ejecute cada hora para mantener
	actualizado el contenido del directorio /var/www entre las dos máquinas

1.- Haciendo uso de tar czf - directorio | ssh equipodestino 'cat > ~/tar.tgz' podemos pasar mediante
la salida del pipeline la compresión del directorio por medio de ssh.

2.- Para clonar una carpeta entre las dos máquinas hacemos uso de chown y rsync:
	-> sudo chown vicente:vicente -R /var/www para hacer que el usuario de la otra máquina sea dueño
	del nuevo directorio.
	-> rsync -avz -e ssh 192.168.182.131:/var/www/ /var/www/ así clonamos la carpeta de una máquina
	a otra.

3.- Ahora vamos ha configurar ssh para que no haga falta introducir la contraseña para acceder 
desde una máquina a otra.
	-> ssh-keygen -b 4096 -t rsa (con esto tenemos la clave pública de ssh.)
	-> chmod 600 ~/.ssh/authorized_keys (copiamos la clave pública al equipo remoto
					    añadiéndola al fichero ~/.ssh/authorized_keys)
	->ssh-copy-id 192.168.182.131 (así copiamos la clave a la máquina deseada)
	->ssh 192.168.182.132 (ya no nos pedirá la contraseña)
Esto lo he realizado para las dos máquinas.

4.- Por último vamos a crear una tarea programada con el demonio cron para así tener siempre
vinculados las carpetas /var/www de las dos máquinas:
	-> creamos un script para ejercutarlo desde cron y le damos permisos de ejecución.
	-> vamos a cron con: sudo crontab -e y escribimos al final del archivo:
		45 * * * * vicente /home/vicente/p2sync.sh (con esto conseguimos que cada hora a 
							   y 45 se ejecute el script)
