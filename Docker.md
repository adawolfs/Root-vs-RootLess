## Docker 
Por default Docker ejecuta los contenedores como root

```
docker run --rm -it alpine:3.14 sh
```

## En nuevo usuario en el servidor.
Como administrador del area de servidores se nos ha solicidato agregar un nuevo usuario para un developer freelance que trabajara con el equipo. El usuario debe de poder ejecutar contenedores, debemos de evaluar las medidas de seguridad.



### Crear un nuevo usuario en el servidor
```
# adduser --uid 666 --gecos '' damien
```

### Option 1: Make the user a sudo(er)

#### Add user to sudo group
```
// Metodo: 1
# usermod -aG sudo damien
// Metodo: 2
# gpasswd -a damien sudo
```

#### Remove user from sudo group
```
# Option 1
deluser damien sudo
# Option 2
gpasswd -d damien sudo
```

### Option 2: Add user to docker group

#### Add user to docker group
```
# Option 1
usermod -a -G docker damien
# Option 2
gpasswd -a damien docker
```


#### Scale permissions.

```
// Crear un contenedor de alpine con la raiz montada en el
$ docker run -v /:/rootfs --rm -it alpine:3.14 /bin/sh

// Solo si queremos mantener acceso a internet
# mount --bind /etc/resolv.conf /rootfs/etc/resolv.conf

// Let's hack it
# chroot /rootfs
```


#### Remove user from docker group
It's always good to know how to clean your mess.
```
# Option 1
deluser damien docker
# Option 2
gpasswd -d damien docker
```

#### Identify user groups
```
groups damien
```


### Option 3: Use rootless docker.

https://docs.docker.com/engine/security/rootless/


Instalar rootless docker
```
$ curl -fsSL https://get.docker.com/rootless | sh
```

Iniciar rootless docker service
```
systemctl --user start docker
```

Definir el socket a utilizar
```
export DOCKER_HOST=unix://$XDG_RUNTIME_DIR/docker.sock
```


Uninstall

```
rootlesskit rm -rf ~/.local/share/docker
rm -rf .docker .local .config bin
```