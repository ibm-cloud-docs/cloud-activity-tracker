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

# Fazendo download de eventos
{: #downloading_events}

É possível fazer download de eventos para um arquivo local ou dados do canal para outro programa. Você faz download de eventos no contexto de uma sessão. Uma sessão especifica quais eventos serão transferidos por download. Se o download dos eventos for interrompido, a sessão permitirá retomar o download de onde ele parou. Após a conclusão do download, deve-se excluir a sessão.
{:shortdesc}

Conclua as etapas a seguir para fazer download eventos que estão disponíveis em um espaço do {{site.data.keyword.Bluemix_notm}} em um arquivo local:

## Etapa 1: efetuar login no Bluemix
{: #prereq}

Antes de iniciar, efetue login em uma região, organização e espaço do {{site.data.keyword.Bluemix_notm}} em que o serviço {{site.data.keyword.cloudaccesstrailshort}} é provisionado. 

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

## Etapa 2: identificar quais eventos estão disponíveis
{: #step2}

1. Use o comando `cf at status` para ver quais eventos estão disponíveis.

    Por exemplo, para ver quais eventos estão disponíveis para as últimas 2 semanas, execute o comando a seguir:

    ```
    $ bx cf at status
    ```
    {: codeblock}
    
    Por exemplo, a saída da execução desse comando é:
    
    ```
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-24 |    16  | 3020  | ActivityTracker    |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-07-25 |   1224 | 76115 | ActivityTracker    |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}

    **Nota:** o serviço {{site.data.keyword.cloudaccesstrailshort}} é um serviço global que usa a Hora Universal Coordenada (UTC). Dias são definir como dias UTC. Para obter eventos para um dia de horário local específico, você pode precisar fazer download de múltiplos dias UTC.
	
	Para obter mais informações, veja [cf at status](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).


## Etapa 3: criar uma sessão
{: #step3}

Uma sessão é necessária para definir o escopo dos dados do evento que estão disponíveis para um download e para manter o status do download. 

Use o comando [cf at session create](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create) para criar uma sessão. Opcionalmente, é possível especificar a data de início e data de encerramento ao criar uma sessão. 

**Nota:** quando você especifica a data de início e a data de encerramento, a sessão fornece acesso a eventos entre essas datas inclusivas. 

Para criar uma sessão que é usada para fazer download de eventos para a data atual, execute o comando a seguir:

```
bx cf at session create 
```
{: codeblock}

A sessão retorna as seguintes informações:

* O intervalo de data a ser transferido por download. O padrão é a data UTC atual.
* Informações sobre se devem ser incluídos eventos que estão disponíveis para a conta inteira ou apenas para o espaço atual. Por padrão, você obtém eventos para o espaço no qual efetuou login.
* O ID de sessão que é necessário para fazer download de eventos.
* O ID do usuário que cria a sessão.

Por
exemplo,

```
$ bx cf at session create
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T10:29:28.541092735Z            |
| access-time  | 2017-07-25T10:29:28.541092735Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 32c657c5-31c0-4a3c-a139-b380871c737a      |
| space        | 66fe4565-abab-46c9-cdcd-qf4565342345      |
+--------------+-------------------------------------------+
```
{: screen}

**Dica:** para ver a lista de sessões ativas, execute o comando [cf at session list](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_list).

Por
exemplo,

```
bx cf at session list
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| Id                                   | Space                                |Username             | Create-time                    | Access-time                    |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| 32c657c5-31c0-4a3c-a139-b380871c737a | 66fe4565-abab-46c9-cdcd-qf4565342345 |xxx@yyy.com          | 2017-07-25T10:29:28.541092735Z | 2017-07-25T10:29:28.541092735Z |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
```
{: screen} 


## Etapa 4: fazer download de eventos para um arquivo
{: #step4}

Para fazer download dos eventos que são especificados pelos parâmetros de sessão, execute o comando a seguir:

```
bx cf at download -o Events_File_Name Session_ID
```
{: codeblock}

em que

* Events_File_Name é o nome do arquivo de saída.
* Session_ID é o GUID da sessão. Você obtém esse valor na etapa anterior. Use o valor para o campo **Id**.

Por
exemplo,

```
bx cf at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

O indicador de progresso é movido de 0 a 100% conforme os eventos são transferidos por download.

**Nota:** 

* O formato dos dados transferidos por download é compactado como JSON. Por exemplo, quando você fizer download de eventos em um sistema Linux, descompacte o arquivo ZIP do arquivo .gz e abra-o para ver os dados em formato JSON. 
* O JSON compactado é adequado para ingestão pelo ElasticSearch ou pelo Logstash. Por exemplo, se -o não for fornecido e você estiver trabalhando em um sistema Linux, os dados fluirão para o stdout para que seja possível canalizá-los diretamente em sua própria pilha Elástica.
* Também é possível processar os dados com qualquer programa que possa analisar JSON. 

## Etapa 4: Exclua a sessão

Após o download ser concluído, deve-se excluir a sessão usando o comando [cf at session delete](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete). 

Execute o comando a seguir para excluir uma sessão:

```
bx cf at session delete Session_ID
```
{: codeblock}

Em que Session_ID é o GUID da sessão que você criou em uma etapa anterior. Use o valor para o campo **Id**.

Por
exemplo,

```
bx cf at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




