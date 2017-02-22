# webenvdev
Entorno de desarrollo web basado en Docker y Docker Compose
Esta version es especica para desarrollar proyectos con Magento 2

IMPORTANTE: esta versión aún esta bajo desarrollo.

<h3>Pre requisitos</h3>
Es necesario tener instalado en tu sistema:
- Docker
- Docker Compose
- Los puertos 80 y 3306 deben estar libres, esto significa que si la maquina anfitrion tiene un servidor web y mysql debemos detenerlos para usar el entorno de desarrollo virtualizado.

<h3>Instalacion</h3>
Clonar el repositorio
~/git clone git@github.com:olivertar/webenvdev.git

Ir a la carpeta "docker" dentro del directorio de instalacion
~/cd webenvdev/docker

Editar el archivo ".env" y modificar las variables si es necesario.
MYSQLROOTPASSWORD=garbanzo <- Es la clave del usuario Root de Mysql
BASEWWW=../../www <- Es la ruta, relativa al directorio webenvdev/docker donde estaran las carpetas con los archivos de nuestros proyectos.

Inicializar Docker
~/docker-compose up

Esta operacion solo se hace una vez y puede demorar un rato mas o menos largo mientras descarga e instala las imagenes de MySQL y PHP

Agregar a nuestro archivo hosts (/etc/hosts) las siguientes lineas
127.0.0.1 phpmyadmin.dev
127.0.0.1 myapp.dev
127.0.0.1 help.dev

<h3>Prueba</h3>
Si no hubo problemas en la instacion en http://help.dev deberiamos ver la informacion de PHP (phpinfo)

<h3>Uso</h3>
Para detener los contenedores el comando es:
~/docker-compose stop

Para reinicialos podemos usar:
~/docker-compose start mysql php7 nginx
o
~/docker-compose start

si necesitamos acceder al entorno por ssh:
~/docker exec -it php7 bash
y para cerrar la terminal:
exit






