##Instalação DSpace

1. Sistema Operacional

O sistema operacional deve ser atualizado com as versões mais recentes dos softwares já instalados. 
A instalação será baseada na documentação oficial e utiliza como base o pacote LAMP (Linux, Apache, MairaDB/Mysql e PHP) 
mesmo que esse guia use o banco postgresql. 
Como estamos usando um servidor recém instalado vamos atualizar o SO sem preocupação de incompatibilidade com outros sistemas 
já instalados.

Atualize o sistema operacional
```
sudo apt-get update
sudo apt-get upgrade
```

Instale o pacote LAMP e os pacotes maven e ant
```
sudo apt-get install tasksel
```

Selecione a opção LAMP e Tomcat Server
```
sudo apt-get install maven ant
```

Configure o Tomcat
```
vi /etc/tomcat7/server.xml
```

  Adicione as seguintes linhas ao final do arquivo mas antes da linha 
  ```</Host>
  <Context path="/xmlui" docBase="/dspace/webapps/xmlui"/>
        <Context path="/sword" docBase="/dspace/webapps/sword"/>
        <Context path="/oai"   docBase="/dspace/webapps/oai"/>
        <Context path="/jspui" docBase="/dspace/webapps/jspui"/>
        <Context path="/lni"   docBase="/dspace/webapps/lni"/>
        <Context path="/solr"  docBase="/dspace/webapps/solr"/>```



2. Banco de dados

O banco de dados utilizado é o postgresql e será configurado para suportar o DSpace

Verifique se o banco de dados já existe
Crie o usuário e acesse o servidor de banco de dados

3. Compilar e instalar o DSpace

Executar os comandos abaixo para instalar o DSpace.
```
mkdir /dspace
cd /dspace
git clone https://github.com/DSpace/DSpace.git
cd DSpace
sudo apt-get install openjdk-7-jdk
mvn package
cd dspace/target/dspace-4.2-build/
```

4. Ajustes

Ajustar permissões do Tomcat e desabilitar o Mysql.

```
cd /
chown tomcat7:tomcat7 /dspace -R
service tomcat7 restart
update-rc.d -f mysql remove
w3m http://localhost:8080/xmlui/
```


Caso tudo tenha sido instalado e configurado de maneira correta a tela inicial do DSpace deve aparecer no terminal
