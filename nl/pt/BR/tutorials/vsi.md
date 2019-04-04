---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, VSI events, tutorial

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


# Monitorando o {{site.data.keyword.BluVirtServers_short}} e o {{site.data.keyword.baremetal_short}} com o {{site.data.keyword.cloudaccesstrailshort}}
{: #vsi}

Use este tutorial para aprender como configurar usuários em uma conta do {{site.data.keyword.cloud_notm}} para que seja possível monitorar eventos do {{site.data.keyword.cloudaccesstrailshort}} que são gerados por esses usuários quando eles trabalham com o {{site.data.keyword.BluVirtServers_short}} e o {{site.data.keyword.baremetal_short}}.
{:shortdesc}

{{site.data.keyword.BluVirtServers}} são servidores virtuais escaláveis que são comprados com núcleos dedicados e alocações de memória. Eles são uma boa opção caso você esteja procurando por recursos de cálculo, que podem ser incluídos em minutos, com acesso a recursos como modelos de imagem. 
* Para obter mais informações, consulte [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers). 
* Para obter a lista de ações que geram um evento do {{site.data.keyword.cloudaccesstrailshort}}, consulte [Eventos que são gerados pelo {{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-at_events#at_events).

Os {{site.data.keyword.baremetal_short}} são servidores físicos de locatário único que fornecem desempenho e controle com
acesso de baixo nível aos recursos de hardware. 
* Para obter mais informações, consulte [{{site.data.keyword.baremetal_long}}](/docs/bare-metal?topic=bare-metal-about#about).
* Para obter a lista de ações que geram um evento do {{site.data.keyword.cloudaccesstrailshort}}, consulte [Eventos que são gerados pelo {{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-at_events#at_events).

**Para que o usuário gere eventos do {{site.data.keyword.BluVirtServers_short}} e do {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloudaccesstrailshort}}, ele deve ter acesso aos recursos de infraestrutura no IBM Cloud Console.**
{: tip}

## Etapa 1. Vincular a conta do Softlayer a uma conta do {{site.data.keyword.cloud_notm}}
{: #vsi_step1}

** Para gerar eventos do {{site.data.keyword.cloudaccesstrailshort}}, a conta do Softlayer deve ser vinculada a uma conta do {{site.data.keyword.cloud_notm}}. Para obter mais informações, veja [Alternando para IBMid e vinculando contas](/docs/account?topic=account-unifyingaccounts#link_accounts).

Considere as informações a seguir ao vincular a sua conta do Softlayer a uma conta do {{site.data.keyword.cloud_notm}}:
* Todas as novas contas recebem automaticamente um IBMid e as contas existentes do SoftLayer, exceto contas federadas SAML, são ativadas para alternar para a autenticação do IBMid.
* Cada conta do SoftLayer que você planeja vincular a uma conta do {{site.data.keyword.cloud_notm}} deve ser de propriedade de um IBMid exclusivo com um endereço de e-mail exclusivo.
* Para alternar sua conta existente do SoftLayer para um IBMid, crie um IBMid e, em seguida, use seu código de registro para confirmá-lo.
* Após trocar uma conta por uma conta IBMid, é possível vincular a conta do SoftLayer e a conta do {{site.data.keyword.cloud_notm}} para usar os recursos combinados de infraestrutura como serviço (IaaS) e plataforma como serviço (PaaS). 

Conclua as etapas a seguir para vincular uma conta:
1. [Solicite um IBMid e um código de registro](/docs/account?topic=account-unifyingaccounts#reqIBMidandregcode)
2. [Confirme seu IBMid com o código de registro](/docs/account?topic=account-unifyingaccounts#confIBMiduseregcode)
3. [Vincule a sua conta IBMid](/docs/account?topic=account-unifyingaccounts#link_user_account)


## Etapa 2. Conceder permissões de infraestrutura de usuários
{: #vsi_step2}

**Nota:** se você conceder permissões por meio do *Portal de infraestrutura do {{site.data.keyword.cloud_notm}}*, o usuário não terá acesso do painel *Infraestrutura do {{site.data.keyword.cloud_notm}}* para gerenciar dispositivos e os eventos do {{site.data.keyword.cloudaccesstrailshort}} não serão gerados. **Deve-se conceder a um usuário permissão de infraestrutura por meio da conta do {{site.data.keyword.cloud_notm}} para gerenciar dispositivos. Essas ações geram eventos do {{site.data.keyword.cloudaccesstrailshort}}.**
{: tip}

Conclua as etapas a seguir para conceder a um usuário permissão de infraestrutura:

1. [Efetue login no {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/login){:new_window}.
    
	Após você efetuar login com o seu ID do usuário e senha, a UI do {{site.data.keyword.cloud_notm}} será aberta.

2. Na barra de menus, clique em **Gerenciar** &gt; **Conta** e, em seguida, selecione **Usuários**. 

3. Escolha um usuário para quem você deseja conceder permissões para trabalhar com dispositivos.

4. Selecione **Designar acesso**.

5. Selecione **Designar acesso à sua conta do Softlayer**. O Portal de infraestrutura do {{site.data.keyword.cloud_notm}} é aberto dentro do contexto do {{site.data.keyword.cloud_notm}}.

6. Configure as permissões que você deseja conceder ao usuário para gerenciar dispositivos. Selecione **Permissões do portal**. Em seguida, na seção **Dispositivos**, conceda ao usuário as permissões que o usuário precisa para gerenciar dispositivos. Por exemplo, é possível mudar as permissões para `Visualizar detalhes do servidor virtual`, `Reinicializar o servidor e visualizar informações do sistema do IPMI`, `Fazer upgrade do servidor` ou `Emitir recarregamentos do S.O. e iniciar o Kernel de resgate`.

7. Salve as permissões do portal. Ao selecionar **Acesso ao dispositivo**, você é solicitado a salvar as mudanças. Clique em **Salvar**.

8. Configure os dispositivos que o usuário pode gerenciar. Na seção **Acesso ao dispositivo**, selecione os dispositivos físicos. Em seguida, clique em **Atualizar acesso ao dispositivo**.






