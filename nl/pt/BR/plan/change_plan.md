---

copyright:
  years: 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# Alterando o plano
{: #change_plan}

É possível mudar o seu plano de serviços {{site.data.keyword.cloudaccesstraillong}} em {{site.data.keyword.Bluemix_notm}} no Painel de serviços ou executando o comando `cf update-service`. É possível fazer upgrade ou reduzir seu plano a qualquer momento.
{:shortdesc}

## Mudando o plano de serviços por meio da UI
{: #change_plan_ui}

Para mudar o seu plano de serviços no {{site.data.keyword.Bluemix_notm}} no Painel de serviços, conclua as etapas a seguir:

1. Efetue login no {{site.data.keyword.Bluemix_notm}} e, em seguida, clique no serviço {{site.data.keyword.cloudaccesstraillong_notm}} por meio do painel do {{site.data.keyword.Bluemix_notm}}. 
    
2. Selecione a guia **Plano** na UI do {{site.data.keyword.Bluemix_notm}}.

    São exibidas informações sobre o seu plano atual.
	
3. Selecione um novo plano para fazer upgrade ou reduzir o seu plano. 

4. Clique em **Salvar**.



## Mudando o plano de serviço por meio da CLI
{: #change_plan_cli}

Para mudar seu plano de serviços no Bluemix por meio da CLI, conclua as etapas a seguir:

1. Efetue login em uma região, uma organização e um espaço do {{site.data.keyword.Bluemix_notm}}. 

    ```
    cf login -a Endpoint
    ```
    {: codeblock}
	
	Em que *Terminal* é a URL para efetuar login no {{site.data.keyword.Bluemix_notm}}. Essa URL é diferente por região.
	
	<table>
	    <caption>Lista de terminais para acessar o {{site.data.keyword.Bluemix_notm}}</caption>
		<tr>
		  <th>Região</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>Sul dos EUA</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
		<tr>
		  <td>Reino Unido</td>
		  <td>api.eu-gb.bluemix.net</td>
		</tr>
		<tr>
		  <td>Alemanha</td>
		  <td>api.eu-de.bluemix.net</td>
		</tr>
	</table>

    Siga as instruções. Insira suas credenciais do {{site.data.keyword.Bluemix_notm}}, selecione uma organização e um espaço. 

    Por exemplo, execute o comando a seguir para efetuar login na região Sul dos EUA:
	
	```
	cf login -a api.ng.bluemix.net
	```
	{: codeblock}
	
2. Execute o comando `cf services` para verificar seu plano atual e para obter o nome do serviço {{site.data.keyword.cloudaccesstrailshort}} na lista de serviços que está disponível no espaço. 

    O valor do campo **nome** é aquele que deve ser usado para mudar o plano. 

    Por
exemplo,
	
	```
	$ cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK
    
    name                            service              plan          bound apps      last operation
    Activity Tracker-oj            activityTracker       premium                       create succeeded
    ```
	{: screen}
    
3. Faça upgrade ou reduzir seu plano. Execute o `cf update-service` comando.
    
	```
	Cf update-service service_name [-p new_plan ]
	```
	{: codeblock}
	
	em que 
	
	* *service_name* é o nome do seu serviço. É possível executar o comando `cf services` para obter o valor.
	* *new_plan* é o nome do plano.
	
	A tabela a seguir lista os planos diferentes e seus valores suportados:
	
	<table>
	  <caption>Tabela 1.  Lista de planos.</caption>
	  <tr>
	    <th>Planejar</th>
	    <th>Nome</th>
	  </tr>
	  <tr>
	    <td>Lite</td>
	    <td>Lite</td>
	  </tr>
	  <tr>
	    <td>Premium</td>
	    <td>Premium</td>
	  </tr>
	</table>
	
	Por exemplo, para reduzir o seu plano para o plano *Lite*, execute o comando a seguir:
	
	```
	cf update-service "Activity Tracker-oj" -p lite
    Updating service instance Activity Tracker-oj as xxx@yyy.com...
    OK
	```
	{: screen}

4. Verifique se o novo plano é alterado. Execute o `cf services` comando.

    ```
	cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name                   service            plan      bound apps   last operation
    Activity Tracker-oj    activityTracker    lite                   update succeeded
	```
	{: screen}






