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

Y he despues he tenido que reiniciar el servidor apache2 con este comando para salir de root y seguircon la practica.
El comando es este:
 - sudo systemctl restart apache2

Una vez instalado varios servidores web,lo que tendremos que hacer es configurar el MySQL y para poder acceder a la consola de MySQL habra que ejecutar el siguiente comando que dire ahora:
 - mysql

Una vez ya hemos entrado en la consola de MySQL tendremos que crear una base de datos para que nos pueda funcionar el owncloud y vaya todo bien. 
Es el siguiente comando:
 - CREATE DATABASE bbdd;

Despues de crear la base de datos, necesitamos crear un usuario con su contraseña para poder entrar en owncloud facilmente y que todo vaya bien:
El comando es el siguiente:
 - CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

Una vez que hayamos creado nuestra base de datos y nuestro usuario con su perspectiva contraseña, le tendremos que dar privilegios para que pueda funcionar con normalidad:
El comando es el siguiente:
 - GRANT ALL ON bbdd.* to 'usuario'@'localhost';

Una vez que hemos creado nuestra base de datos, el usuario con su perspectiva contraseña 
