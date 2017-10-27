# laboratorio 2
# istruzioni per Kali: installazione di Damn Vulnerable Web Application (DVWA)

Eseguite i seguenti passi su bash: 

1. wget https://github.com/ethicalhack3r/DVWA/archive/master.zip 
2. unzip master.zip 
3. mv DVWA-master /var/www/dvwa
4. /etc/init.d/apache2 start
5. /etc/init.d/mysql start
6. mysql -u root

7. Incollare la query:
```
CREATE DATABASE dvwa;
GRANT ALL PRIVILEGES ON dvwa.* TO 'user'@'localhost' IDENTIFIED BY 'password';
```
8. Chiudere mysql con CTRL+D

9. Eseguire: 
```
cd /var/www/dvwa/config

mv config.inc.php.dist config.inc.php

nano config.inc.php
```

10. Sostituire la riga `$_DVWA[ 'db_user' ]     = 'root';` con `$_DVWA[ 'db_user' ]     = 'user';`

11. Sostituire la riga `$_DVWA[ 'db_password' ] = 'p@ssw0rd';` con `$_DVWA[ 'db_password' ] = 'password';`

12. Sostituire la riga `$_DVWA[ 'db_port '] = '5432';` con `#$_DVWA[ 'db_port '] = '5432';`

13. Eseguire: `nano /etc/apache2/sites-enabled/000-default.conf`

14. Sostituire la riga `DocumentRoot /var/www'/html` con `DocumentRoot /var/www`

15. Eseguire: `/etc/init.d/apache2 restart`

16. Connettersi al sito admin

17. Cliccare il bottone *Create Reset/Database*

18. Credenziali web application: *User "admin"* - *Password "password"*

19. Entrare su DVWA Security e impostare come *livello di sicurezza* "low".
