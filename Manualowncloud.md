Para empezar he creado un directorio con el comando mkdir y lo he llamado "mkdir cloud", a partir de crear el directorio he comenzado a poner varios comandos para tener el vagrant que son:

   - vagrant init ubuntu/jammy64
   - vagrant up --provider=virtualbox
   - vagrant ssh
   - ll /vagrant

Una vez utilizado estos comandos y ser vagrant@ubuntu-jammy, tendremos que actualizar la maquina. Para poder actualizar la maquina primero de todo nos tendremos que hacer root con este comando:

   - sudo -s

Una vez somos root tendremos que poner uno de estos comandos que nos sirven para actualizar la maquina:

   - sudo apt update
   - sudo apt upgrade

Despues de actualizar la maquina he tenido que instalar varios servidores web que son los siguientes:

   - sudo apt install -y apache2
   - sudo apt install -y mysql-server
   - sudo apt install -y php libapache2-mod-php
   - sudo apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl

Y he despues he tenido que reiniciar el servidor apache2 con este comando para salir de root y seguircon la practica. El comando es este:

   - sudo systemctl restart apache2

Una vez instalado varios servidores web,lo que tendremos que hacer es configurar el MySQL y para poder acceder a la consola de MySQL habra que ejecutar el siguiente comando que dire ahora:

   - mysql

Una vez ya hemos entrado en la consola de MySQL tendremos que crear una base de datos para que nos pueda funcionar el owncloud y vaya todo bien. Es el siguiente comando:

   - CREATE DATABASE bbdd;

Despues de crear la base de datos, necesitamos crear un usuario con su contraseña para poder entrar en owncloud facilmente y que todo vaya bien: El comando es el siguiente:

   - CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

Una vez que hayamos creado nuestra base de datos y nuestro usuario con su perspectiva contraseña y darle privilegios, tendremos que salie de esta maquina para poder seguir con la instalación. El comando es el siguiente:
   - exit

Despues de haber salido de mysql, tendremos que ver con un usuario que no tenga permisos si somos capaces de conectarnos poniendo su contraseña. Es el siguiente comando:
   - mysql -u usuario -p
Una vez haber comprobado si nos podemos conectar a mysql, tendremos que ir a la pagina oficial de owncloud y descargarnos el archivo zip y tendremos que poner este comando:
   - mv /vagrant/owncloud.zip /var/www/html/

Una vez habernos bajado esto habra que descomprimirlo con el siguiente comando:
   - unzip owncloud.zip

Despues de descomprimir el archivo de owncloud, tendremos que crear un directorio en el cual daremos unos permisos. El directorio se llama:
   - cd /var/www/html
Y dentro de este directorio tendremos que poner estos comandos:
   - sudo chmod -R 775 .
   - sudo chown -R root:www-data

Despues de darle permisos a los archivos descomprimidos, tendremos que eliminar la versión de php 8.0 y nos tendremos que descargar la 7.4. Con los siguientes comandos:
   - apt-get remove php-common
   - add-apt-repository ppa:ondrej/php -y
   - apt install php7.4 php7.4-intl php7.4-mysql php7.4-mbstring \
       php7.4-imagick php7.4-igbinary php7.4-gmp php7.4-bcmath \
       php7.4-curl php7.4-gd php7.4-zip php7.4-imap php7.4-ldap \
       php7.4-bz2 php7.4-ssh2 php7.4-common php7.4-json \
       php7.4-xml php7.4-dev php7.4-apcu php7.4-redis \
       libsmbclient-dev php-pear php-phpseclib
   - update-alternatives --config php
Y para ver en que version estas de php es el siguiente comando:
   - php --version

Una vez habernos bajado la 7.4, tendremos que modificar varios parametros en el archivo. Con el siguiente comando:
  - vi vagrantfile

Y habra que configurar estos parametros:
   - # Create a forwarded port mapping which allows access to a specific port
# within the machine from a port on the host machine. In the example below,
# accessing "localhost:8080" will access port 80 on the guest machine.
# NOTE: This will enable public access to the opened port
config.vm.network "forwarded_port", guest: 80, host: 8080
   - # Create a public network, which generally matched to bridged network.
# Bridged networks make the machine appear as another physical device on
# your network.
config.vm.network "public_network"

                                                                                              



