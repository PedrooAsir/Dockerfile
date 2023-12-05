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
