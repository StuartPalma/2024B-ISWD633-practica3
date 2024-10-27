# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](img/directorio.PNG)

### Crear un volumen tipo host con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](img/volumen-host.PNG)
# COMPLETAR CON EL COMANDO
````
PS C:\Users\User> docker run -d --name nginx-conatiner -p 8082:80 -v "C:/Users/User/Desktop/UNIVERSIDAD/construccion y evolucion de software/practica3/nginx/html:/usr/share/nginx/html" nginx:alpine
4f5c166b565eb8b4bf0c73af28afd97721423a68f94e649d48f2d3793362571a
````

### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
````
Aparece un mensaje de error porque no existe archivo index.html para que funcione
o existe otro caso que al crear con otra direccion te de la bienvenida a nginx 
````
### ¿Qué pasa con el archivo index.html del contenedor?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
````
No aparece con el metodo utilizado ya qu edeberiamos haberlo creado antes dentro
de la carpeta 

````

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
````
Al ingresar se puede ver como aparece una apgina web con el template descargado
````

### Eliminar el contenedor
# COMPLETAR CON EL COMANDO
````
PS C:\Users\User> docker rm -f nginx-conatiner  
nginx-conatiner
````

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
````
el contenido de la carpeta sigue igual a como lo dejamos antes de eliminarlo y esta disponible para el uso, ya que el mapeo de volumne tipo host
se mantiene en mi maquina aunque el contenedor sea eliminado
````

### ¿Qué hace el comando pwd?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
````
El comasndo PWD (Print Working Directory) muestra una ruta completa del directorio actual y es utilizado porque puedes referenciar la ruta exacta sin tener que escribirla manualmente 
````

Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

