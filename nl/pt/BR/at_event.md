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



# Campos de eventos do Activity Tracker
{: #at_event}

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} são baseados no padrão Cloud Auditing Data Federation (CADF).
{:shortdesc}

## Campos do inicializador
{: #initiator}

A tabela a seguir lista os campos comuns que estão disponíveis para um evento do {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Campos do inicializador comum</caption>
  <tr>
    <th>Nome de Campo</th>
	  <th>Descrição</th>
    <th>Valor</th>
  </tr>
  <tr>
    <td>initiator.id</td>
	  <td>ID do inicializador da ação. </br>Há dois tipos de inicializadores: IBMID e serviceID.</td>
    <td>Exemplo de um IBMID: IBMid-000000XXX2 </br>Exemplo de um ID de serviço: iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	  <td>Nome do usuário que iniciou a ação.</td>
    <td></td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	  <td>Tipo da origem do evento.</td>
    <td>Os valores válidos são: *service/security/account/user*, *service/security/clientid*, *service/security/account/serviceid*</td>
  </tr>
  <tr>
    <td>initiator.credential.type</td>
	  <td>Tipo de credencial de ID do inicializador. </td>
    <td>Os valores válidos são: *user*, *token*, *apikey*</td>
  </tr>
</table>

## Campos de destino
{: #target}

A tabela a seguir lista os campos de destino comuns que estão disponíveis para um evento do {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Campos de destino comuns</caption>
  <tr>
    <th>Nome de Campo</th>
	  <th>Descrição</th>
    <th>Valor</th>
  </tr>
  <tr>
    <td>target.id</td>
	  <td>Nome do recurso em nuvem (CRN) do recurso no qual a ação é executada. </br>Para obter mais informações, consulte [Formato de CRN](/docs/overview/crn.html#format).</td>
    <td>Por exemplo: `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1`</td>
  </tr>
  <tr>
    <td>target.name</td>
	  <td>Nome legível do nome do recurso em nuvem no qual a ação é executada.</td>
    <td></td>
  </tr>
  <tr>
    <td>target.typeURI</td>
    <td>Tipo do recurso em nuvem no qual a ação é executada. </br>O formato desse campo é **serviceName/objectType**, em que servicename é o nome do serviço. </td>
	  <td>Por exemplo: `iam-am/policy` ou `cloud-object-storage/bucket/acl`</td>
  </tr>
</table>
 
## Campos de ação
{: #action}

A tabela a seguir lista os campos de ação comuns que estão disponíveis para um evento do {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Campos de ação comuns</caption>
  <tr>
    <th>Nome de Campo</th>
	  <th>Descrição</th>
    <th>Valor</th>
  </tr>
  <tr>
    <td>action</td>
	  <td>Ação que aciona o evento. </br>O formato desse campo é **serviceName.objectType.action**, em que servicename é o nome do serviço. </br>Para obter informações sobre eventos que são gerados por um serviço, veja <a href="/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services">Serviços do Cloud</a></td>
    <td>Por exemplo: *iam-identity.serviceid-apikey.login*</td>
  </tr>
  <tr>
    <td>eventTime</td>
	  <td>Indica o registro de data e hora de quando o evento foi criado. </br>A data é representada como Hora Universal Coordenada (UTC). </br>O formato está em conformidade com o ISO 8601.</td>
    <td>Por exemplo: 2017-10-19T19:07:50.32+0000<td>
  </tr>
</table>

## Campos de resultado
{: #outcomes}

A tabela a seguir lista os campos de resultados comuns que estão disponíveis para um evento do {{site.data.keyword.cloudaccesstrailshort}}:

<table>
  <caption>Campos de resultado comuns</caption>
  <tr>
    <th>Nome de Campo</th>
	  <th>Descrição</th>
    <th>Valor</th>
  </tr>
  <tr>
    <td>outcome</td>
	  <td>Resultado da ação. </td>
    <td>Os valores válidos são: *success*, *failure*, *pending*</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	  <td>Campo numérico que inclui o código de resposta HTTP.</td>
    <td>Por exemplo, *200* para um resultado bem-sucedido.</td>
  </tr>
  <tr>
    <td>severity</td>
	  <td>Define o nível de ameaça que uma ação pode ter sobre a Nuvem. </td>
    <td>Os valores válidos são: *normal*, *warning* e *critical* </br></br>**Normal** é configurado para ações de rotina na Nuvem. Por exemplo: iniciar uma instância ou atualizar um token. </br></br>**Warning** é configurado para ações em que um recurso em nuvem é atualizado ou seus metadados são modificados. Por exemplo: atualizar a versão de um nó do trabalhador, renomear um certificado ou renomear uma instância de serviço. </br></br>**Critical** é configurado para ações que afetam a segurança na Nuvem. Por exemplo: mudar as credenciais de um usuário, excluir dados, acesso não autorizado para trabalhar com um recurso em nuvem. </td>
  </tr>
</table>
