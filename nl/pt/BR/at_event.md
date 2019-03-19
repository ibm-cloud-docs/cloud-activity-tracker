---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Campos do evento
{: #at_event}

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} são baseados no padrão Cloud Auditing Data Federation (CADF). 
{:shortdesc}

## Campos do inicializador
{: #initiator}

A tabela a seguir lista os campos comuns que estão disponíveis para um evento do {{site.data.keyword.cloudaccesstrailshort}}:

| Nome de Campo | Descrição | Valor |
|------------|-------------|-------|
| `initiator.id` | ID do inicializador da ação. </br></br>Há diferentes tipos de inicializadores: IBMid, ID de serviço e identificação de usuário do Cloud Foundry (CF). | Exemplo de um IBMID: IBMid-000000XXX2 </br>Exemplo de um ID de serviço: iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14 </br>Exemplo de uma identificação de usuário do CF: 7666666b-23ae-4a34-8569-cu75tgdr4da3 |
| `initiator.name` | Nome do usuário que iniciou a ação. | Por exemplo, um endereço de e-mail. |
| `initiator.typeURI` | Tipo da origem do evento. | Os valores válidos são: *service/security/account/user*, *service/security/clientid* e *service/security/account/serviceid* |
| `initiator.credential.type` | Tipo de credencial de ID do inicializador. | Os valores válidos são: *user*, *token* e *apikey* |
{: caption="Tabela 1. Campos comuns do inicializador" caption-side="top"} 

  

## Campos de destino
{: #target}

A tabela a seguir lista os campos de destino comuns que estão disponíveis para um evento do {{site.data.keyword.cloudaccesstrailshort}}:

| Nome de Campo | Descrição | Valor |
|------------|-------------|-------|
| `target.id` | Nome do recurso em nuvem (CRN) do recurso no qual a ação é executada. </br>Para obter mais informações, consulte [Formato de CRN](/docs/overview?topic=overview-format-crn#format). | Por exemplo: `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1` |
| `target.name` | Nome legível do nome do recurso em nuvem no qual a ação é executada. |  |
| `target.typeURI` | Tipo do recurso em nuvem no qual a ação é executada. </br>O formato desse campo é **serviceName/objectType**, em que servicename é o nome do serviço. | Por exemplo: `iam-am/policy` ou `cloud-object-storage/bucket/acl` |
{: caption="Tabela 2. Campos de destino comuns" caption-side="top"} 


 
## Campos de ação
{: #action}

A tabela a seguir lista os campos de ação comuns que estão disponíveis para um evento do {{site.data.keyword.cloudaccesstrailshort}}:

| Nome de Campo | Descrição | Valor |
|------------|-------------|-------|
| `action` | Ação que aciona o evento. </br>O formato desse campo é **serviceName.objectType.action**, em que servicename é o nome do serviço. </br>Para obter mais informações sobre os valores de ação para eventos que são gerados por um serviço, consulte <a href="/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services">Serviços de nuvem</a> | Por exemplo: *iam-identity.serviceid-apikey.login* |
| `eventTime` | Indica o registro de data e hora de quando o evento foi criado. </br>A data é representada como Hora Universal Coordenada (UTC). </br>O formato está em conformidade com o ISO 8601. | Por exemplo: 2017-10-19T19:07:50.32+0000 |
{: caption="Tabela 3. Campos de ação comuns" caption-side="top"} 



## Campos de resultado
{: #outcomes}

A tabela a seguir lista os campos de resultados comuns que estão disponíveis para um evento do {{site.data.keyword.cloudaccesstrailshort}}:

| Nome de Campo | Descrição | Valor |
|------------|-------------|-------|
| `outcome` | Resultado da ação. | Os valores válidos são: *success*, *failure* e *pending* |
| `reason.reasonCode` | Campo numérico que inclui o código de resposta HTTP. | Por exemplo, *200* para um resultado bem-sucedido. |
| `severity` | Define o nível de ameaça que uma ação pode ter sobre a Nuvem. | Os valores válidos são: *normal*, *warning* e *critical* </br></br>**Normal** é configurado para ações de rotina na Nuvem. Por exemplo: iniciar uma instância ou atualizar um token. </br></br>**Warning** é configurado para ações em que um recurso em nuvem é atualizado ou seus metadados são modificados. Por exemplo: atualizar a versão de um nó do trabalhador, renomear um certificado ou renomear uma instância de serviço. </br></br>**Critical** é configurado para ações que afetam a segurança na Nuvem. Por exemplo: mudar as credenciais de um usuário, excluir dados, acesso não autorizado para trabalhar com um recurso em nuvem. |
{: caption="Tabela 4. Campos de resultado comuns" caption-side="top"} 


