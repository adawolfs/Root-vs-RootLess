## Process inspections tools
Ver detalles sobre un proceso en especifico.
```
ps -fea | grep COMMAND
```

Htop nos mostrara informacion util de varios procesos
```
htop
```

### Add subuids and subgids
Esto es necesario para permitir ejecutar contenedores como root.


https://www.redhat.com/sysadmin/rootless-podman

```
usermod --add-subuids 10000-65536 damien
usermod --add-subgids 10000-65536 damien
```
