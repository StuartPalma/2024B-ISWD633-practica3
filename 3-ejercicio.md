## Esquema para el ejercicio
![Imagen](img/esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO
````
PS C:\Users\User> docker network create net-wp
ef06dd742c5940101d4cd58d98410c1e6a77c21d4a07e096c8438414415c0cc8
````

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es (/var/lib.mysql) 

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
````
Esta carpeta incialmente suele estar vacia, pero cuando el contenedor MYSQL se ejecuta se llena de varios archivos con
la configuracion y datos de las bases de datos que hayan sido creadas
````

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO
````
PS C:\Users\User> docker run -d --name contenedor-mysql --env-file=mysql1.env -v "C:/Users/User/Desktop/UNIVERSIDAD/construccion y evolucion de software/practica3/db:/var/lib/mysql" mysql:8
>> 
b761c532faf0864c44621206d521391566415c0c35df3fd72750d67767a21fbc
PS C:\Users\User> docker network connect net-wp contenedor-mysql (en caso de olvidarse de establecer la conexion)
````

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
````
se peude apreciar un montón de archivos relacionados con la base de datos y una base de datos con el nombre que yo coloque dentro del .env
utilizado para mi creacion
````

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es (wordpress:/var/www/html)

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO
````
PS C:\Users\User> docker run -d --name wordpress-container --network net-wp --env-file=wordpress.env "-p" 8083:80 -v "C:/Users/User/Desktop/UNIVERSIDAD/construccion y evolucion de software/practica3/www:/var/www/html" wordpress:latest
f41b549c9c373d7f266d76605b9720814d61f499de19a9e926c57ea05a90fe6f
````

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
````
Al eliminar y recrear el contenedor se observa que la configuración personalizada y las entradas se mantienen.
Esto sucede porque los datos persistentes se guardan en las carpetas montadas en el host 

````

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA



