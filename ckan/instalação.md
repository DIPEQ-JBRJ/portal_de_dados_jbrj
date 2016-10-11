##Instalação CKan

A instalação será realizada através do gerenciador de pacotes padrão do Ubuntu (apt) e do gerenciador de pacotes da linguagem Pyhton (pip) além de comandos executados no terminal do sistema operacional. Neste guia vamos utilizar um servidor recém instalado e dedicado ao Ckan. A instalação seguirá um passo a passo divido no seguinte esquema.
Sistema operacional: Atualização e preparação do ambiente para instalação do Ckan
Banco de dados: Instalação e configuração da base de dados do Ckan
Servidor de indexação: Instalação do SOLR
Tabelas do Ckan: Criar tabelas no Ckan
Webserver: Configuração do servidor web para disponibilizar o Ckan em produção


####Sistema Operacional

O sistema operacional deve ser atualizado com as versões mais recentes dos softwares já instalados. 
Como estamos usando um servidor recém instalado vou atualizar o SO sem preocupação de incompatibilidade com outros sistemas já instalados.

Atualize o sistema operacional
```
sudo apt-get update
sudo apt-get upgrade
```

Instale os pacotes necessários para criar o ambiente do Ckan
```
sudo apt-get install python-dev postgresql libpq-dev python-pip python-virtualenv     git-core solr-jetty openjdk-6-jdk
```

Prepare o ambiente Python onde o Ckan será instalado
```
mkdir -p ~/ckan/lib
sudo ln -s ~/ckan/lib /usr/lib/ckan
mkdir -p ~/ckan/etc
sudo ln -s ~/ckan/etc /etc/ckan
```

Crie o ambiente virtual (O ambiente virtual dive ficar ativo até o final da instalação. Caso haja reboot ou logout do usuário, deve ativar novamente o ambiente com o comando . /usr/lib/ckan/default/bin/activate).
```
sudo mkdir -p /usr/lib/ckan/default
sudo chown `whoami` /usr/lib/ckan/default
virtualenv --no-site-packages /usr/lib/ckan/default
 . /usr/lib/ckan/default/bin/activate
```

####Instalar o Ckan
```
pip install -e 'git+https://github.com/ckan/ckan.git@ckan-2.2#egg=ckan'
pip install -r /usr/lib/ckan/default/src/ckan/requirements.txt
deactivate
. /usr/lib/ckan/default/bin/activate
```

####Banco de dados

O banco de dados utilizado é o postgresql e será configurado para suportar o Ckan.

Verifique se o banco de dados já existe
```
sudo -u postgres psql -l
```

Crie o usuário do banco que será usado pelo Ckan e guarde a senha criada.
```
sudo -u postgres createuser -S -D -R -P ckan_default
```
    
Crie a base de dados
```
sudo -u postgres createdb -O ckan_default ckan_default -E utf-8
```

Crie o arquivo de configuração do Ckan
```
sudo mkdir -p /etc/ckan/default
sudo chown -R `whoami` /etc/ckan/
cd /usr/lib/ckan/default/src/ckan
paster make-config ckan /etc/ckan/default/development.ini
```

Edite o arquivo development.ini e altere a senha do banco onde está escrito “pass” e o endereço do banco onde está escrito “localhost” (caso necessário)
```
sudo vi /etc/ckan/default/development.ini
sqlalchemy.url = postgresql://ckan_default:<password><servidor>/ckan_default
```
 
####Servidor de indexação

O Solr é um servidor de busca de alta performance necessário para o bom funcionamento do Ckan.

Editar o arquivo de configuração /etc/default/jetty 
```
sudo vi /etc/default/jetty
```

Modificar as linhas abaixo
```
NO_START=0   
JETTY_HOST=127.0.0.1
JETTY_PORT=8983
JAVA_HOME=/usr/lib/jvm/java-6-openjdk-amd64/
```

####Iniciar o Solr

```
sudo service jetty start
sudo mv /etc/solr/conf/schema.xml /etc/solr/conf/schema.xml.bak
sudo ln -s /usr/lib/ckan/default/src/ckan/ckan/config/solr/schema.xml /etc/solr/conf/schema.xml
sudo service jetty restart
```


Testar o Solr e editar o arquivo /etc/ckan/development.ini
```
w3m http://localhost:8983/solr/
solr_url=http://127.0.0.1:8983/solr
```

####Tabelas do Ckan

Criação das tabelas necessárias para o funcionamento do Ckan.

Executar os comandos abaixo
```
cd /usr/lib/ckan/default/src/ckan
paster db init -c /etc/ckan/default/development.ini (Deve aparecer a mensagem Initialising DB: SUCCESS)
ln -s /usr/lib/ckan/default/src/ckan/who.ini /etc/ckan/default/who.ini
cd /usr/lib/ckan/default/src/ckan
paster serve /etc/ckan/default/development.ini
```

Testar o Ckan no terminal
```
w3m http://127.0.0.1:5000/
```

Caso tudo tenha sido instalado e configurado de maneira correta a tela inicial do Ckan deve aparecer no terminal


####Webserver

Após o Ckan ser instalado com sucesso vamos configurar o webserver para colocarmos o sistema em produção. 
No exemplo vou usar apache com o módulo wsgi. No site existem outras opções de instalação com outros webserver (http://docs.ckan.org/en/ckan-2.0/deployment.html)




