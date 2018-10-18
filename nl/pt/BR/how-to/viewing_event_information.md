---

copyright:
  years: 2016, 2018
lastupdated: "2018-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Visualizando informações de evento
{: #viewing_event_status}

Use o comando `ibmcloud at status` para obter informações sobre os eventos que são coletados e armazenados no {{site.data.keyword.cloudaccesstrailshort}} para um espaço do {{site.data.keyword.Bluemix}}.
{:shortdesc}

É possível obter informações sobre o tamanho do log de eventos, o número de registros e se os eventos estão disponíveis ou não para análise no Kibana. 

Conclua as etapas a seguir para visualizar informações sobre o log de eventos:

## Etapa 1: Efetuar login no {{site.data.keyword.Bluemix_notm}}
{: #prereq}

Efetue login no {{site.data.keyword.Bluemix_notm}}. Conclua
as etapas a seguir:

1. Execute o comando [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) para efetuar login no {{site.data.keyword.Bluemix_notm}}.
2. Execute o comando [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) para configurar a organização e o espaço nos quais você deseja provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}.

**Nota:** configure a organização e o espaço nos quais o {{site.data.keyword.cloudaccesstrailshort}} é provisionado.

## Etapa 2: identificar quais eventos estão disponíveis
{: #step2}

Use o comando `ibmcloud at status` para ver informações sobre os eventos disponíveis em um domínio de espaço.

* Para obter informações sobre eventos em um domínio de espaço, execute o comando `ibmcloud at status`.
* Para obter informações sobre eventos no domínio de contas, execute o comando `ibmcloud at status` com a opção `-a`.

```
$ ibmcloud at status -a -s YYYY-MM-DD -e YYYY-MM-DD
```
{: codeblock}
    
em que
    
* *-a* é usado para especificar se a solicitação se aplica ao domínio de contas.
* *-s* é usado para configurar a data de início em Universal Coordinated Time (UTC): *AAAA-MM-DD*.
* *-e* é usado para configurar a data de encerramento em Universal Coordinated Time (UTC): *AAAA-MM-DD*.

Por exemplo, para ver quais eventos estão disponíveis para as últimas 2 semanas em um domínio de espaço, execute o comando a seguir:

```
$ ibmcloud at status
```
{: codeblock}
    
Por exemplo, a saída da execução desse comando é:
    
```
+------------+--------+------------+
|    DATE    |  COUNT | SEARCHABLE |
+------------+--------+------------+
| 2017-07-24 |    16  |    None    |
+------------+--------+------------+
| 2017-07-25 |   1224 |    All     |
+------------+--------+------------+
```
{: screen}

**Nota:** o serviço {{site.data.keyword.cloudaccesstrailshort}} é um serviço global que usa a Hora Universal Coordenada (UTC). Dias são definir como dias UTC. Para obter eventos para um dia de horário local específico, você pode precisar fazer download de múltiplos dias UTC.
	














