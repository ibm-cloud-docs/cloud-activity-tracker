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


# Eventos de instância de serviço  
{: #at_events_rc}

Como um responsável pela segurança, auditor ou gerenciador, é possível usar o serviço {{site.data.keyword.cloudaccesstrailfull}} para controlar como os usuários e aplicativos interagem com os serviços do {{site.data.keyword.Bluemix}}. 
{:shortdesc}

O serviço {{site.data.keyword.cloudaccesstrailfull_notm}} registra atividades iniciadas pelo usuário que mudam o estado de um serviço no {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Sobre o {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov ).

Para começar a monitorar as ações do usuário, veja [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla). 

## Eventos para provisão e gerenciamento de instâncias de serviço
{: #at_events_rc_provision}

A tabela a seguir lista os métodos de API que geram um evento quando eles são chamados:

<table>
  <caption>Ações que geram eventos</caption>
  <tr>
    <th>Ação</th>
	  <th>Descrição</th>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.create</td>
	  <td>Um evento é gerado quando você provisiona uma instância de serviço.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.update</td>
	  <td>Um evento é gerado quando você renomeia uma instância de serviço ou quando você muda o plano de serviço.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.delete</td>
	  <td>Um evento é gerado quando uma instância de serviço é excluída.</td>
  </tr>
</table>


##  Eventos para gerenciar chaves API que estão associadas a uma instância de serviço
{: #at_events_rc_keys}

A tabela a seguir lista os métodos de API que geram um evento quando eles são chamados:

<table>
  <caption>Ações que geram eventos</caption>
  <tr>
    <th>Ação</th>
	  <th>Descrição</th>
  </tr>
  <tr>
    <td><i>service_name</i>.key.create</td>
	  <td>Um evento é gerado quando uma chave API é criada para uma instância de serviço por meio da seção *Credenciais de serviço* da IU da instância de serviço.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.key.delete</td>
	  <td>Um evento é gerado quando uma chave API que está associada a uma instância de serviço é excluída da seção *Credenciais de serviço* da IU da instância de serviço.</td>
  </tr>
</table>

##  Eventos para ligar uma instância de serviço a um app
{: #at_events_rc_bind}

A tabela a seguir lista os métodos de API que geram um evento quando eles são chamados:

<table>
  <caption>Ações que geram eventos</caption>
  <tr>
    <th>Ação</th>
	  <th>Descrição</th>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.create</td>
	  <td>Um evento é gerado quando você liga uma instância de serviço a um aplicativo.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.delete</td>
	  <td>Um evento é gerado quando você desvincula uma instância de serviço de um aplicativo.</td>
  </tr>
</table>




## Onde procurar os eventos
{: #at_events_rc_ui}

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} estão disponíveis no **domínio de contas** da região **Sul dos EUA**.

Para visualizar esses eventos, deve-se provisionar uma instância do serviço {{site.data.keyword.cloudaccesstrailshort}} na região **Sul dos EUA**. Em seguida, deve-se abrir a UI do {{site.data.keyword.cloudaccesstrailshort}} e mudar para o domínio de contas para ver os eventos. Para obter mais informações, consulte [Visualizando eventos de conta](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events).


