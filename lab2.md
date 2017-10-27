# laboratorio 2
# istruzioni per Kali: installazione di Damn Vulnerable Web Application (DVWA)

Eseguite i seguenti passi su bash: 

1. wget https://github.com/ethicalhack3r/DVWA/archive/master.zip 
2. unzip master.zip 
3. mv DVWA-master /var/www/dvwa
4. /etc/init.d/apache2 start
5. /etc/init.d/mysql start
6. mysql -u root


Incollare la query:

CREATE DATABASE dvwa;
GRANT ALL PRIVILEGES ON dvwa.* TO 'user'@'localhost' IDENTIFIED BY 'password';


Chiudere mysql con CTRL+D



Eseguire:

cd /var/www/dvwa/config

mv config.inc.php.dist config.inc.php

nano config.inc.php



Sostituire la riga $_DVWA[ 'db_user' ]     = 'root'; con $_DVWA[ 'db_user' ]     = 'user';

Sostituire la riga $_DVWA[ 'db_password' ] = 'p@ssw0rd'; con $_DVWA[ 'db_password' ] = 'password';


Sostituire la riga $_DVWA[ 'db_port '] = '5432'; con #$_DVWA[ 'db_port '] = '5432';

Eseguire:
nano /etc/apache2/sites-enabled/000-default.conf

Sostituire la riga DocumentRoot /var/www'/html con DocumentRoot /var/www

Eseguire:

/etc/init.d/apache2 restart



Connettersi al sito admin

Cliccare il bottone Create Reset/Database

Credenziali web application: User "admin" - Password "password"

Entrare su DVWA Security e impostare come livello di sicurezza "low".
