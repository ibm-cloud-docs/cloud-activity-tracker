---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Eventos de gerenciamento de conta  
{: #at_events_acc_mgt}

Como um responsável pela segurança, auditor ou gerenciador, é possível usar o serviço {{site.data.keyword.cloudaccesstrailfull}} para controlar como os usuários e aplicativos interagem com a conta do {{site.data.keyword.Bluemix}}. 
{:shortdesc}

O serviço {{site.data.keyword.cloudaccesstrailfull_notm}} registra atividades iniciadas pelo usuário que mudam o estado de um serviço no {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Sobre o {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov ).

Para começar a monitorar as ações do usuário, veja [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla). 



## Eventos para gerenciar contas
{: #at_events_acc_mgt_account}

A tabela a seguir lista o método de API que gera um evento quando eles são chamados:

<table>
  <caption>Ações que geram eventos</caption>
  <tr>
    <th>Ação</th>
	  <th>Descrição</th>
  </tr>
  <tr>
    <td>billing.account.create</td>
	  <td>Um evento é gerado quando você provisiona uma conta, depois que o ID da conta é designado para a conta.</td>
  </tr>
  <tr>
    <td>billing.account.update</td>
	  <td>Um evento é gerado quando você atualiza informações sobre a conta.</td>
  </tr>
  <tr>
    <td>billing.account.active</td>
	  <td>Um evento é gerado quando você verifica a conta, ou seja, um evento é gerado quando a conta se torna ativa.</td>
  </tr>
  <tr>
    <td>billing.account.subscription.create</td>
	  <td>Um evento é gerado quando você cria uma <a href="/docs/account/index.html#subscription-account">Conta da assinatura</a>.</td>
  </tr>
</table>



## Eventos para gerenciar usuários
{: #at_events_acc_mgt_users}

A tabela a seguir lista o método de API que gera um evento quando eles são chamados:

<table>
  <caption>Ações que geram eventos</caption>
  <tr>
    <th>Ação</th>
	  <th>Descrição</th>
  </tr>
  <tr>
    <td>user-management.user.create</td>
	  <td>Um evento é gerado quando você envia um convite para um usuário participar de uma conta. </br>O proprietário da conta é o único usuário na conta que pode executar essa ação.</td>
  </tr>
  <tr>
    <td>user-management.user.active</td>
	  <td>Um evento é gerado quando você ativa o usuário na conta. </br>Quando o usuário verifica seu endereço de e-mail, o evento é gerado.</td>
  </tr>
  <tr>
    <td>user-management.account.user.delete</td>
	  <td>Um evento é gerado quando você remove um usuário da conta. </br>O proprietário da conta é o único usuário na conta que pode executar essa ação.</td>
  </tr>
</table>

## Eventos para gerenciar organizações
{: #at_events_acc_mgt_org}

A tabela a seguir lista o método de API que gera um evento quando eles são chamados:

<table>
  <caption>Ação que gera eventos</caption>
  <tr>
    <th>Ação</th>
	  <th>Descrição</th>
  </tr>
  <tr>
    <td>billing.account.org.create</td>
	  <td>Um evento é gerado quando você inclui uma organização na conta.</td>
  </tr>
</table>

## Onde procurar os eventos
{: #at_events_acc_mgt_ui}

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} estão disponíveis no **domínio de contas** da região **Sul dos EUA**. Para obter mais informações, consulte [Visualizando eventos de conta](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events).

Para visualizar esses eventos, deve-se provisionar uma instância do serviço {{site.data.keyword.cloudaccesstrailshort}} na região **Sul dos EUA**. Em seguida, deve-se abrir a UI do {{site.data.keyword.cloudaccesstrailshort}} e mudar para o domínio de contas para ver os eventos. Para obter mais informações, consulte [Visualizando eventos de conta](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events). 








