---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Alterando o plano
{: #change_plan}

É possível mudar seu plano de serviço do {{site.data.keyword.cloudaccesstraillong}} por meio da IU do {{site.data.keyword.cloud_notm}} ou executando o comando `ibmcloud service update`. É possível fazer upgrade ou reduzir seu plano a qualquer momento.
{:shortdesc}

## Mudando o plano de serviços por meio da UI
{: #change_plan_ui}

Para mudar seu plano de serviço por meio da IU do {{site.data.keyword.cloud_notm}}, conclua as etapas a seguir:

1. Efetue login no {{site.data.keyword.cloud_notm}} e, em seguida, clique no serviço do {{site.data.keyword.cloudaccesstraillong_notm}} no *Painel*. 
    
2. Selecione a guia **Plano**.

    São exibidas informações sobre o seu plano atual.
	
3. Selecione um novo plano para fazer upgrade ou reduzir o seu plano. 

4. Clique em **Salvar**.



## Mudando o plano de serviço por meio da CLI
{: #change_plan_cli}

Para mudar seu plano de serviço por meio da CLI, conclua as etapas a seguir:

1. Efetue login no {{site.data.keyword.cloud_notm}}. 

    Execute o comando [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) para efetuar login no {{site.data.keyword.cloud_notm}} e, em seguida, execute o comando [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) para configurar a organização e o espaço nos quais você deseja provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}.
	
2. Execute o comando `ibmcloud service list` para verificar seu plano atual e para obter o nome do serviço {{site.data.keyword.cloudaccesstrailshort}} na lista de serviços disponível no espaço. 

    O valor do campo **nome** é aquele que deve ser usado para mudar o plano. 

    Por
exemplo,
	
	```
	$ ibmcloud service list
    Invoking 'cf services'...

    Getting services in org MyOrg / space dev as xxx@ibm.com...
    OK

    name                       service                  plan                 bound apps                               last operation
    Activity Tracker-zt          OK                     accessTrail             premium                                update succeeded
    ```
	{: screen}
    
3. Faça upgrade ou reduzir seu plano. Execute o comando `ibmcloud service update`.
    
	```
	ibmcloud service update service_name [-p new_plan]
	```
	{: codeblock}
	
	em que 
	
	* *service_name* é o nome do seu serviço. É possível executar o comando `ibmcloud service list` para obter o valor.
	* *new_plan* é o nome do plano.
	
	A tabela a seguir lista os planos diferentes e seus valores suportados:
	
	<table>
	  <caption>Tabela 1. Lista de planos.</caption>
	  <tr>
	    <th>Planejar</th>
	    <th>Nome</th>
	  </tr>
	  <tr>
	    <td>Lite</td>
	    <td>grátis</td>
	  </tr>
	  <tr>
	    <td>Premium</td>
	    <td>Premium</td>
	  </tr>
	</table>
	
	Por exemplo, para reduzir o seu plano para o plano *Lite*, execute o comando a seguir:
	
	```
	ibmcloud service update "Activity Tracker-zt" -p free
    Updating service instance Activity Tracker-zt as xxx@ibm.com...
    OK
	```
	{: screen}



