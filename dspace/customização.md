####Arquivo de Configuração

```
/dspace/config/dspace.cfg
```


####Layout e CSS

```
Layout: /dspace/webapps/jspui/layout
CSS:    /dspace/webapps/jspui/static
```


####Linguagem

Configurar o português como linguagem padrão do DSpace
  Editar variável default.locale para pt_BR no arquivo de configuração
  
Configurar o formulário de entrada em português 
  Copiar input-forms_pt_BR.xml para ```/dspace/config/```
  Editar variável webui.supported.locales para pt_BR
  
Adicionar Português na lista de linguagem do fomulário
  Editar o arquivo /dspace/config/input-forms
  Em ```<value-pairs value-pairs-name="common_iso_languages" dc-term="language_iso">```
  Adicionar 
  ```
  <pair>
       <displayed-value>Português</displayed-value>
       <stored-value>pt_BR</stored-value>
  </pair>
  ```
