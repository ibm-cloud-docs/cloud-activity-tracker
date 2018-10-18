---

copyright:
  years: 2016, 2018
lastupdated: "2018-06-21"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Activity Tracker
{: #activity_tracker_ov}

Use o serviço {{site.data.keyword.cloudaccesstrailfull}} para controlar como os aplicativos interagem com os serviços do {{site.data.keyword.Bluemix}}. Use o {{site.data.keyword.cloudaccesstrailshort}} para monitorar atividade anormal e obedeça aos requisitos de auditoria regulamentares. Os eventos que são coletados obedecem ao padrão Cloud Auditing Data Federation (CADF).
{:shortdesc}

* O {{site.data.keyword.cloudaccesstrailshort}} oferece controle de
segurança de alto nível para seus recursos de TI na nuvem.
* O {{site.data.keyword.cloudaccesstrailshort}} fornece uma solução para os administradores de rede para capturar, armazenar, visualizar, procurar e monitorar a atividade de API em um único local.
* O {{site.data.keyword.cloudaccesstrailshort}} fornece recursos para fazer download de eventos que podem ser usados para gerar um relatório de trilha de auditoria. É possível requerer
esses relatórios para que sua organização obedeça às regulamentações internas e às regulamentações externas da
indústria e do país.

Conformidade com políticas internas e regulamentações da indústria é um requisito importante na estratégia
de qualquer organização, independentemente de onde os aplicativos são executados: no local, em uma nuvem híbrida ou em
uma nuvem pública. O serviço {{site.data.keyword.cloudaccesstrailshort}} fornece a estrutura e a funcionalidade para monitorar chamadas API e produzir a evidência para obedecer às políticas corporativas e regulamentações específicas do segmento de mercado.

Ao trabalhar em um ambiente de nuvem, como o {{site.data.keyword.Bluemix_notm}}, deve-se planejar a estratégia de nuvem para auditoria e monitoramento de cargas de trabalho e dados de acordo com suas políticas internas e com os requisitos de conformidade baseados no segmento de mercado e no país. É possível usar as informações que são registradas por meio do serviço {{site.data.keyword.cloudaccesstrailshort}} para
identificar incidentes de segurança, detectar acesso não autorizado e obedecer aos requisitos de auditoria
regulamentares e internos.

Por exemplo, é possível usar os logs de atividades do {{site.data.keyword.cloudaccesstrailshort}} para identificar as informações a seguir:

* Os usuários que fizeram chamadas API para serviços de nuvem.
* O endereço IP de origem a partir do qual as chamadas API foram feitas.
* O registro de data e hora de quando as chamadas API foram feitas.
* O status da chamada API.


## Coletando Eventos
{: #collect}

O serviço {{site.data.keyword.cloudaccesstrailshort}} captura apenas os dados de atividade que estão relacionados a chamadas API e outras ações que são feitas para serviços de nuvem selecionados no {{site.data.keyword.Bluemix_notm}}. 

* Os eventos são coletados automaticamente. 
* Eventos que são coletados no {{site.data.keyword.cloudaccesstrailshort}} estão em conformidade com o padrão do Cloud Auditing Data Federation (CADF). O padrão CADF define um modelo de evento completo que inclui as informações necessárias para
certificar, gerenciar e auditar a segurança de aplicativos em ambientes de nuvem.
* {{site.data.keyword.cloudaccesstrailshort}} armazena e agrupa eventos por domínio. Há um domínio de conta por região e um domínio de espaço por espaço do Cloud Foundry. 

O modelo de evento CADF inclui os componentes a seguir:

<table>
  <caption>Tabela 1. Componentes que estão disponíveis em um modelo de evento CADF</caption>
  <tr>
    <th>Componente</th>
	<th>Descrição</th>
  </tr>
  <tr>
    <td>Ação</td>
	<td>A ação é a operação ou a atividade que um inicializador executa, tenta executar ou está aguardando para concluir.</td>
  </tr>
  <tr>
    <td>Inicializador</td>
	<td>O inicializador é o recurso que faz uma chamada API e gera um evento CADF. O evento que é acionado depende da ação solicitada pela chamada
API.</td>
  </tr>
  <tr>
    <td>Observador</td>
	<td>O observador é o recurso que cria e armazena um registro CADF das informações disponíveis em um evento CADF.</td>
  </tr>
  <tr>
    <td>Resultado</td>
	<td>O resultado é o status da ação com relação ao destino.</td>
  </tr>
  <tr>
    <td>Destino</td>
	<td>O destino é o recurso com relação ao qual a ação é executada, a execução é tentada ou cuja conclusão está pendente.</td>
  </tr>
</table>


Considere as informações a seguir quando você trabalhar com o log do {{site.data.keyword.cloudaccesstrailshort}} na nuvem pública {{site.data.keyword.IBM_notm}}:

* É possível armazenar registros de auditoria somente para chamadas API feitas para recursos que são executados na nuvem pública {{site.data.keyword.IBM_notm}}.
* Somente o armazenamento em nuvem pública {{site.data.keyword.IBM_notm}} é usado para coletar eventos.
* As informações são armazenadas por 3 dias. Depois disso, as
informações são excluídas com base no esquema primeiro a entrar,
primeiro a sair.
* Os eventos CADF do tipo *Atividade* são suportados pelo serviço {{site.data.keyword.cloudaccesstrailshort}}.


## Rastreador de Atividade de Provisionamento
{: #provision}

Para visualizar eventos que estão disponíveis por meio de um domínio de contas, deve-se provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}} em um espaço do Cloud Foundry na região em que deseja monitorar a atividade da API. Somente o **proprietário da conta** pode ver eventos de conta.

Para visualizar os eventos que estão disponíveis por meio de um domínio de espaço, deve-se provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}} no espaço em que deseja monitorar a atividade da API.

Para saber como provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}, veja [Provisionando o serviço {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).



## Analisando logs de atividades
{: #analyze}

É possível analisar logs de atividades por meio da IU do {{site.data.keyword.cloudaccesstrailshort}} no {{site.data.keyword.Bluemix_notm}} ou usando o Kibana, uma ferramenta de software livre. É possível monitorar eventos que estão disponíveis em um espaço específico ou no nível de conta.

É possível procurar, analisar e monitorar logs de atividades durante as últimas 24 horas por meio da IU do {{site.data.keyword.cloudaccesstrailshort}} no {{site.data.keyword.Bluemix_notm}}. Para obter mais informações, veja [Navegando para a UI do {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_at_ui.html#launch_at_ui).

É possível procurar, analisar e monitorar os logs de atividades nos últimos 3 dias por meio do Kibana usando o painel Kibana do {{site.data.keyword.cloudaccesstrailshort}} ou criando seus próprios painéis customizados. * **Nota:** esse recurso está disponível para usuários do plano **Premium**.

* Para obter mais informações sobre como ativar o Kibana, veja [Navegando para o painel Kibana](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana). 
* Para obter uma lista de campos que podem ser usados para analisar eventos no Kibana, consulte [Campos de eventos do {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/at_event.html#at_event)



## Regiões
{: #regions}

O serviço {{site.data.keyword.cloudaccesstrailshort}} está disponível nas regiões a seguir:

* Alemanha
* Sydney
* Reino Unido 
* Sul dos EUA


## Plano de serviço
{: #plan}

O {{site.data.keyword.cloudaccesstrailshort}} serviço fornece vários planos.

É possível mudar um plano por meio da UI do {{site.data.keyword.Bluemix_notm}} ou da linha de comandos. É possível fazer upgrade ou reduzir seu plano a qualquer momento. Para obter mais informações sobre upgrades de plano de serviço, veja [Mudando o plano](/docs/services/cloud-activity-tracker/how-to/change_plan.html#change_plan). 

A tabela a seguir descreve os planos que estão disponíveis:

<table>
    <caption>Tabela 1. Recursos para ingestão de eventos, retenção de eventos e exportação de eventos</caption>
      <tr>
        <th>Planejar</th>
        <th>Ingestão de eventos</th>
        <th>Retenção de eventos</th>
		<th>Exportar eventos</th>
      </tr>
      <tr>
        <td>Lite (padrão)</td>
        <td>Não</td>
        <td>Últimos 3 dias</td>
		<td>Não</td>
      </tr>
      <tr>
        <td>Premium</td>
        <td>Sim</td>
        <td>O número configurável de dias.</td>
		<td>Sim</td>
      </tr>
</table>

<table>
    <caption>Tabela 2. Recursos para gerenciar e visualizar eventos</caption>
      <tr>
        <th>Planejar</th>
		    <th>API</th>
		    <th>CLI</th>
        <th>Kibana</th>
      </tr>
      <tr>
        <td>Lite (padrão)</td>
		    <td>Não</td>
		    <td>Não</td>
        <td>Não</td>
      </tr>
      <tr>
        <td>Premium</td>
		    <td>Sim</td>
		    <td>Sim</td>
        <td>Sim</td>
      </tr>
</table>

**Nota:** o custo mensal de armazenamento de eventos é calculado como uma média do ciclo de faturamento.

## Segurança
{: #security}

Considere as informações a seguir sobre a segurança ao trabalhar com o serviço {{site.data.keyword.cloudaccesstrailshort}}:

* Os serviços IBM que geram eventos do {{site.data.keyword.cloudaccesstrailshort}} seguem a política de segurança do {{site.data.keyword.IBM_notm}} Cloud. Para obter mais informações, veja [Confiar na segurança e privacidade do IBM Cloud ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud-computing/learn-more/why-ibm-cloud/security/){: new_window}.
* O serviço {{site.data.keyword.cloudaccesstrailshort}} captura ações iniciadas pelo usuário que mudam o estado de serviços de nuvem. As informações não fornecem acesso direto a bancos de dados ou aplicativos.
* Somente usuários autorizados podem visualizar e monitorar os logs de eventos do {{site.data.keyword.cloudaccesstrailshort}}. Cada usuário é identificado por seu ID exclusivo no {{site.data.keyword.Bluemix_notm}}.
