# PRACTICA-APACHE



## CARACTERÍSTICAS GENERALES DEL ARCHIVO DOCKER-COMPOSE.YML:


Se deben levantar dos servicios, uno de ellos con la imagen de apache y el otro con la imagen del servidor bind9.El primero de ellos ofrecerá el servicio de servidor web , mientras que el segundo tiene la tarea de resolver las peticicones de resolución de nombres de los dominios configurados.


A cada uno de los servicios se le asocia una IP fija dentro de una nueva red , especificando a a su vez los parámetros especícicos de esta en la sección network del archivo de configuración.

Los volúmenes asociados al servicio de apache constarán de dos directorios específicos , _www_ y _confApache_ , en donde se definirán los contenidos de los diferentes espacios web a servir , como la delimitación de los parámetros asociados al servicio de  hosting virtual.

En relación a los directorios vinculados a los volúmenes de bind9 se presentan _conf_ y _zonas_.
El primero de ellos tiene los archivos de configuración asociado a la delimitación de zonas o la especificación de los servidores reenviadores.
El segundo lleva a cabo el mapeo de las direcciones IP a los diferentes nombres de dominio



## EDICIÓN DE LOS DIFERENTES ARCHIVOS DE CONFIGURACIÓN 


En _www_ introducimos a través de archivos index.html los contenidos de los difeerentes sitios web a ofrecer.

En _confApache_ , más especificamente en _suitable-available_ describimos el contenido de las directivas asociadas a cada uno de los huépedes virtuales .

Aquí se especifica el nombre de dominio , los alias , los puertos implicados así como la ruta de dónde poder encontrar el contenido web a mostrar.


Para el caso del servicio DNS , se debe modificar el archivo SOA para mapear los nombres de dominio de los sitios web a una única IP que será la que de cabida a todos los espacios web.



## REDIRECCIONAR LA MÁQUINA ANFITRIONA.


Finalmente para que el sistema utilice el servidor DNS es necesario modificar el archivo de configuración system-resolved:

- Se debe abrir el archivo con permisos de administrador _sudo nano /etc/systemd/resolved.conf_.

- Posteriormente se modifica el parámetro que actua como apuntador de DNS: _DNS_=<IP DEL SERVER>#<PUERTO>










 








