---

copyright:
  years: 2016, 2018

lastupdated: "2018-07-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Eventos do {{site.data.keyword.cloudaccesstrailshort}}
{: #events}

Use o serviço {{site.data.keyword.cloudaccesstrailfull}} para controlar o {{site.data.keyword.cloudaccesstrailshort}} no {{site.data.keyword.Bluemix}}.
{:shortdesc}



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
