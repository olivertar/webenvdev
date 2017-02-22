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

<h3>Virtual Host</h3>
Por ahora los crearemos manualmente.</br>
Los virtual host de Nginx estan definidos dentro de la carpeta "webenvdev/config/nginx".</br>
El archivo deberá tener el nombre del dominio y la extension ".conf".</br>
Un ejemplo de virtual host para Magento 2 es el archivo "mag2.conf"</br>
Si lo copiamos con el nombre de nuestro proyecto (miproyecto.conf), lo editamos y modificamos las variables:</br>
$MAGE_ROOT /var/www/html/<strong>miproyecto</strong>;</br>
server_name <strong>miproyecto</strong>.dev;</br>
y luego agregamos en nuestro archivo "hosts" (/etc/hosts) la linea: 127.0.0.1 <strong>miproyecto</strong>.dev</br>
nuestro virtual host deberia estar completamente configurado.

<h3>Document Root</h3>
El lugar donde se encuentran los archivos de nuestro proyecto esta determinado por la variable "BASEWWW" que hemos configurado anteriormente.</br>
Para el caso del ejemplo deberiamos crear una carpeta "miproyecto" dentro de la carpeta "www"</br>

<h3>Bases de Datos</h3>
Si bien podemos trabajar con la terminal o acceder con un administrador remoto, lo mas simple para proyectos simples muchas veces es usar PhpMyAdmin.</br>
El virtual host ya está configurado por defecto, solo debemos mover la carpeta "webenvdev/www/html/phpmyadmin" a la carpeta definida en la variable "BASEWWW" y apuntar nuestro navegador a "http://phpmyadmin.dev"</br>
El usuario es "root" y la clave, si no han modificado "MYSQLROOTPASSWORD", es "garbanzo".</br>
NOTA: cuando tengamos que configurar una coneccion a una base de datos como "host" debemos usar "mysql" en lugar de "localhost".

<h3>Acceso SSH</h3>
Si necesitamos acceder al entorno por ssh por ejemplo para instalar Magento 2 con composer</br>
~/docker exec -it php7 bash</br>
y para cerrar la terminal:</br>
>exit






