---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, launch Kibana

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
{:deprecated: .deprecated}


# Abrindo o painel do Kibana
{: #launch_kibana}

É possível ativar o Kibana por meio da IU do {{site.data.keyword.cloudaccesstrailshort}} no {{site.data.keyword.cloud_notm}} ou diretamente de um navegador da web.
{:shortdesc}
   
O {{site.data.keyword.cloudaccesstrailfull}} foi descontinuado. A partir de 9 de maio de 2019, não é possível fornecer novas instâncias do {{site.data.keyword.cloudaccesstrailshort}}. As instâncias existentes do plano premium são suportadas até 30 de setembro de 2019. Para continuar o monitoramento da atividade de sua conta do {{site.data.keyword.cloud_notm}}, provisione uma instância do [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


##  Abrindo o Kibana por meio do painel do serviço do Activity Tracker
{: #launch_Kibana_from_at}

Os logs de atividades que o Kibana exibe incluem eventos para todos os recursos que são implementados no espaço da organização do {{site.data.keyword.cloud_notm}} em que você efetuou login e onde o serviço {{site.data.keyword.cloudaccesstrailshort}} é provisionado.

Conclua as etapas a seguir para ativar o Kibana por meio do painel do serviço {{site.data.keyword.cloudaccesstrailshort}}:

1. Efetue login em sua conta do {{site.data.keyword.cloud_notm}}.

    O painel do {{site.data.keyword.cloud_notm}} pode ser localizado em: [https://cloud.ibm.com/login ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/login){:new_window}.
    
	Após você efetuar login com o seu ID do usuário e senha, a UI do {{site.data.keyword.cloud_notm}} será aberta.

2. Selecione o serviço {{site.data.keyword.cloudaccesstrailshort}} no painel do {{site.data.keyword.cloud_notm}}. 
    
3. Selecione a guia **Gerenciado**.

4. Para visualizar eventos de espaço, selecione **Logs de espaço** para o campo *Visualizar logs*. **Nota:** essa é a visualização padrão. Em seguida, clique em **Visualizar no Kibana**. 

    O painel Kibana é aberto. O painel **ActivityTracker_Space_Dashboard_in_24h** é carregado com um filtro de tempo configurado para as últimas 24 horas.

5. Para visualizar eventos de conta, selecione **Logs de conta** para o campo *Visualizar logs*. Em seguida, clique em **Visualizar no Kibana**. 

    O painel **ActivityTracker_Account_Dashboard_in_24h** é carregado com um filtro de tempo configurado para as últimas 24 horas.
	
	
##  Abrindo o Kibana por meio de um navegador da web
{: #launch_Kibana_from_browser}

Conclua as etapas a seguir para ativar o Kibana em um navegador:

1. Abra um navegador da web e ative o Kibana na região em que você deseja monitorar eventos. Em seguida, efetue login na interface com o usuário do Kibana.
    
    Por exemplo, a tabela a seguir lista a URL que se deve usar para ativar o Kibana por região:
      
    <table>
          <caption>Tabela 1. URLs para ativar o Kibana por região</caption>
           <tr>
            <th>Região</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>Alemanha</td>
            <td>`https://logging.eu-fra.bluemix.net`</td>
          </tr>
          <tr>
            <td>Sydney</td>
            <td>`https://logging.au-syd.bluemix.net` </td>
          </tr>
		  <tr>
            <td>Reino Unido</td>
            <td>`https://logging.eu-gb.bluemix.net`</td>
          </tr>
		  <tr>
            <td>Sul dos EUA</td>
            <td>`https://logging.ng.bluemix.net`</td>
          </tr>
    </table>
	
	A página Descobrir no Kibana é aberto.
	
2. Verifique se você está com login efetuado na conta do {{site.data.keyword.cloud_notm}} em que deseja visualizar e analisar os eventos de atividade.

3. Visualizar eventos de espaço ou de conta

* Clique no canto superior direito da janela do Kibana no qual as informações de login são exibidas.
* Em **Domínio** selecione espaço ou conta no menu suspenso
* Para eventos de espaço, selecione o **espaço** de interesse no menu suspenso Espaço
* Para eventos de conta, selecione a **conta** correta no menu suspenso Conta

4. Ajuste o horário de procura

* O horário de procura padrão do Kibana é configurado para os últimos 15 minutos.
* Clique em `Last 15 minutes` na barra cinza superior direita
* Selecione o período para o qual você deseja ver os eventos. Os últimos eventos de 3 dias são pesquisáveis. Selecione um prazo de 3 dias ou menos.

5. Filtre para mostrar apenas eventos do Activity Tracker
* Você pode encontrar os eventos de Logs e do Activity Tracker ao visualizar diretamente no Kibana.
* Na barra de procura insira, `type:ActivityTracker` para mostrar apenas eventos do Activity Tracker.

Os eventos que você vê no Kibana correspondem aos eventos que são hospedados no domínio selecionado na região em que você ativou o Kibana.

## Limitações
{: #launch_kibana_limitations}

* Devido a limitações no Kibana, não é possível ter múltiplas guias do navegador do Kibana abertas de uma vez na mesma sessão para visualizar diferentes espaços ou contas. Portanto, se tiver duas ou mais sessões abertas de uma vez e mudar o domínio do espaço para conta ou vice-versa, você poderá ter problemas.
* Por padrão, somente o proprietário da conta pode visualizar eventos de conta. Para permitir que outros visualizem os eventos de conta, siga as instruções em [Visualizando eventos de conta](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-view_acc_events#view_acc_events).



