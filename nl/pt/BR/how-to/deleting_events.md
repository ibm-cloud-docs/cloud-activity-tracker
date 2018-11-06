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


# Excluindo eventos
{: #deleting_events}

Use o comando *ibmcloud at delete* para excluir manualmente os eventos que são armazenados no {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

Conclua
as etapas a seguir:

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

Para obter mais informações, veja [Visualizando informações de evento](/docs/services/cloud-activity-tracker/how-to/viewing_event_information.html#viewing_event_status).
	
  
## Etapa 3: excluir eventos
{: #step3}
	
Para excluir eventos, execute o comando `ibmcloud at delete`.

```
ibmcloud at delete -s YYYY-MM-DD -e YYYY-MM-DD
```
{: codeblock}
    
em que

* *-s* é usado para configurar a data de início em Universal Coordinated Time (UTC): *AAAA-MM-DD*.
* *-e* é usado para configurar a data de encerramento em Universal Coordinated Time (UTC): *AAAA-MM-DD*.

Por exemplo, para excluir os eventos para 10 de junho de 2017, execute o comando a seguir:

```
ibmcloud at delete -s 2017-06-10 -e 2017-06-10
```
{: screen}

Você recebe informações sobre os registros de eventos que foram excluídos.










