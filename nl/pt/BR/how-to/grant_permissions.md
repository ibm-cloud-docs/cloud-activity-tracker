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


# Concedendo permissões para visualizar eventos
{: #grant_permissions}

No {{site.data.keyword.Bluemix}}, é possível designar funções do Cloud Foundry, funções do IAM ou ambas para um usuário. Essas funções definem as tarefas que um usuário pode executar ao trabalhar com o serviço {{site.data.keyword.cloudaccesstrailshort}}.  
{:shortdesc}

## Concedendo permissões para ver os eventos de conta
{: #grant_acc_events}

Conceda a um usuário as permissões a seguir para ver eventos de conta em uma região:

1. Função de *Desenvolvedor* em um espaço da região em que o {{site.data.keyword.cloudaccesstrailshort}} é provisionado. 

    Para obter mais informações, consulte [Concedendo uma função do CF](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role).

2. Política do IAM para o serviço {{site.data.keyword.loganalysisshort}} com a função de *visualizador* na região. 

    A função de visualizador é a função mínima do IAM necessária. 
	
	Para obter mais informações, consulte [Concedendo permissões do IAM](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy).


## Concedendo permissões para ver eventos de espaço
{: #grant_space_events}

Conceda a um usuário a permissão a seguir para ver eventos de espaço em uma região:

* Função de *Desenvolvedor* no espaço da região em que o {{site.data.keyword.cloudaccesstrailshort}} é provisionado. 

    Para obter mais informações, consulte [Concedendo uma função do CF](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role).


## Concedendo permissões do IAM
{: #grant_iam_policy}

Para conceder a um usuário uma função do IAM, considere as informações a seguir:

* Deve-se ter permissões para designar políticas a outros usuários na conta ou deve-se ser o proprietário da conta. Se você não for o proprietário da conta, deverá ter uma política do IAM com a função de **administrador** para o serviço {{site.data.keyword.loganalysisshort}}.

* Ao definir uma política, as regiões especificadas definem as regiões em que um usuário tem acesso concedido para visualizar eventos de domínio de contas.

Conclua as etapas a seguir para conceder a um usuário permissões para visualizar eventos de um domínio de contas:

1. Efetue login no console do {{site.data.keyword.cloud_notm}}.

    Abra um navegador da web e ative o painel do {{site.data.keyword.cloud_notm}}: [http://bluemix.net ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](http://bluemix.net){:new_window}
	
	Após você efetuar login com o seu ID do usuário e senha, a UI do {{site.data.keyword.cloud_notm}} será aberta.

2. Na barra de menus, clique em **Gerenciar > Conta > Usuários**. 

    A janela *Usuários* exibe uma lista de usuários com seus endereços de e-mail para a conta selecionada atualmente.
	
3. Se o usuário é um membro da conta, selecione o nome do usuário na lista ou clique em **Gerenciar usuário** no menu *Ações*.

    Se o usuário não é um membro da conta, veja [Convidando usuários](/docs/iam/iamuserinv.html#iamuserinv).

4. Na seção **Políticas de acesso**, clique em **Designar acesso** e, em seguida, selecione **Designar acesso aos recursos**.

    A janela *Designar acesso a recursos ao usuário** é aberta.

5. Insira informações sobre a política. A tabela a seguir lista os campos que são necessários para definir uma política: 

    <table>
	  <caption>Lista de campos para configurar uma política do IAM.</caption>
	  <tr>
	    <th>Campo</th>
		<th>Valor</th>
	  </tr>
	  <tr>
	    <td>Serviços</td>
		<td>*IBM Cloud Log Analysis*</td>
	  </tr>	  
	  <tr>
	    <td>Regiões</td>
		<td>É possível especificar as regiões nas quais o usuário terá acesso concedido para trabalhar com eventos. Selecione uma ou mais regiões individualmente ou selecione **Todas as regiões atuais** para conceder acesso a todas as regiões.</td>
	  </tr>
	  <tr>
	    <td>Instância de serviço</td>
		<td>Selecione *Todas as instâncias de serviço*.</td>
	  </tr>
	  <tr>
	    <td>Funções</td>
		<td>Selecione uma ou mais funções do IAM. <br>As funções válidas são: *administrador*, *operador*, *editor* e *visualizador*.</td>
	  </tr>
     </table>
	
6. Clique em **Designar**.
	
A política que você configura é aplicável às regiões selecionadas. 


## Concedendo uma função de CF
{: #grant_cf_role}

Para conceder a um usuário uma função do CF, considere as informações a seguir:

* Deve-se ter permissões na organização e no espaço para designar ao usuário uma função do Cloud Foundry. 

* Apenas a função de **desenvolvedor** permite que um usuário visualize eventos.

Conclua as etapas a seguir para conceder a um usuário acesso para visualizar eventos de espaço:

1. Efetue login no console do {{site.data.keyword.cloud_notm}}.

    Abra um navegador da web e ative o painel do {{site.data.keyword.cloud_notm}}: [http://bluemix.net ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](http://bluemix.net){:new_window}
	
	Após você efetuar login com o seu ID do usuário e senha, a UI do {{site.data.keyword.cloud_notm}} será aberta.

2. Na barra de menus, clique em **Gerenciar > Conta > Usuários**. 

    A janela *Usuários* exibe uma lista de usuários com seus endereços de e-mail para a conta selecionada atualmente.
	
3. Se o usuário é um membro da conta, selecione o nome do usuário na lista ou clique em **Gerenciar usuário** no menu *Ações*.

    Se o usuário não é um membro da conta, veja [Convidando usuários](/docs/iam/iamuserinv.html#iamuserinv).

4. Selecione **Acesso ao Cloud Foundry**, em seguida, selecione a organização.

    A lista de espaços disponíveis na organização é exibida.

5. Escolha um espaço. Em seguida, na ação de menu, selecione **Editar função de espaço**.

6. Selecione **Desenvolvedor**.
	
7. Clique em **Salvar função**.




