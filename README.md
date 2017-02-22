# webenvdev
Entorno de desarrollo web basado en Docker y Docker Compose</br>
Esta versión es especifica para desarrollar proyectos con <strong>Magento 2</strong></br>

IMPORTANTE: <strong>esta versión aún está bajo desarrollo.</strong>

<h3>Pre requisitos</h3>
Es necesario tener instalado en tu sistema:
- Docker
- Docker Compose
- Los puertos 80 y 3306 deben estar libres, esto significa que si la maquina anfitrión tiene un servidor web y mysql debemos detenerlos para usar el entorno de desarrollo virtualizado.

<h3>Componentes</h3>
- MySQL 5.7
- Nginx
- PHP 7.0
- Librerias PHP
<ul>
<li>bc-math</li>
<li>curl</li>
<li>gd, ImageMagick</li>
<li>intl</li>
<li>mbstring</li>
<li>mcrypt</li>
<li>mhash</li>
<li>openssl</li>
<li>PDO/MySQL</li>
<li>SimpleXML</li>
<li>soap</li>
<li>xml</li>
<li>xsl</li>
<li>zip</li>
<li>json</li>
<li>iconv</li>
</ul>

<h3>Instalación</h3>
Clonar el repositorio</br>
~/git clone git@github.com:olivertar/webenvdev.git

Ir a la carpeta "docker" dentro del directorio de instalación</br>
~/cd webenvdev/docker

Editar el archivo ".env" (webenvdev/docker/.env) y modificar las variables si es necesario.</br>
MYSQLROOTPASSWORD=garbanzo <- Es la clave del usuario Root de Mysql</br>
BASEWWW=../../www <- Es la ruta, relativa al directorio webenvdev/docker donde estarán las carpetas con los archivos de nuestros proyectos.

Inicializar Docker</br>
~/docker-compose up

Esta operacion solo se hace una vez y puede demorar un rato mas o menos largo mientras descarga e instala las imagenes de MySQL y PHP

Agregar a nuestro archivo hosts (/etc/hosts) las siguientes lineas</br>
127.0.0.1 phpmyadmin.dev</br>
127.0.0.1 myapp.dev</br>
127.0.0.1 help.dev

<h3>Prueba</h3>
Si no hubo problemas en la instación en http://help.dev deberiamos ver la informacion de PHP (phpinfo)

<h3>Uso</h3>
Para detener los contenedores el comando es:</br>
~/docker-compose stop

Para reinicialos podemos usar:</br>
~/docker-compose start mysql php7 nginx</br>
o</br>
~/docker-compose start

si necesitamos acceder al entorno por ssh:</br>
~/docker exec -it php7 bash</br>
y para cerrar la terminal:</br>
>exit






