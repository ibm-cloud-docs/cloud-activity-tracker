---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Visualizando informações de evento
{: #viewing_event_status}

Use o comando *cf at status* para obter informações sobre os eventos que são coletados e armazenados no {{site.data.keyword.cloudaccesstrailshort}} para um espaço do {{site.data.keyword.Bluemix}}.
{:shortdesc}

## Obtendo informações sobre eventos
{: #viewing_event_information}

Use o comando `cf at status` para visualizar o tamanho, a conta e se os eventos estão disponíveis ou não para análise no Kibana. Para obter mais informações, veja [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

1. Efetue login em uma região, uma organização e um espaço do {{site.data.keyword.Bluemix_notm}}. 

    ```
    bx login -a Endpoint
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
	</table>

    Siga as instruções. 

    Por exemplo, execute o comando a seguir para efetuar login na região Sul dos EUA:
	
	```
	bx login -a api.ng.bluemix.net
	```
	{: codeblock}
	
	Em seguida, configure a organização e o espaço. Execute o seguinte comando:

    ```
    bx target -o OrgName -s SpaceName
    ```
   {: codeblock}

    em que

    * OrgName é o nome da organização.
    * SpaceName é o nome do espaço.
    
2. Execute o comando *cf at status* para visualizar detalhes dos eventos que são coletados no {{site.data.keyword.cloudaccesstrailshort}}.

    ```
    $ bx cf at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
    ```
    {: codeblock}
    
    em que
    
    * *-a* é usado para especificar informações de nível de conta
    * *-s* é usado para configurar a data de início em Universal Coordinated Time (UTC): *AAAA-MM-DD*
    * *-e* é usado para configurar a data de encerramento em Universal Coordinated Time (UTC): *AAAA-MM-DD*
    	
	Use o comando `cf at status` com as opções **-s** para configurar o dia de início e **-e** para configurar a data de encerramento. Exemplo:

    * `bx cf at status` fornece informações para as últimas 2 semanas.
    * `bx cf at status -s 2017-05-03` fornece informações de 3 de maio de 2017 até a data atual.
    * `bx cf at status -s 2017-05-03 -e 2017-05-08` fornece informações entre 3 de maio de 2017 e 8 de maio de 2017. 
 
    Use o comando `cf at status` com a opção **-a** para configurar o domínio para a conta.
	
    Por exemplo, para obter informações sobre os eventos que estão disponíveis para 10 de junho de 2017, execute o comando a seguir:
    
    ```
    $ bx cf at status -s 2017-06-10 -e 2017-06-10
    +------------+-------+------+-----------------+------------+
    | Date       | Count | Size | Types           | Searchable |
    +------------+-------+------+-----------------+------------+
    | 2017-07-10 | 1     | 2531 | ActivityTracker | All        |
    +------------+-------+------+-----------------+------------+
    ```
    {: screen}
	














