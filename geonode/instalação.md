Primeiramente verifique se o repositório add-apt-repository está disponível

```
sudo apt-get install software-properties-common
sudo apt-get install python-software-properties
```


Configure o repositório PPA do Geonode

```
sudo add-apt-repository ppa:geonode/release
```

Instale o pacote do Geonode. Automaticamente ele irá instalar todas as depedências
```
sudo apt-get update
sudo apt-get install geonode
```

Após a conclusão da instalação do Geonode configure o usuário administrador

```
geonode createsuperuser
```

Configure o endereço IP do Geonode
```
sudo geonode-updateip <IP>
```
