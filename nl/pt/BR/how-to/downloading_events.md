---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, download events

subcollection: cloud-activity-tracker

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}

# Fazendo download de eventos
{: #downloading_events}

É possível fazer download de eventos em um arquivo local. Você faz download de eventos no contexto de uma sessão. Uma sessão especifica quais eventos serão transferidos por download. Após a conclusão do download, deve-se excluir a sessão.
{:shortdesc}

O {{site.data.keyword.cloudaccesstrailfull}} foi descontinuado. A partir de 9 de maio de 2019, não é possível fornecer novas instâncias do {{site.data.keyword.cloudaccesstrailshort}}. As instâncias existentes do plano premium são suportadas até 30 de setembro de 2019. Para continuar o monitoramento da atividade de sua conta do {{site.data.keyword.cloud_notm}}, provisione uma instância do [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Conclua as etapas a seguir para fazer download de eventos em um arquivo local:

## Etapa 1: Efetuar login no {{site.data.keyword.cloud_notm}}
{: #prereq}

Efetue login no {{site.data.keyword.cloud_notm}}. Conclua
as etapas a seguir:

1. Execute o comando [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) para efetuar login no {{site.data.keyword.cloud_notm}}.
2. Execute o comando [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) para configurar a organização e o espaço nos quais você deseja provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}.

**Nota:** configure a organização e o espaço nos quais o {{site.data.keyword.cloudaccesstrailshort}} é provisionado.

## Etapa 2: identificar quais eventos estão disponíveis
{: #step2}

Use o comando `ibmcloud at status` para ver informações sobre os eventos disponíveis em um domínio de espaço.

* Para obter informações sobre eventos em um domínio de espaço, execute o comando `ibmcloud at status`.
* Para obter informações sobre eventos no domínio de contas, execute o comando `ibmcloud at status` com a opção `-a`.

Para obter mais informações, veja [Visualizando informações de evento](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status).
  


## Etapa 3: criar uma sessão
{: #step3}

Uma sessão é necessária para definir o escopo dos dados do evento que estão disponíveis para um download e para manter o status do download. 

Use o comando `ibmcloud at session create` para criar uma sessão. Por padrão, uma sessão inclui dados para as últimas 2 semanas.  Opcionalmente, é possível especificar a data de início e a data de encerramento ao criar uma sessão para especificar um intervalo de tempo, uma hora específica do dia e o escopo dos eventos. 

**Nota:** 

* Quando você especifica a data de início e a data de encerramento, a sessão fornece acesso a eventos entre essas datas inclusivas. 
* Não é possível fazer download de mais de 2 semanas de dados por sessão. Portanto, o intervalo de tempo deve ser menor que 2 semanas.
* É possível fazer download de eventos para um domínio de espaço ou para o domínio de contas em uma região.

Para criar uma sessão que seja usada para fazer download de eventos para uma data específica, execute o comando a seguir:

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25
```
{: codeblock}

A sessão retorna as seguintes informações:

* O intervalo de data a ser transferido por download.
* Informações sobre se devem ser incluídos eventos que estão disponíveis para a conta inteira ou apenas para o espaço atual. Por padrão, você obtém eventos para o espaço no qual efetuou login.
* O ID de sessão que é necessário para fazer download de eventos.
* O ID do usuário que cria a sessão.

Por
exemplo,

```
$ ibmcloud at session create
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

**Dica:** para ver a lista de sessões ativas, execute o comando `ibmcloud at session list`.

Por
exemplo,

```
ibmcloud at session list
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
ibmcloud at download -o Events_File_Name Session_ID
```
{: codeblock}

em que

* Events_File_Name é o nome do arquivo de saída.
* Session_ID é o GUID da sessão. Você obtém esse valor na etapa anterior. Use o valor para o campo **Id**.

Por
exemplo,

```
ibmcloud at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
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

Após o download ser concluído, deve-se excluir a sessão usando o comando `ibmcloud at session delete`. 

Execute o comando a seguir para excluir uma sessão:

```
ibmcloud at session delete Session_ID
```
{: codeblock}

Em que Session_ID é o GUID da sessão que você criou em uma etapa anterior. Use o valor para o campo **Id**.

Por
exemplo,

```
ibmcloud at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




