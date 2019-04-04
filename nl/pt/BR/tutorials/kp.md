---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, monitoring activity, tutorial

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


# Monitorando a atividade do {{site.data.keyword.keymanagementserviceshort}} com o {{site.data.keyword.cloudaccesstrailshort}}
{: #kp}

Utilize este tutorial para aprender como usar o serviço {{site.data.keyword.cloudaccesstrailfull}} para monitorar a interação de um usuário com o serviço {{site.data.keyword.keymanagementserviceshort}}. 
{:shortdesc}

1. Saiba como provisionar o serviço do {{site.data.keyword.cloudaccesstrailshort}}.
2. Saiba como usar um serviço de Nuvem para gerar eventos de atividade que são coletados automaticamente pelo serviço do {{site.data.keyword.cloudaccesstrailshort}}. Os eventos estão em conformidade com o [padrão do Cloud Auditing Data Federation (CADF) ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo") ](https://www.dmtf.org/sites/default/files/standards/documents/DSP0262_1.0.0.pdf){: new_window}.
3. Saiba como monitorar a atividade de Nuvem de um serviço usando os painéis predefinidos do {{site.data.keyword.cloudaccesstrailshort}}.

A figura a seguir mostra os diferentes componentes e ações que ocorrem quando uma atividade iniciada pelo usuário muda o estado de um serviço:

![Componentes e ações que ocorrem quando uma atividade iniciada pelo usuário muda o estado de um serviço](../images/AT_f1.png "Componentes e ações que ocorrem quando uma atividade iniciada pelo usuário muda o estado de um serviço")



## Antes de Começar
{: #kp_prereqs}

Crie uma [conta do {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/login). Seu ID do usuário deve ser um membro ou um proprietário de uma conta do {{site.data.keyword.cloud_notm}}, com permissões de desenvolvedor no espaço em que você planeja usar o serviço {{site.data.keyword.cloudaccesstrailshort}}.


## Etapa 1. Provisionar o Activity Tracker
{: #kp_step1}

Deve-se provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}} na mesma região em que o serviço do Cloud cuja atividade você deseja monitorar é provisionado. Depois que o serviço {{site.data.keyword.cloudaccesstrailshort}} é provisionado, os eventos são coletados automaticamente de serviços do Cloud selecionados. 

**Nota:** esse tutorial mostra como usar o serviço {{site.data.keyword.cloudaccesstrailshort}} para monitorar a interação de um usuário com o serviço do Cloud {{site.data.keyword.keymanagementservicelong_notm}} na região Sul dos EUA. Portanto, deve-se provisionar o {{site.data.keyword.cloudaccesstrailshort}} na região Sul dos EUA. Para ver informações sobre em qual região um serviço está disponível, veja [Serviços por região](/docs/resources?topic=resources-services_region#services_region).

Conclua as etapas a seguir para provisionar uma instância do serviço {{site.data.keyword.cloudaccesstraillong_notm}} no {{site.data.keyword.cloud_notm}}:

1. [Efetue login no {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/login){:new_window}.
    
	Após você efetuar login com o seu ID do usuário e senha, a UI do {{site.data.keyword.cloud_notm}} será aberta.

2. Clique em **Catálogo**. A lista dos serviços que estão disponíveis no {{site.data.keyword.cloud_notm}} é aberta.

3. Selecione a categoria **Segurança e identidade** para filtrar a lista de serviços que é exibida.

    **Nota:** o serviço também está disponível por meio da categoria **Ferramentas do desenvolvedor**.

4. Clique no tile **Activity Tracker**. 

5. Configure as informações que definem onde o serviço será provisionado. 

    Insira os dados conforme indicado na tabela a seguir: 

    <table>
	  <caption>Tabela 1. Campos que são necessários para provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}</caption>
	  <tr>
	    <th width="50%">Campo</th>
		<th width="50%">Valor</th>
	  </tr>
	  <tr>
	    <td>Selecionar região para implementar em:</td>
		<td>Sul dos EUA</td>
	  </tr>
	  <tr>
	    <td>Escolha uma organização:</td>
		<td>Selecione a organização na qual você planeja provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}.</td>
	  </tr>
	  <tr>
	    <td>Escolha um espaço:</td>
		<td>Selecione o espaço na organização na qual você planeja provisionar o serviço do {{site.data.keyword.cloudaccesstrailshort}}.</td>
	  </tr>
	</table>

6. Clique em **Criar** para provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}} no espaço em que você efetuou login.
   

## Etapa 2.  Configurar o serviço de nuvem  
{: #kp_step2}

Este tutorial mostra como monitorar a atividade de API para o serviço {{site.data.keyword.keymanagementserviceshort}} no {{site.data.keyword.cloud_notm}}.

Conclua as etapas a seguir para configurar o serviço {{site.data.keyword.keymanagementserviceshort}} no {{site.data.keyword.cloud_notm}}:

1. Provisione uma instância do serviço {{site.data.keyword.keymanagementserviceshort}} na região Sul dos EUA. Para obter mais informações, consulte [Provisionando por meio do console do IBM Cloud](/docs/services/key-protect?topic=key-protect-provision#provision).

2. Defina as permissões do {{site.data.keyword.cloud_notm}} para o usuário que você está planejando usar para trabalhar com chaves. 

    Um usuário precisa de uma política do IAM com uma função de serviço configurada como *manager* ou *writer* para que possa criar chaves.

    Um usuário precisa de uma política do IAM com uma função de serviço configurada como *manager* para que possa excluir chaves.

    Um usuário precisa de uma política do IAM com uma função de serviço configurada como *reader* para que possa ver chaves. 


## Etapa 3. Gerar um evento do Activity Tracker
{: #kp_step3}

Nesta etapa, crie uma chave de segurança usando o serviço {{site.data.keyword.keymanagementserviceshort}} para gerar dados do evento do {{site.data.keyword.cloudaccesstrailshort}}. Para obter mais informações, consulte [Criando novas chaves](/docs/services/key-protect?topic=key-protect-create-standard-keys#create-standard-keys).

* Os eventos do {{site.data.keyword.cloudaccesstrailshort}} são gerados como resultado da criação de uma chave.
* Os eventos do {{site.data.keyword.cloudaccesstrailshort}} estão disponíveis no
{{site.data.keyword.cloudaccesstrailshort}} **domínio de contas** disponível na região do
{{site.data.keyword.cloud_notm}} na qual eles são gerados. 

## Etapa 4. Monitorar um evento do Activity Tracker
{: #kp_step4}

Nesta etapa, verifique por meio da UI do {{site.data.keyword.cloud_notm}} se os eventos do {{site.data.keyword.cloudaccesstrailshort}} são gerados.

Conclua as etapas a seguir para verificar se um evento foi criado:

1. Conceda as permissões de usuário para visualizar eventos de conta. Para obter mais informações, consulte [Visualizando eventos de conta](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events) e [Concedendo permissões para ver eventos de conta](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_acc_events).

2. No Painel do {{site.data.keyword.cloud_notm}}, selecione o serviço {{site.data.keyword.cloudaccesstrailshort}}. O painel do serviço é aberto.

3. Configure a visualização para procurar os eventos do {{site.data.keyword.keymanagementserviceshort}} que foram gerados quando você provisionou o serviço e incluiu uma chave.

    * Selecione **Logs de conta** para o campo *Visualizar logs*.
    * Selecione **target.typeURI_str** para o campo *Campo de procura* e insira `kms/secrets` no campo *Filtro*.
	
    Os dados que são exibidos mostram eventos do {{site.data.keyword.keymanagementserviceshort}} que estão disponíveis para as últimas 24 horas. 
	


## Etapas Seguintes
{: #kp_next_steps}

Em seguida, use o painel Kibana predefinido do {{site.data.keyword.cloudaccesstrailshort}} para monitorar e analisar logs de eventos. Para ativar o Kibana, veja [Navegando para o painel Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_kibana). Por padrão, no Kibana, os logs de atividade de espaço são exibidos por meio do painel **ActivityTracker_Space_Dashboard_in_24h**:

Também é possível usar a CLI do {{site.data.keyword.cloudaccesstrailshort}} para gerenciar seus eventos por meio da linha de comandos. Para obter mais informações, veja [Visualizando informações de evento](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status).



