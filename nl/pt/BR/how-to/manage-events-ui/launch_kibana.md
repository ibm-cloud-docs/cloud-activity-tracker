---

copyright:
  years: 2016, 2018
lastupdated: "2018-04-27"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Navegando para o painel do Kibana
{: #launch_kibana}

É possível ativar o Kibana por meio da IU do {{site.data.keyword.cloudaccesstrailshort}} no {{site.data.keyword.Bluemix}} ou diretamente de um navegador da web.
{:shortdesc}
   

##  Navegando para o Kibana do painel do serviço Activity Tracker
{: #launch_Kibana_from_at}

Os logs de atividades que o Kibana exibe incluem eventos para todos os recursos que são implementados no espaço da organização do {{site.data.keyword.Bluemix_notm}} em que você efetuou login e onde o serviço {{site.data.keyword.cloudaccesstrailshort}} é provisionado.

Conclua as etapas a seguir para ativar o Kibana por meio do painel do serviço {{site.data.keyword.cloudaccesstrailshort}}:

1. Efetue login em sua conta do {{site.data.keyword.Bluemix_notm}}.

    O painel do {{site.data.keyword.Bluemix_notm}} pode ser localizado em: [http://bluemix.net ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://bluemix.net){:new_window}.
    
	Depois de efetuar login com seu ID de usuário e senha, a UI do {{site.data.keyword.Bluemix_notm}} é aberta.

2. Selecione o serviço {{site.data.keyword.cloudaccesstrailshort}} no painel do {{site.data.keyword.Bluemix_notm}}. 
    
3. Selecione a guia **Gerenciado**.

4. Clique em **Visualização avançada**. 

    O painel Kibana é aberto.

Por padrão, o painel **ActivityTracker_Space_Dashboard_in_24h** é carregado e um filtro de tempo configurado para as últimos 24 horas. 


	
	
##  Navegando para o Kibana por meio de um navegador da web
{: #launch_Kibana_from_browser}

As informações de log que o Kibana exibe incluem eventos para todos os recursos que são implementados no espaço da organização do {{site.data.keyword.Bluemix_notm}} em que você efetuou login.

Conclua as etapas a seguir para ativar o Kibana em um navegador:

1. Abra um navegador da web e ative o Kibana. Em seguida, efetue login na interface com o usuário do Kibana.
    
    Por exemplo, a tabela a seguir lista a URL que se deve usar para ativar o Kibana por região:
      
    <table>
          <caption>Tabela 1. URLs para ativar o Kibana por região</caption>
           <tr>
            <th>Região</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>Alemanha</td>
            <td>[https://logging.eu-fra.bluemix.net](https://logging.eu-fra.bluemix.net) </td>
          </tr>
          <tr>
            <td>Sydney</td>
            <td>[https://logging.au-syd.bluemix.net](https://logging.au-syd.bluemix.net) </td>
          </tr>
		  <tr>
            <td>Reino Unido</td>
            <td>[https://logging.eu-gb.bluemix.net](https://logging.eu-gb.bluemix.net)</td>
          </tr>
		  <tr>
            <td>Sul dos EUA</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
    </table>
	
	A página Descobrir no Kibana é aberto.
	
2. Verifique se você efetuou login na conta, organização e espaço do {{site.data.keyword.Bluemix_notm}} nos quais deseja visualizar e analisar os logs de atividades.

    É possível ver eventos e logs que estão disponíveis no espaço no qual você efetuou login.

3. Para filtrar eventos, selecione **Abrir** na barra de menus.

    A lista de painéis salvos é exibida.
	
4. Para visualizar os eventos para o espaço em que você efetuou login, selecione **ActivityTracker_Space_Dashboard_in_24h**.


## Limitações
{: #limitations}

 Devido a limitações no Kibana, não é possível ter múltiplas guias do navegador do Kibana abertas de uma vez na mesma sessão para visualizar diferentes espaços ou contas. Portanto, se tiver duas ou mais sessões abertas de uma vez e mudar o domínio do espaço para conta ou vice-versa, você poderá ter problemas.
	



