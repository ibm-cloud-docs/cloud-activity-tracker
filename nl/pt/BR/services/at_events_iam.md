---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, IAM events

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


# Eventos do IAM
{: #at_events_iam}

Como um responsável pela segurança, auditor ou gerenciador, é possível usar o serviço {{site.data.keyword.cloudaccesstrailfull}} para controlar como os usuários e aplicativos interagem com o serviço do {{site.data.keyword.iamlong}} (IAM) no {{site.data.keyword.Bluemix}}. 
{:shortdesc}

O serviço {{site.data.keyword.cloudaccesstrailfull_notm}} registra atividades iniciadas pelo usuário que mudam o estado de um serviço no {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Sobre o {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

Para começar a monitorar as ações do usuário, veja [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla). 

Um inicializador pode ser um usuário, um serviço ou um aplicativo.
{: tip}

## Gerenciando eventos de grupos de acesso
{: #at_events_iam_access}

A tabela a seguir lista as ações que geram um evento:

| Ação | Descrição |
|----------|---------|
| `iam-groups.group.create`   | Um evento é gerado quando um inicializador cria um grupo de acesso. | 
| `iam-groups.group.read`     | Um evento é gerado quando um inicializador consulta informações que estão relacionadas a grupos de acesso. |
| `iam-groups.group.update`   | Um evento é gerado quando um inicializador atualiza um nome de grupo ou uma descrição. |
| `iam-groups.group.delete`   | Um evento é gerado quando um inicializador exclui um grupo de acesso. |
| `iam-groups.member.add`     | Um evento é gerado quando um inicializador inclui um membro em um grupo de acesso. |
| `iam-groups.member.delete`  | Um evento é gerado quando um inicializador remove um membro de um grupo de acesso. |
| `iam-groups.member.read`    | Um evento é gerado quando um inicializador verifica a associação de um membro. |
| `iam-groups.rule.read`      | Um evento é gerado quando um inicializador visualiza uma regra em um grupo de acesso. |
| `iam-groups.rule.create`    | Um evento é gerado quando um inicializador inclui uma regra em um grupo de acesso. |
| `iam-groups.rule.update`    | Um evento é gerado quando um inicializador modifica o nome da regra. |
| `iam-groups.rule.delete`    | Um evento é gerado quando um inicializador exclui uma regra de um grupo de acesso. |
{: caption="Tabela 1. Gerenciar ações de grupos de acesso" caption-side="top"} 



## Trabalhando com eventos de IDs de serviço
{: #at_events_iam_serviceids}

A tabela a seguir lista as ações que geram um evento:

| Ação | Descrição |
|----------|---------|
| `iam-identity.account-serviceid.create` | Um evento é gerado quando um inicializador cria um ID de serviço.  | 
| `iam-identity.account-serviceid.update` | Um evento é gerado quando um inicializador renomeia um ID de serviço ou modifica sua descrição. | 
| `iam-identity.account-serviceid.delete` | Um evento é gerado quando um inicializador exclui um ID de serviço. | 
{: caption="Tabela 2. Trabalhando com ações de IDs de serviço" caption-side="top"} 


## Trabalhando com eventos de teclas API
{: #at_events_iam_apikeys}

A tabela a seguir lista as ações que geram um evento:

| Ação | Descrição |
|----------|---------|
| `iam-identity.user-apikey.create`      | Um evento é gerado quando um inicializador cria uma chave API. | 
| `iam-identity.user-apikey.update`      | Um evento é gerado quando um inicializador renomeia uma chave API ou modifica sua descrição. |  
| `iam-identity.user-apikey.delete`      | Um evento é gerado quando um inicializador exclui uma chave API. |  
| `iam-identity.serviceid-apikey.create` | Um evento é gerado quando um inicializador cria uma chave API para um ID de serviço. |  
| `iam-identity.serviceid-apikey.delete` | Um evento é gerado quando um inicializador exclui uma chave API para um ID de serviço. |  
{: caption="Tabela 3. Trabalhando com ações de chaves API" caption-side="top"} 


## Criação de log em eventos
{: #at_events_iam_login}

A tabela a seguir lista as ações que geram um evento:

| Ação | Descrição |
|----------|---------|
| `iam-identity.user-apikey.login`         | Um evento é gerado quando um usuário efetua login no {{site.data.keyword.cloud_notm}} usando uma chave API. |  
| `iam-identity.serviceid-apikey.login`    | Um evento é gerado quando um inicializador efetua login no {{site.data.keyword.cloud_notm}} usando uma chave API que está associada a um ID de serviço. |  
| `iam-identity.user-identitycookie.login` | Esse é um evento que é gerado quando um inicializador solicita um novo cookie de identidade para executar uma ação. |
| `iam-identity.user-refreshtoken.login`   | Esse é um evento que é gerado quando o inicializador efetua login no IBM Cloud ou quando um inicializador que já efetuou login no IBM Cloud solicita um novo token de atualização para executar uma ação. |
{: caption="Tabela 4. Ações de login do usuário" caption-side="top"} 


## Gerenciando eventos de políticas
{: #at_events_iam_policies}

A tabela a seguir lista as ações que geram um evento:

| Ação | Descrição |
|----------|---------|
| `iam-am.policy.create` | Um evento é gerado quando um inicializador inclui uma política em um usuário ou grupo de acesso. |
| `iam-am.policy.delete` | Um evento é gerado quando um inicializador modifica permissões para uma política de um usuário ou grupo de acesso.|
| `iam-am.policy.update` | Um evento é gerado quando um inicializador exclui uma política que é designada a um usuário ou grupo de acesso. |
{: caption="Tabela 5. Gerenciando ações de política" caption-side="top"} 


## Visualizando eventos
{: #at_events_iam_ui}

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} estão disponíveis no **domínio de contas** da região **Sul dos EUA**.

Para visualizar esses eventos, deve-se provisionar uma instância do serviço {{site.data.keyword.cloudaccesstrailshort}} na região **Sul dos EUA**. Em seguida, deve-se abrir a UI do {{site.data.keyword.cloudaccesstrailshort}} e mudar para o domínio de contas para ver os eventos. 

Para obter mais informações, consulte [Visualizando eventos de conta](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events).



