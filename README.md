# Dockerfile

### 1. Realiza una imagen personalizada de un ubuntu 22.04 que contenga: El comando "ip", comando "ping" y comando "dig".

Para ello, empezaremos creando un archivo llamado *Dockerfile* en la carpeta que quieras.

- Dentro de este archivo creado, metemos el siguiente código:
```
FROM ubuntu:22.04

ENV TERM linux
ENV DEBIAN_FRONTEND noninteractive

RUN apt update
RUN apt install -y emacs iproute2 dnsutils iputils-ping

CMD ["/bin/bash"]
```