## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO

docker network create net-wp


### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Contiene los archivos del sistema de bases de datos de MySQL

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO

docker run -d --name mysql-wp --network net-wp -v "C:\Users\jaang\Desktop\ejercicio3\db:/var/lib/mysql" -e MYSQL_ROOT_PASSWORD=root123 -e MYSQL_DATABASE=wordpressdb -e MYSQL_USER=wpuser -e MYSQL_PASSWORD=wppass mysql:8


### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

Se crean automáticamente archivos y directorios internos de MySQL, es decir, la estructura de datos persistente de las bases de datos

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO

docker run -d --name wordpress-wp --network net-wp -p 9500:80 -v "C:\Users\jaang\Desktop\ejercicio3\www:/var/www/html" -e WORDPRESS_DB_HOST=mysql-wp:3306 -e WORDPRESS_DB_USER=wpuser -e WORDPRESS_DB_PASSWORD=wppass -e WORDPRESS_DB_NAME=wordpressdb wordpress

### Personalizar la apariencia de wordpress y agregar una entrada
<img width="1893" height="1018" alt="image" src="https://github.com/user-attachments/assets/6413294d-c2a6-4c96-a5ed-a28b9d635e46" />

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA 

Aunque el contenedor se eliminó, toda la configuración, temas, plugins y entradas se mantienen, porque los datos persistieron en los volúmenes montados en las carpetas del host
