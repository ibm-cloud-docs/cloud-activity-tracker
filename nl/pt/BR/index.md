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


# Introdução
{: #getting-started-with-cla}

O serviço {{site.data.keyword.cloudaccesstrailfull}} registra as atividades iniciadas pelo usuário que mudam
o estado de um serviço no {{site.data.keyword.Bluemix}}. Saiba como usar o serviço {{site.data.keyword.cloudaccesstrailfull}} para monitorar a interação de um usuário com um serviço do Cloud.
{:shortdesc}

A figura a seguir mostra os diferentes componentes e ações que ocorrem quando uma atividade iniciada pelo usuário muda o estado de um serviço:

![Componentes e ações que ocorrem quando uma atividade iniciada pelo usuário muda o estado de um serviço](images/AT_f1.png "Componentes e ações que ocorrem quando uma atividade iniciada pelo usuário muda o estado de um serviço")

**Nota:** essa introdução mostrará como iniciar o monitoramento de atividade do Cloud no Sul dos EUA.

## Antes de Começar
{: #index_prereqs}

* Leia sobre o serviço {{site.data.keyword.cloudaccesstrailshort}}. Para obter mais informações, consulte  [ Sobre o  {{site.data.keyword.cloudaccesstrailshort}} ](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov).
* Verifique as regiões em que o serviço está disponível. Para obter informações adicionais, consulte
[Regiões](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov_regions).
* Obtenha uma identificação de usuário que seja membro ou proprietário de uma conta do {{site.data.keyword.cloud_notm}}. 

    Para obter uma identificação de usuário do {{site.data.keyword.cloud_notm}}, acesse: [Registro ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/registration/){:new_window}.



## Etapa 1: Fornecimento do {{site.data.keyword.cloudaccesstrailshort}}
{: #index_step1}

Considere as seguintes informações para escolher onde fornecer uma instância do serviço {{site.data.keyword.cloudaccesstrailshort}}:

* O {{site.data.keyword.cloudaccesstrailshort}} coleta eventos em domínios. Há um domínio de contas por região e um domínio de espaço por espaço do Cloud Foundry (CF). 

* **Para monitorar ações de conta globais**,deve-se fornecer uma instância do serviço {{site.data.keyword.cloudaccesstrailshort}} em um espaço na região Sul dos EUA. Estes são alguns exemplos de ações globais: fornecer uma instância, mudar a política de IAM do usuário ou convidar um usuário para a conta.

* **Para monitorar eventos gerados por um serviço que é fornecido no contexto de uma organização e um espaço do CF**, deve-se fornecer uma instância do serviço {{site.data.keyword.cloudaccesstrailshort}} na mesma região e espaço em que o serviço cuja atividade você deseja monitorar é fornecido. 

* **Para monitorar eventos gerados por um serviço que é fornecido no contexto de um grupo de recursos**, deve-se fornecer uma instância do serviço {{site.data.keyword.cloudaccesstrailshort}} em um espaço na mesma região em que o serviço cuja atividade você deseja monitorar é fornecido. 

* Para fornecer uma instância, a sua identificação de usuário deve ter **função de desenvolvedor** no espaço em que você planeja fornecer o serviço {{site.data.keyword.cloudaccesstrailshort}}.

Conclua as etapas a seguir para provisionar uma instância do serviço {{site.data.keyword.cloudaccesstraillong_notm}} no {{site.data.keyword.cloud_notm}}:

1. Efetue login no {{site.data.keyword.cloud_notm}}.

    O painel do {{site.data.keyword.cloud_notm}} pode ser localizado em: [https://cloud.ibm.com ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com){:new_window}.
    
	Após você efetuar login com o seu ID do usuário e senha, a UI do {{site.data.keyword.cloud_notm}} será aberta.

2. Clique em **Catálogo**. A lista dos serviços que estão disponíveis no {{site.data.keyword.cloud_notm}} é aberta.

3. Selecione a categoria **Segurança e identidade** para filtrar a lista de serviços que é exibida.

    **Nota:** o serviço também é disponibilizado por meio da categoria **Ferramentas do desenvolvedor**.

4. Clique no tile **Activity Tracker**. 

5. Configure as informações que definem onde o serviço será provisionado.

    Por exemplo, para fornecer o serviço na região Sul dos EUA, insira os dados conforme indicado na tabela a seguir: 

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
		<td>Selecione o espaço na organização que você selecionou no qual planeja provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}.</td>
	  </tr>
	</table>

6. Selecione um plano. 

    Por padrão, o plano **Lite** é selecionado.

	Para obter mais informações, veja [Planos de serviço](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov_plan).

7. Clique em **Criar** para fornecer uma instância do serviço {{site.data.keyword.cloudaccesstrailshort}} no espaço em que você efetuou login.
   


## Etapa 2: Conceder acesso aos usuários para monitorar eventos
{: #index_step2}

Para visualizar eventos, deve-se ter permissões de acesso no {{site.data.keyword.cloud_notm}}. As permissões variam dependendo de se você deseja visualizar eventos de conta globais, eventos para um serviço que é fornecido no contexto de um grupo de recursos ou eventos para um serviço fornecido no contexto de uma organização e um espaço do CF. 

**Para monitorar ações de conta globais** e **monitorar um serviço que é fornecido no contexto de um grupo de recursos**, considere as informações a seguir:

* Deve-se ter uma política de IAM para o serviço {{site.data.keyword.loganalysisshort}} com a função de **leitor** no serviço {{site.data.keyword.loganalysisshort}}. 
* O proprietário da conta ou um administrador do serviço {{site.data.keyword.loganalysisshort}} pode conceder essa política.

**Para monitorar um serviço que é fornecido no contexto de uma organização e um espaço do CF**, considere as informações a seguir:

* Deve-se ter a função de **desenvolvedor** para o espaço no qual você forneceu uma instância do serviço do {{site.data.keyword.cloudaccesstrailshort}}.
* O proprietário da conta, o gerenciador de organização ou o gerenciador de espaço pode conceder a você a função de **desenvolvedor** para o espaço.

**Nota: para conceder a um usuário uma política de IAM, deve-se ser o proprietário da conta ou um administrador do serviço {{site.data.keyword.loganalysisshort}}. **

### Conceda acesso aos usuários para monitorar eventos de domínio de contas
{: #index_acc}

Conclua as etapas a seguir para conceder a um usuário uma política de IAM por meio da IU do {{site.data.keyword.cloud_notm}}:

1. Efetue login no console do {{site.data.keyword.cloud_notm}}.

    Abra um navegador da web e ative o painel do {{site.data.keyword.cloud_notm}}: [https://cloud.ibm.com ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com){:new_window}

2. Na barra de menus, clique em **Gerenciar** &gt; **Segurança** &gt; **Identidade e acesso** e, em seguida, selecione **Usuários**.
3. Na linha para o usuário que você deseja designar acesso, selecione o menu **Ações** e, em seguida, clique em **Designar acesso**.
4. Selecione **Designar acesso a recursos**.
5. Selecione **Análise do log**.
6. Selecione **Todas as regiões**.
7. Selecione **Todas as instâncias de serviço**.
8. Selecione a função de serviço **Leitor**.
9. Clique em Designar.

### Conceda acesso aos usuários para monitorar eventos de domínio de espaço
{: #index_space}

Para conceder a um usuário uma função de desenvolvedor em um espaço por meio da IU do {{site.data.keyword.cloud_notm}}, conclua as etapas a seguir:

1. Efetue login no console do {{site.data.keyword.cloud_notm}}.

    Abra um navegador da web e ative o painel do {{site.data.keyword.cloud_notm}}: [https://cloud.ibm.com ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com){:new_window}
	
	Após você efetuar login com o seu ID do usuário e senha, a UI do {{site.data.keyword.cloud_notm}} será aberta.

2. Na barra de menus, clique em **Gerenciar** &gt; **Segurança** &gt; **Identidade e acesso** e, em seguida, selecione **Usuários**.

3. Selecione o usuário.

4. Selecione **Acesso ao Cloud Foundry**.

5. Expanda uma organização.

    A lista de espaços disponíveis na organização é exibida.

6. No menu Ação, selecione **Editar função de organização**. Selecione a função de **Auditor** para o campo *Funções de organização*. Em seguida, clique em **Salvar função**.

7. Selecione um espaço. 

8. No menu Ação, selecione **Editar função de espaço**. Selecione a função de **Desenvolvedor** para o campo *Funções de espaço*. Em seguida, clique em **Salvar função**.
	
7. Clique em **Designar**.



## Etapa 3: Gerar eventos do {{site.data.keyword.cloudaccesstrailshort}}
{: #index_step3}

Depois que o serviço {{site.data.keyword.cloudaccesstrailshort}} é provisionado, os eventos são coletados automaticamente de serviços do Cloud selecionados. Para saber mais sobre os serviços que você pode monitorar com o {{site.data.keyword.cloudaccesstrailshort}}, incluindo informações sobre as ações que geram um evento do {{site.data.keyword.cloudaccesstrailshort}}, consulte [Serviços de nuvem](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services).

**Nota:** para que um usuário gere eventos do {{site.data.keyword.BluVirtServers_short}} e do {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}}, ele deve ter acesso aos recursos de infraestrutura no IBM Cloud Console. Para obter mais informações, consulte [Monitorando a atividade do {{site.data.keyword.BluVirtServers_short}} e do {{site.data.keyword.baremetal_short}} com o {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/tutorials/vsi.html#vsi).

Para saber como gerar eventos, conclua o tutorial [Monitorando a atividade do {{site.data.keyword.keymanagementserviceshort}} com o {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/tutorials/kp.html#kp).

## Etapa 4: Visualizando eventos
{: #index_step4}

É possível monitorar eventos do {{site.data.keyword.cloudaccesstrailshort}} na IU do {{site.data.keyword.cloud_notm}}. Também é possível fazer upgrade de seu plano para o plano Premium para monitorar eventos por meio do Kibana. 

**Para monitorar ações de conta globais** e **monitorar um serviço que é fornecido no contexto de um grupo de recursos**, considere as informações a seguir:

* Os eventos são coletados em um domínio de contas.

    Há um domínio de contas por região.

    As ações de conta globais são coletadas no domínio de contas do Sul dos EUA.

    Os eventos para um serviço são coletados no domínio de contas da região em que uma instância desse serviço é fornecida.

* O proprietário da conta pode visualizar eventos por meio da IU do {{site.data.keyword.cloud_notm}} ou no Kibana.
* Outros usuários podem somente visualizar eventos de domínio de contas por meio do Kibana. 


**Para monitorar um serviço que é fornecido no contexto de uma organização e um espaço do CF**, considere as informações a seguir:

* Os eventos são coletados em um domínio de espaço. 
* Cada espaço do CF possui um domínio de espaço do {{site.data.keyword.cloudaccesstrailshort}} associado. 
* É possível visualizar eventos por meio da IU do {{site.data.keyword.cloud_notm}} ou no Kibana.

A tabela a seguir define o domínio do {{site.data.keyword.cloudaccesstrailshort}} no qual os eventos devem ser monitorados:

| Monitoramento                                                           | Domínio do {{site.data.keyword.cloudaccesstrailshort}} |  
|----------------------------------------------------------------------|----------------------------------------------------| 
| `Ações de conta globais`                                             | domínio de contas do Sul dos EUA                            |  
| `Serviços que são fornecidos no contexto de um grupo de recursos`   | domínio de contas                                     | 
| `Serviços que são fornecidos no contexto de uma organização e um espaço do CF` | domínio de espaço                                       | 
{: caption="Tabela 1. Domínios do {{site.data.keyword.cloudaccesstrailshort}} por origem de eventos" caption-side="top"} 

Para visualizar eventos, é possível escolher uma das opções a seguir:

* [Navegando para o painel Activity Tracker para monitorar a atividade de nuvem na conta](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html#launch_at_ui_account_view_account) 
* [Navegando para o painel Activity Tracker para monitorar a atividade de nuvem em um espaço](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html#launch_at_ui_account_view_space) 
* [Navegando para o Kibana por meio de um navegador da web](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana).

Para visualizar eventos que você gera concluindo as etapas no tutorial, escolha [Navegando para o painel do Activity Tracker para monitorar a atividade de nuvem na conta](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html#launch_at_ui_account_view_account). Se você não for o proprietário da conta, faça upgrade do plano de serviço e verifique se você tem as permissões de acesso corretas para visualizar eventos. 


## Etapas Seguintes
{: #index_next_steps}

Use a CLI do {{site.data.keyword.cloudaccesstrailshort}} para gerenciar seus eventos por meio da linha de comandos. Para obter mais informações, consulte [Gerenciando eventos usando a CLI do Activity Tracker](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#tutorial2).



