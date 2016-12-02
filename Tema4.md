# Ejercicios tema 4

### 1. Instala LXC en tu versión de Linux favorita.
Lo instalamos mediante la orden: `sudo pacman -S lxc arch-install-scripts`

 La salida de `lxc-checkconfig` es:

 ```bash
--- Namespaces ---
Namespaces: enabled
Utsname namespace: enabled
Ipc namespace: enabled
Pid namespace: enabled
User namespace: missing
Network namespace: enabled

--- Control groups ---
Cgroup: enabled
Cgroup clone_children flag: enabled
Cgroup device: enabled
Cgroup sched: enabled
Cgroup cpu account: enabled
Cgroup memory controller: enabled
Cgroup cpuset: enabled

--- Misc ---
Veth pair device: enabled
Macvlan: enabled
Vlan: enabled
Bridges: enabled
Advanced netfilter: enabled
CONFIG_NF_NAT_IPV4: enabled
CONFIG_NF_NAT_IPV6: enabled
CONFIG_IP_NF_TARGET_MASQUERADE: enabled
CONFIG_IP6_NF_TARGET_MASQUERADE: enabled
CONFIG_NETFILTER_XT_TARGET_CHECKSUM: enabled
FUSE (for use with lxcfs): enabled

--- Checkpoint/Restore ---
checkpoint restore: missing
CONFIG_FHANDLE: enabled
CONFIG_EVENTFD: enabled
CONFIG_EPOLL: enabled
CONFIG_UNIX_DIAG: enabled
CONFIG_INET_DIAG: enabled
CONFIG_PACKET_DIAG: enabled
CONFIG_NETLINK_DIAG: enabled
File capabilities: enabled

Note : Before booting a new kernel, you can check its configuration
usage : CONFIG=/path/to/config /usr/bin/lxc-checkconfig
 ``` 
> Due to security concerns, the default Arch kernel does not ship with the ability to run containers as an unprivileged user; therefore, it is normal to see a missing status for "User namespaces" when running the check. 




### 6. Instalar docker.
```bash
sudo pacman -S docker 

systemctl start docker
systemctl enable docker

sudo gpasswd -a $USER docker

``` 


### 7.1 Instalar a partir de docker una imagen alternativa de Ubuntu y alguna adicional, por ejemplo de CentOS.
Para instlarlo se puede hacer uso directo de `docker run`:
``` bash
sudo docker pull ubuntu

sudo docker pull centos
```

### 7.1 Buscar e instalar una imagen que incluya MongoDB.

```bash
docker pull mongo
```

### 7 - Comprobación
```bash
docker images
//REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
//mongo               latest              86e302671af4        26 hours ago        401.9 MB
//ubuntu              latest              4ca3a192ff2a        2 days ago          128.2 MB
//centos              latest              0584b3d2cf6d        4 weeks ago         196.5 MB
```

### 8. Crear un usuario propio e instalar nginx en el contenedor creado de esta forma.

En primer lugar ejecutamos el contenedor con ubuntu:

```bash
docker run -i -t ubuntu /bin/bash
```

Instalamos sudo:
```bash
apt update
apt install sudo
```
Creamos el nuevo usuario y nos cambiamos:
```bash
root@20122cc1a18a:/# useradd antonio -m -s /bin/bash
root@20122cc1a18a:/# passwd antonio
//Enter new UNIX password: 
//Retype new UNIX password: 
//passwd: password updated successfully
root@20122cc1a18a:/# adduser antonio sudo  
root@20122cc1a18a:/# login antonio
//Password: 
//Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.8.9-1-MANJARO x86_64)
// .....
```

Instalamos NGINX:
```bash
sudo apt install nginx
```

### 9. Crear a partir del contenedor anterior una imagen persistente con commit.

Para este ejercicio en primer lugar obtenemos la id del contenedor y luego hacemos un commit.

```bash
docker ps -a | grep ubuntu 
// 20122cc1a18a        ubuntu              "/bin/bash"              14 minutes ago      Exited (0) 2 minutes ago                        peaceful_borg

docker commit 20122cc1a18a ejercicio9

//Comprobación

docker images

//REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
//ejercicio9          latest              c423cc4d7561        33 seconds ago      225.7 MB
//mongo               latest              86e302671af4        26 hours ago        401.9 MB
//ubuntu              latest              4ca3a192ff2a        2 days ago          128.2 MB
//centos              latest              0584b3d2cf6d        4 weeks ago         196.5 MB
```

### 10. Crear una imagen con las herramientas necesarias para el proyecto de la asignatura sobre un sistema operativo de tu elección.

```bash
docker run -i -t ubuntu /bin/bash

apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10

echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.0 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-3.0.list

apt update

apt install -y mongodb-org

apt install -y build-essential curl

curl -sL https://deb.nodesource.com/setup_7.x | bash -
apt install -y nodejs

```
Guardamos el contenedor:

``` bash
docker commit 20122cc1a18a proyecto

```