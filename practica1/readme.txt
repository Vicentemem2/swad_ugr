Pr�ctica 1

->En esta pr�ctica tan solo hab�a que crear dos m�quinas.
->Instalar y configurar apache2, comprobar que funciona.
->Ver que las dos m�quinas tienen comunicaci�n entre si.
->Crear una p�gina para comprovar que apache funciona.

Para ver la versi�n de Apache2 tenemos que ejecutar apache2 -v y luego ps aux | grep apache para 
listarlos procesos que hay en ejecuci�n y poder observar que apache se est� ejecutando.

Podemos ver que las dos m�quinas tienen conexi�n a Internet y que se comunican entre ellas.
Hacemos ifconfig para ver la IP que tiene cada una y a continuaci�n ping a la otra m�quina para
comprobar que efectivamente se comunican entre s�.

Para comprobar que Apache funciona correctamente podemos acceder desde el navegador del Sistema Operativo
anfitri�n con la IP de una de las m�quinas para ver que efectivamente funcionan.