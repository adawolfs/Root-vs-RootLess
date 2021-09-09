# Podman 

Por default Podman es rootless.

## En nuevo usuario en el servidor.

Como administrador del area de servidores se nos ha solicidato agregar un nuevo usuario para un developer freelance que trabajara con el equipo. El usuario debe de poder ejecutar contenedores, debemos de evaluar las medidas de seguridad.



## Crear un nuevo usuario en el servidor
```
# adduser --uid 666 ---gecos '' damien
```

## Option 1: Ejecutar nuestro contenedor

### 
```
// Crear un contenedor de alpine con la raiz montada en el
$ podman run -v /:/rootfs --rm -it alpine:3.14 /bin/sh

// Solo si queremos mantener acceso a internet
# mount --bind /etc/resolv.conf /rootfs/etc/resolv.conf

// Let's hack it
# chroot /rootfs
```

