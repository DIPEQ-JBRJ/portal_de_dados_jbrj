#Integração de Dados e Sistemas

Este Portal de Dados oferece ferramentas específicas para e integração dos nossos dados em outros sistemas, e para a integração de outros sistemas com nossos sistemas.

##Integração de Dados

Você pode usar nossos dados para integrar no seu sistema, "baixando" (*download*) os conjuntos de dados atualizados no formato [Darwin Core Archive](http://dadoswiki.jbrj.gov.br/doku.php?id=padroes#darwin_core), através da ferramenta [Integrated Publishing Toolkit (IPT)](http://www.gbif.org/ipt). O IPT é uma ferramenta de software livre de código aberto que é usado para publicar e compartilhar conjuntos de dados sobre biodiversidade através das redes SiBBr e GBIF. Projetado para a interoperabilidade, que permite a publicação de conteúdo em bancos de dados, os dados e metadados são publicados utilizando os padrões Darwin Core Archive e Ecological Metadata Language, respectivamente.

Temos dois IPTs funcionando hoje para ofertar conjuntos de dados para *download*:
- [IPT com dados das coleções institucionais e listas de espécies](http://ipt.jbrj.gov.br/jbrj/)
- [IPT com dados do Herbário Virtual REFLORA](http://ipt.jbrj.gov.br/reflora/)

Atenção |
--------|
**Note que os dados no IPT, oferecidos no formato *Darwin Core Archive*, são mais adequados ao consumo por "máquinas", ou seja, outros computadores. Caso deseje "baixar" nossos dados no formato de uma planilha eletrônica, por exemplo, use [esta ferramenta aqui](http://ckan.jbrj.gov.br/).**|

## Integração de Sistemas

Nossos dados também podem ser integrados a outros sistemas de forma dinâmica, atraves de uma [*Application Programming Interface* (API)](https://pt.wikipedia.org/wiki/Interface_de_programa%C3%A7%C3%A3o_de_aplica%C3%A7%C3%B5es) oferecida como um [*Web Service*](https://pt.wikipedia.org/wiki/Web_service) de baseada na tecnologia [REST](https://pt.wikipedia.org/wiki/REST).

Utilizamos a plataforma aberta [Swagger](http://swagger.io/) para oferecer três diferentes conjuntos de serviços:

- [Serviço de acesso à coleções institucionais via Sistema JABOT](http://servicos.jbrj.gov.br/jabot/)
- [Serviço de acesso à Flora do Brasil 2020 e a Lista Oficial de Plantas do Brasil](http://servicos.jbrj.gov.br/flora/)
- [Serviço de acesso aos dados do Centro Nacional de Conservação da Flora (CNCFlora) e a Lista de Espécies Ameaçadas de Extinção](http://cncflora.jbrj.gov.br/services/index.html)

A plataforma Swagger oferece uma interface amigável aos serviços. Entretanto, se necessitar de algum auxílio ou tivr críticas e sugestões à fazer, [entre em contato](http://dados.jbrj.gov.br/contato.php).

