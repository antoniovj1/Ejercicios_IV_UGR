# Ejercicios tema 5

### 1. Instalar los paquetes necesarios para usar KVM. Se pueden seguir estas instrucciones. Ya lo hicimos en el primer tema, pero volver a comprobar si nuestro sistema está preparado para ejecutarlo o hay que conformarse con la paravirtualización.
Para comprobar que mi CPU soporta virtualización hago uso de la orden `egrep --color=auto 'vmx|svm|0xc0f' /proc/cpuinfo`.
Y compruebo que los modulos `kvm y kvm-intel` mediante el comando `zgrep CONFIG_KVM /proc/config.gz`.


### 2.1 Crear varias máquinas virtuales con algún sistema operativo libre tal como Linux o BSD. Si se quieren distribuciones que ocupen poco espacio con el objetivo principalmente de hacer pruebas se puede usar CoreOS (que sirve como soporte para Docker) GALPon Minino, hecha en Galicia para el mundo, Damn Small Linux, SliTaz (que cabe en 35 megas) y ttylinux (basado en línea de órdenes solo).

En primer lugar instalamos `Qemu` mediante la orden `sudo pacman -S qemu`.
Creamos un disco `qemu-img create -f qcow2 dsl.img 3G`.
Instalamos mediante la orden `qemu-system-x86_64 -m 1024 -hda dsl.img -cdrom Descargas/dsl-4.4.10.iso`
Podemos volver a iniciarla `qemu-system-x86_64 -m 2048 -hda dsl.img -kernel-kqemu`


### 2.2 Hacer un ejercicio equivalente usando otro hipervisor como Xen, VirtualBox o Parallels.
La instalación con VirtualBox se pude llevar a cabo mediante terminal o haciendo uso de la interfaz
gráfica, que es la que usaremos en este caso. El proceso es muy simple, hacemos click en `Nueva` y seguimos los
pasos que se indican. Una vez que han acabado, la seleccionamos y le damos a `Iniciar`, tras esto se nos pide
que se indique la localización de la imagen iso y con esto habremos terminado.



### 3. Crear un benchmark de velocidad de entrada salida y comprobar la diferencia entre usar paravirtualización y arrancar la máquina virtual simplemente con `qemu-system-x86_64 -hda /media/Backup/Isos/discovirtual.img


### 4. Crear una máquina virtual Linux con 512 megas de RAM y entorno gráfico LXDE a la que se pueda acceder mediante VNC y ssh.

### 5. Crear una máquina virtual ubuntu e instalar en ella alguno de los servicios que estamos usando en el proyecto de la asignatura.

### 6. Instalar una máquina virtual con Linux Mint para el hipervisor que tengas instalado.