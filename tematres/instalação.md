##Instalação Tematres

Extraia os arquivos de instalação do tematres no diretório /var/www/tematres

Edite o arquivo de configuração, o qual encontra-se em /var/www/tematres/vocab/db.tematres.php

Selecting the type of database server to use. If left blank it will use MySql.
$ DBCFG ["DBdriver"] = "";

IP address or name of the database server, for example, localhost
$ DBCFG ["Server"] = "localhost";
Name of the database
$ DBCFG ["DBName"] = "tematres";

User name to connect to the database
$ DBCFG ["dblogin"] = "root";

User password to connect to the database  
$ DBCFG ["dbpass"] = "";

Prefix for tables in this controlled vocabulary
$ DBCFG ["dbprefix"] = "LC_";

Acesse no browser o diretório de instalação do tematres
Será necessário informar o nome do seu vocabulário
