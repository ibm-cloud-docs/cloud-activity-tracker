---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, events

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
{:deprecated: .deprecated}


# Eventos do {{site.data.keyword.cloudaccesstrailshort}}
{: #events}

Use o serviço {{site.data.keyword.cloudaccesstrailfull}} para controlar o {{site.data.keyword.cloudaccesstrailshort}} no {{site.data.keyword.Bluemix}}. 
{:shortdesc}

O {{site.data.keyword.cloudaccesstrailfull}} foi descontinuado. A partir de 9 de maio de 2019, não é possível fornecer novas instâncias do {{site.data.keyword.cloudaccesstrailshort}}. As instâncias existentes do plano premium são suportadas até 30 de setembro de 2019. Para continuar o monitoramento da atividade de sua conta do {{site.data.keyword.cloud_notm}}, provisione uma instância do [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


## Lista de eventos
{: #actions}

A tabela a seguir lista as ações que geram um evento:

<table>
  <caption>Tabela 1. Lista de ações que geram um evento</caption>
  <tr>
    <th>Ação</th>
	  <th>Descrição</th>
  <tr>
  <tr>
    <td>read.events</td>
	  <td>Obtenha informações sobre os eventos que estão armazenados.</td>
  </tr>
  <tr>
    <td>create.sessions</td>
	  <td>Crie uma sessão que possa ser usada para fazer download de eventos.</td>
  </tr>
  <tr>
    <td>delete.session</td>
	  <td>Exclua uma sessão.</td>
  </tr>
  <tr>
    <td>read.sessions</td>
	  <td>Liste as sessões.</td>
  </tr>
  <tr>
    <td>download.events</td>
	  <td>Faça download de eventos.</td>
  </tr>
  <tr>
    <td>delete.events</td>
	  <td>Exclua eventos.</td>
  </tr>
</table>


## Onde procurar os eventos
{: #ui}
 	
Os eventos do {{site.data.keyword.cloudaccesstrailshort}} estão disponíveis no espaço do Cloud Foundry no qual o serviço {{site.data.keyword.cloudaccesstrailshort}} é provisionado.
