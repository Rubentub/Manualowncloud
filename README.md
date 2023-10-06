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

~                                                                                                                                                                                                           
~                                                                                                                                                                                                           
~                                                                                                                                                                                                           
~                                                                                                                                                                                                           
~                                                                                                                                                                    
