# Ejercicios tema 6

### 1. Instalar chef en la máquina virtual que vayamos a usar

Para instalar chef ejecutamos: `curl -L https://www.opscode.com/chef/install.sh | bash`

### 2. Crear una receta para instalar la aplicación que se viene creando en la asignatura en alguna máquina virtual o servidor en la nube.


### 3. Desplegar la aplicación de DAI con todos los módulos necesarios usando un playbook de Ansible.

Para desplegar la aplicación de DAI podemos usar el siguiente playbook

```yml
---
- hosts: all
  become: true
  remote_user: antonio

  vars:
    - homeDir: /home/ubuntu
    - appDir : dai
    - default: server {  listen 80; server_name YOUR_SERVERS_IP_ADDRESS;  location / { proxy_pass "http://127.0.0.1:8080"; proxy_http_version 1.1; proxy_set_header Upgrade $http_upgrade; proxy_set_header Connection 'upgrade'; proxy_cache_bypass $http_upgrade; }}

  tasks:

  - name: Add Mongo Key
    apt_key: id=EA312927  keyserver=keyserver.ubuntu.com

  - name: Add Mongo Repo
    apt_repository: repo='deb http://repo.mongodb.org/apt/ubuntu {{ansible_distribution_release}}/mongodb-org/3.2 multiverse'                                     

  - name: Update
    become: true
    shell: "apt-get update"

  - name: Install Packages
    apt: name={{ item }}  state=latest
    with_items:
      - build-essential
      - git
      - mcrypt
      - curl
      - mongodb-org
      - nginx  
      - django

  - name: Nginx reverse proxy
    pip:
    requirements: /home/ubuntu/dai/requirements.txt

```

### 4. Instalar una máquina virtual Debian usando Vagrant y conectar con ella.
Para instalar Debian y conectar podemos realizar lo siguiente:

```shell
  vagrant init debian/jessie64 
  vagrant up
  vagrant ssh
```

### 5. Crear un script para provisionar `nginx` o cualquier otro servidor web que pueda ser útil para alguna otra práctica

Para provisionar la máquina con `nginx` modificamos el `vagrantfile` que se generó al ejecutar `vagrant init debian/jessie64` y lo dejamos de la siguiente
forma:

```shell
Vagrant.configure("2") do |config|

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "debian/jessie64"


  #rsync (desactivado)
   config.vm.synced_folder ".", "/projectsrc", type: "rsync",
    rsync__exclude: ".git/", :disabled => true

  config.vm.provision "shell",
		inline: "apt install -y nginx"
end
```

### 6. Configurar tu máquina virtual usando vagrant con el provisionador chef.