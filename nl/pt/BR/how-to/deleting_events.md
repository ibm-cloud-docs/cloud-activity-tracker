---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, delete events

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

# Excluindo eventos
{: #deleting_events}

Use o comando *ibmcloud at delete* para excluir manualmente os eventos que são armazenados no {{site.data.keyword.cloudaccesstrailshort}}.
{:shortdesc}

O {{site.data.keyword.cloudaccesstrailfull}} foi descontinuado. A partir de 9 de maio de 2019, não é possível fornecer novas instâncias do {{site.data.keyword.cloudaccesstrailshort}}. As instâncias existentes do plano premium são suportadas até 30 de setembro de 2019. Para continuar o monitoramento da atividade de sua conta do {{site.data.keyword.cloud_notm}}, provisione uma instância do [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


Conclua
as etapas a seguir:

## Etapa 1: Efetuar login no {{site.data.keyword.cloud_notm}}
{: #deleting_events_prereq}

Efetue login no {{site.data.keyword.cloud_notm}}. Conclua
as etapas a seguir:

1. Execute o comando [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) para efetuar login no {{site.data.keyword.cloud_notm}}.
2. Execute o comando [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) para configurar a organização e o espaço nos quais você deseja provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}.

**Nota:** configure a organização e o espaço nos quais o {{site.data.keyword.cloudaccesstrailshort}} é provisionado.

## Etapa 2: identificar quais eventos estão disponíveis
{: #deleting_events_step2}

Use o comando `ibmcloud at status` para ver informações sobre os eventos disponíveis em um domínio de espaço.

* Para obter informações sobre eventos em um domínio de espaço, execute o comando `ibmcloud at status`.
* Para obter informações sobre eventos no domínio de contas, execute o comando `ibmcloud at status` com a opção `-a`.

Para obter mais informações, veja [Visualizando informações de evento](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status).
	
  
## Etapa 3: excluir eventos
{: #deleting_events_step3}
	
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










