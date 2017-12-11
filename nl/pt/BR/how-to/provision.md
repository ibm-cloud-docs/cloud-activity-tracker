---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-17"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Provisionando o serviço Activity Tracker
{: #provision}

É possível provisionar o serviço {{site.data.keyword.cloudaccesstraillong}} por meio da UI do {{site.data.keyword.Bluemix}} ou por meio da linha de comandos.
{:shortdesc}


## Provisionando por meio da UI
{: #ui}

Conclua as etapas a seguir para provisionar uma instância do serviço {{site.data.keyword.cloudaccesstraillong_notm}} no {{site.data.keyword.Bluemix_notm}}:

1. Efetue login em sua conta do {{site.data.keyword.Bluemix_notm}}.

    O painel do {{site.data.keyword.Bluemix_notm}} pode ser localizado em: [http://bluemix.net ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](http://bluemix.net){:new_window}.
    
	Depois de efetuar login com seu ID de usuário e senha, a UI do {{site.data.keyword.Bluemix_notm}} é aberta.

2. Clique em **Catálogo**. A lista dos serviços que estão disponíveis no {{site.data.keyword.Bluemix_notm}} é aberta.

3. Selecione a categoria **Segurança** para filtrar a lista de serviços que é exibida.

    O serviço também está disponível sob a categoria **DevOps**.

4. Clique no tile **Activity Tracker**.

5. Configure as informações que definem onde o serviço será provisionado. 

    Insira os dados conforme indicado na tabela a seguir: 

    <table>
	  <caption>Tabela 1. Campos que são necessários para provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}</caption>
	  <tr>
	    <th>Campo</th>
		<th>Valor</th>
	  </tr>
	  <tr>
	    <td>Selecionar região para implementar em:</td>
		<td>Os valores válidos são: Sul dos EUA, Reino Unido, Alemanha</td>
	  </tr>
	  <tr>
	    <td>Escolha uma organização:</td>
		<td>Selecione a organização na qual você planeja monitorar a atividade.</td>
	  </tr>
	  <tr>
	    <td>Escolha um espaço:</td>
		<td>Selecione o espaço na organização que você selecionou no qual planeja monitorar a atividade.</td>
	  </tr>
	</table>

6. Selecione um plano de serviço. 

    Por padrão, o plano **grátis** está configurado.

    Para obter mais informações, veja [Planos de serviço](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans).
	
7. Clique em **Criar** para provisionar o serviço do {{site.data.keyword.cloudaccesstrailshort}} no espaço do {{site.data.keyword.Bluemix_notm}} no qual você está com login efetuado.
  
 

## Provisionando por meio da CLI
{: #cli}

Conclua as etapas a seguir para provisionar uma instância do serviço do {{site.data.keyword.cloudaccesstraillong_notm}} no {{site.data.keyword.Bluemix_notm}} por meio da linha de comandos:

1. Instale a CLI do Cloud Foundry (CF). Se o CF CLI estiver instalado, continue com a próxima etapa.

   Para obter mais informações, veja [Instalando o cf CLI ![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](http://docs.cloudfoundry.org/cf-cli/install-go-cli.html){: new_window}. 
    
2. Efetue login em uma região, uma organização e um espaço do {{site.data.keyword.Bluemix_notm}}. 

    Por exemplo, para efetuar login na região sul dos EUA, execute o comando a seguir:

    ```
    cf login -a https://api.ng.bluemix.net
    ```
    {: codeblock}

    Siga as instruções. Insira suas credenciais do {{site.data.keyword.Bluemix_notm}}, selecione uma organização e um espaço.
	
3. Execute o comando `cf create-service` para provisionar uma instância.

    ```
	cf create-service service_name service_plan service_instance_name
	```
	{: codeblock}
	
	Em que
	
	* service_name é o nome do serviço, ou seja, **activityTracker**.
	* service_plan é o nome do plano de serviço. Para obter uma lista de planos, veja [Planos de serviço](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#plans).
	* service_instance_name é o nome que você deseja usar para a nova instância de serviço criada.
	
	Para obter mais informações sobre o comando cf, veja [cf create-service](/docs/cli/reference/cfcommands/index.html#cf_create-service).

	Por exemplo, para criar uma instância do serviço {{site.data.keyword.cloudaccesstrailshort}} com o plano Lite, execute o comando a seguir:
	
	```
	cf create-service activityTracker free my_activity_tracker_svc
	```
	{: codeblock}
	
4. Verifique se o serviço foi criado com sucesso. Execute o seguinte comando:

    ```	
	cf services
	```
	{: codeblock}
	
	A saída da execução do comando é semelhante ao seguinte:
	
	```
    Getting services in org MyOrg / space MySpace as xxx@yyy.com...
    OK
    
    name                           service                  plan                   bound apps              last operation
    my_activity_tracker_svc        activityTracker          free                                           create succeeded
	```
	{: screen}

	



