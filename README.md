# Dockerfile

### 1. Realiza una imagen personalizada de un ubuntu 22.04 que contenga: El comando "ip", comando "ping" y comando "dig".

Para ello, empezaremos creando un archivo llamado *Dockerfile* en la carpeta que quieras.

- Dentro de Dockerfile, metemos el siguiente código:
```
FROM ubuntu:22.04

ENV TERM linux
ENV DEBIAN_FRONTEND noninteractive

RUN apt update
RUN apt install -y emacs iproute2 dnsutils iputils-ping

CMD ["/bin/bash"]
```

### 2. Una vez realizada crea un repositorio en docker hub y súbela.

Antes que nada, debemos logearnos con docker para poder subir un repositorio y para ello haremos un **docker login**.

Posteriormente, nos pedirá el nombre y usuario. Ya estaremos dentro.

Ahora procedemos a crear y subir la imagen al repositorio. Para crearlo, simplemente vamos al apartado de *Repositories* y creamos.

- El primer comando será :
```
docker build -t pedrooasir/cliente_ubuntu:red .(Para construir la imagen con la etiqueta que estás intentando enviar)
```
- El segundo comando será :
```
docker push pedrooasir/cliente_ubuntu:red (Para subir la imagen con la etiqueta que quieras al repositorio.)
```

### 3. Pruébala con docker run.

```
docker run pedrooasir/cliente_ubuntu:red
```

Y listo, podemos ver en el VS que en "images" se encuentra la imagen que creamos junto a la etiqueta que le pusimos.


### 4. Realiza una segunda imagen con el servidor de apache, pero esta vez que incluya una página web personalizada.

El codigo del Dockerfile será:

```
FROM httpd:latest

COPY ./paginawebb /usr/local/apache2/htdocs/


ENV TERM linux
ENV DEBIAN_FRONTEND noninteractive

RUN apt update
RUN apt install -y emacs iproute2 dnsutils iputils-ping
```

Para el *COPY*, ponemos el html/pagina web donde se encuentra dentro del directorio de donde se encuentran los demas ficheros.

Es decir, cree un nuevo archivo llamado Dockerfile, donde dentro cree un fichero Dockerfile y una nueva carpeta para meter dentro de ella un html.

- Para construir la imagen con una etiqueta: **docker build -t pedrooasir/apache_personalizado .**

- Para ejecutar el contenedor en segundo plano (-d), mapeará el puerto 8080 de tu máquina host al puerto 80 del contenedor (-p 8080:80) y le dará al contenedor el nombre "mi_apache_personalizado": **docker run -d -p 8080:80 --name mi_apache_personalizado pedrooasir/apache_personalizado (Etiqueta)**


Finalmente ponemos : **http://localhost:8080** y ya podriamos ver el contenido de la página web.


- Para subirlo al docker hub: *docker image tag pedrooasir/apache_personalizado:latest pedrooasir apachee_personalizado:latest*

Y despues : *docker image push pedrooasir/apachee_personalizado:latest*

Es equivalente a : *docker image tag mi_imagen:mi_etiqueta mi_usuario/mi_repositorio:mi_etiqueta* y *docker image push mi_usuario/mi_repositorio:mi_etiqueta*