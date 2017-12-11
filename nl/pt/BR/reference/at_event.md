---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Campos de eventos do Activity Tracker
{: #at_event}

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} são baseados no padrão Cloud Auditing Data Federation (CADF).
{:shortdesc}

## Campos do evento
{: #fields}

A tabela a seguir lista os campos que estão disponíveis para análise para um evento do {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Tabela 1. Campos que estão disponíveis para monitoramento por evento.</caption>
  <tr>
    <th>Nome de Campo</th>
	<th>Status</th>
	<th>Descrição</th>
  </tr>
  <tr>
    <td>outcome</td>
	<td>Necessário</td>
	<td>Os valores válidos são: *success*, *failure*</td>
  </tr>
  <tr>
    <td>typeURI</td>
	<td>Necessário</td>
	<td>Este campo é configurado para: *http://schemas.dmtf.org/cloud/audit/1.0/event*</td>
  </tr>
  <tr>
    <td>eventType</td>
	<td>Necessário</td>
	<td>Este campo é configurado para *activity*.</td>
  </tr>
  <tr>
    <td>eventTime</td>
	<td>Necessário</td>
	<td>A data é representada como uma sequência ISO, por exemplo: *2017-09-17 15:15:32.396 +0000 UTC*.</td>
  </tr>
  <tr>
    <td>action</td>
	<td>Necessário</td>
	<td>Este campo indica a ação que acionou o evento, por exemplo, *read.ibm-key-protect.secrets*.</td>
  </tr>
  <tr>
    <td>id</td>
	<td>Opcional</td>
	<td>Este campo contém o UUID do evento.</td>
  </tr>
  <tr>
    <td>initiator.id</td>
	<td>Necessário</td>
	<td>Este campo contém o ID para a origem do evento, como um ID da instância.</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	<td>Opcional</td>
	<td>Este campo fornece um nome legível para a origem do evento, como um ID do usuário.</td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	<td>Necessário</td>
	<td>Este campo informa sobre o tipo da origem do evento, por exemplo, *service/security/account/user*</td>
  </tr>
  <tr>
    <td>initiator.host.agent</td>
	<td>Opcional</td>
	<td>Este campo indica o cliente que foi usado para enviar a solicitação, por exemplo, *python-neutronclient* ou informações do navegador.</td>
  </tr>
  <tr>
    <td>initiator.host.address</td>
	<td>Opcional</td>
	<td>Este campo inclui o endereço IP do inicializador.</td>
  </tr>
  <tr>
    <td>target.id</td>
	<td>Necessário</td>
	<td>Este campo inclui o ID do serviço de destino.</td>
  </tr>
  <tr>
    <td>target.name</td>
	<td>Necessário</td>
	<td>Este campo inclui o nome legível do serviço de destino, por exemplo, *ibm-key-protect*.</td>
  </tr>
  <tr>
    <td>target.typeURI</td>
	<td>Necessário</td>
	<td>Este campo inclui o tipo do destino do evento, por exemplo, *service/ibm-key-protect/secrets*.</td>
  </tr>
  <tr>
    <td>target.host.address</td>
	<td>Opcional</td>
	<td>Este campo inclui o Endereço IP ou a URL do serviço de destino, por exemplo, *xxx.bluemix.net*.</td>
  </tr>
  <tr>
    <td>observer.name</td>
	<td>Necessário</td>
	<td>Este campo é configurado para o valor a seguir: *ActivityTracker*</td>
  </tr>
  <tr>
    <td>observer.id</td>
	<td>Necessário</td>
	<td>Este campo inclui informações sobre o recurso que cria e armazena o evento CADF, por exemplo, *activitytracker.ng.bluemix.net*.</td>
  </tr>
  <tr>
    <td>observer.typeURI</td>
	<td>Necessário</td>
	<td>Este campo é configurado para o valor a seguir: *service/security/edge/activity-tracker*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	<td>Opcional</td>
	<td>Este campo inclui o código de resposta de HTTP, por exemplo, *200* para sucesso.</td>
  </tr>
  <tr>
    <td>reason.reasonType</td>
	<td>Necessário</td>
	<td>Este campo inclui informações sobre o reasonCode quando um é fornecido por meio do campo *reason.reasonCode*.</td>
  </tr>
</table>

 

