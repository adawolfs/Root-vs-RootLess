# Root-vs-Rootless
## Escalando permisos con contenedores.

Este proyecto es un laboratorio para evaluar posibles brechas de seguridad al ejecutar contenedores dentro de un sistema linux como usuario root.

## Motivation
Los contenedores son maquinas de software pontes, versatiles e inseguras por lo cual es necesario evaluar los riesgos y opciones disponibles.

## This lab

```
# head -2 /etc/os-release
NAME="Ubuntu"
VERSION="21.04 (Hirsute Hippo)"

# docker --version
Docker version 20.10.7, build 20.10.7-0ubuntu1~21.04.1

# podman --version
podman version 3.0.1
```

## Use-Case
Agregar un nuevo usuario a un servidor linux, permitirle ejecutar contenedores dentro del servidor. 

## Security implications
Por default docker ejecuta los contenedores como root, esto facilita el trabajo en construccion y ejecucion de contenedores para los developers, pero tambien facilita el trabajo a posibles atacantes.

Ejecutar contenedores como root en un sistema es considerado una vulnerabilidad ya que solo es necesario vulnerar un contenedor para obtener control de todo el sistema.



## Install versions.

```
# sudo apt update && sudo apt upgrade
# sudo apt install docker.io podman -y
```

## References

https://www.youtube.com/watch?v=jeTKgAEyhsA
https://www.youtube.com/watch?v=ZgXpWKgQclc
https://www.youtube.com/watch?v=Ac2boGEz2ww
https://www.youtube.com/watch?v=X446ptFGT1s
https://www.youtube.com/watch?v=Emt4rpjHdz0