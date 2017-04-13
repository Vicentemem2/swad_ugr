Práctica 1

->En esta práctica tan solo había que crear dos máquinas.
->Instalar y configurar apache2, comprobar que funciona.
->Ver que las dos máquinas tienen comunicación entre si.
->Crear una página para comprovar que apache funciona.

Para ver la versión de Apache2 tenemos que ejecutar apache2 -v y luego ps aux | grep apache para 
listarlos procesos que hay en ejecución y poder observar que apache se está ejecutando.

Podemos ver que las dos máquinas tienen conexión a Internet y que se comunican entre ellas.
Hacemos ifconfig para ver la IP que tiene cada una y a continuación ping a la otra máquina para
comprobar que efectivamente se comunican entre sí.

Para comprobar que Apache funciona correctamente podemos acceder desde el navegador del Sistema Operativo
anfitrión con la IP de una de las máquinas para ver que efectivamente funcionan.