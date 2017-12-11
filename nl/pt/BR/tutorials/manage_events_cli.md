---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-07"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Gerenciando eventos usando a CLI do Activity Tracker
{: #tutorial2}

Use este tutorial para aprender como usar a CLI do {{site.data.keyword.cloudaccesstrailshort}} para gerenciar eventos por meio da linha de comandos. Saiba como obter informações sobre eventos armazenados, como fazer download de eventos que são armazenados no {{site.data.keyword.IBM_notm}} Cloud ou como excluir eventos.
{:shortdesc}

Conclua
as etapas a seguir:

1. [Provisionar o serviço {{site.data.keyword.IBM_notm}} Key Protect e gerar eventos](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step1)
2. [Obter informações sobre eventos armazenados (cf at status)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step2)
2. [Especifique de quais logs fazer download criando uma sessão (cf at session create)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step3)
3. [Obter os dados do log real (cf at download)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step4)
4. [Excluir a sessão após a conclusão do download (cf at session delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step5)
5. [Excluir manualmente os logs que não são necessários (cf at delete)](/docs/services/cloud-activity-tracker/tutorials/manage_events_cli.html#step6)


## Suposições
{: #assumptions}

1. Você tem um ID do usuário do {{site.data.keyword.Bluemix_notm}} que tem permissões de desenvolvedor para trabalhar em um espaço de uma conta do {{site.data.keyword.Bluemix_notm}} em que o serviço {{site.data.keyword.IBM_notm}} Cloud {{site.data.keyword.cloudaccesstrailshort}} é provisionado. 

    Para obter mais informações sobre como provisionar o serviço {{site.data.keyword.cloudaccesstrailshort}}, veja [Provisionando o serviço {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/how-to/provision.html#provision).

2. Você instalou o plug-in CF do {{site.data.keyword.cloudaccesstrailshort}} no sistema local. Isso é necessário para que seja possível usar a CLI do {{site.data.keyword.cloudaccesstrailshort}} para gerenciar eventos por meio da linha de comandos. 

    Para obter mais informações sobre como instalar o plug-in CF do {{site.data.keyword.cloudaccesstrailshort}}, veja [Configurando a CLI do {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#config_at_cli).

3. Você efetuou login no {{site.data.keyword.Bluemix_notm}} por meio da linha de comandos usando o comando a seguir:

    ```
    bx login -a Endpoint
    ```
    {: codeblock}
	
	Em que *Terminal* é a URL para efetuar login no {{site.data.keyword.Bluemix_notm}}. Essa URL é diferente por região.
	
	<table>
	    <caption>Lista de terminais para acessar o {{site.data.keyword.Bluemix_notm}}</caption>
		<tr>
		  <th>Região</th>
		  <th>URL</th>
		</tr>
		<tr>
		  <td>Sul dos EUA</td>
		  <td>api.ng.bluemix.net</td>
		</tr>
	</table>

    Por exemplo, execute o comando a seguir para efetuar login na região Sul dos EUA:
	
	```
	bx cf login -a api.ng.bluemix.net
	```
	{: codeblock}

	**Nota:** deve-se efetuar login na região, organização e espaço no {{site.data.keyword.Bluemix_notm}} em que o serviço {{site.data.keyword.cloudaccesstrailshort}} é provisionado para poder executar comandos do {{site.data.keyword.cloudaccesstrailshort}} e gerenciar seus eventos por meio da linha de comandos.
	
	Em seguida, configure a organização e o espaço. Execute o seguinte comando:

    ```
    bx target -o OrgName -s SpaceName
    ```
    {: codeblock}

    em que

    * OrgName é o nome da organização.
    * SpaceName é o nome do espaço.


## Etapa 1: provisionar o serviço IBM Key Protect e gerar eventos 
{: #step1}
	
1. Conclua as etapas a seguir para provisionar uma instância do serviço {{site.data.keyword.keymanagementserviceshort}} no {{site.data.keyword.Bluemix_notm}}:

    1. Efetue login em sua conta do {{site.data.keyword.Bluemix_notm}}.

        O painel do {{site.data.keyword.Bluemix_notm}} pode ser localizado em: [http://bluemix.net](http://bluemix.net)

        Depois de efetuar login com seu ID de usuário e senha, a UI do {{site.data.keyword.Bluemix_notm}} é aberta.

    2. Clique em **Catálogo**. A lista dos serviços que estão disponíveis no {{site.data.keyword.Bluemix_notm}} é aberta.

        Selecione a categoria **Segurança** para filtrar a lista de serviços que é exibida.

    3. Selecione o tile **Key Protect**.

    4. Clique em **Criar** para provisionar o serviço do {{site.data.keyword.keymanagementserviceshort}} no espaço do {{site.data.keyword.Bluemix_notm}} no qual você está com login efetuado.

2. Conclua as etapas a seguir para gerar um evento do {{site.data.keyword.cloudaccesstrailshort}}:

    1. No painel {{site.data.keyword.Bluemix_notm}}, selecione o serviço {{site.data.keyword.keymanagementserviceshort}}. O painel {{site.data.keyword.keymanagementserviceshort}} se abre. Em seguida, selecione a guia **Gerenciar**.

    2. Clique em **Incluir Chave**. Uma nova janela é aberta.

        ![{{site.data.keyword.keymanagementserviceshort}} janela para incluir chaves](images/KP_f2.gif)

    3. Selecione **Gerar chave** e conclua as etapas a seguir:

        * Insira um nome para a chave, por exemplo, *MyFirstKey*.

        * Escolha um algoritmo para a chave.

        * Clique em **Incluir chave**. 

3. Verifique se um evento foi criado:

    1. No Painel do {{site.data.keyword.Bluemix_notm}}, selecione o serviço {{site.data.keyword.cloudaccesstrailshort}}. O painel do serviço é aberto.

    2. Configure a visualização para procurar eventos do {{site.data.keyword.keymanagementserviceshort}} que foram gerados quando você provisionou o serviço e incluiu uma chave.

        * Selecione **Logs de espaço** para o campo *Visualizar logs*.
	    * Selecione **target.name** para o campo *Campo de procura*.
	    * Insira **ibm-key-protect** no campo *Filtro*.
	
	    Os dados que são exibidos correspondem a eventos do {{site.data.keyword.keymanagementserviceshort}} que estão disponíveis para as últimas 24 horas. 

	    ![{{site.data.keyword.cloudaccesstrailshort}} guia gerenciar](images/KP_f3.gif)

## Etapa 2: obter informações sobre eventos armazenados
{: #step2}

Verifique quais eventos estão disponíveis para download. Por exemplo, se você provisionar e incluir uma chave na data atual, execute o comando a seguir para obter informações sobre eventos coletados hoje:

```
bx cf at status -s 2017-07-25 -e 2017-07-25
+------------+-------+-------+------------+
| Date       | Count | Size  | Searchable |
+------------+-------+-------+------------+
| 2017-07-25 | 12    | 34994 | All        |
+------------+-------+-------+------------+
```
{: screen}

Esse comando contará os eventos para 25 de junho de 2017.  {{site.data.keyword.cloudaccesstrailshort}} é um serviço global, portanto, os dias são em Horário Universal. Para obter um dia de horário local completo, você provavelmente precisará fazer download de múltiplos dias de UTC.

Para ver as informações para múltiplos dias, use `-s` para configurar o dia de início e `-e` para configurar a data de encerramento. 

Para saber mais sobre o comando `cf at status`, consulte a [Referência da CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#status).

Use `bx cf at help status` para obter ajuda por meio da linha de comandos.

## Etapa 3: especificar de quais eventos fazer download
{: #step3}

Antes de fazer download de eventos, crie uma sessão:

* A sessão especifica quais eventos serão transferidos por download.
* Se o download dos eventos for interrompido, a sessão permitirá retomar o download de onde ele parou.

Use o comando a seguir para cria uma sessão:

```
bx cf at session create -s 2017-07-25 -e 2017-07-25
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| id           | 21b19aeb-3d32-4c60-b912-517609c62db2      |
| space        | 667fb895-b5f5-46c9-9f0e-cf4587341095      |
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T18:33:22.678350874Z            |
| access-time  | 2017-07-25T18:33:22.678350874Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
+--------------+-------------------------------------------+
```

Há uma data de início e data de encerramento associadas a uma sessão. O comando de download incluirá eventos entre essas datas inclusivas. O intervalo de data padrão é somente o dia atual. 

A parte importante da saída do comando é o `Id` de sessão. Ele é referenciado no comando de download.

Para obter informações sobre sessões existentes, digite `cf at session list`.

Para saber mais sobre as sessões e o comando `cf at session create`, consulte a [Referência da CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_create).

Use `cf at session help create` para obter ajuda por meio da linha de comandos.

## Etapa 4: fazer download de eventos que são identificados para o escopo definido para a sessão
{: #step4}

Para fazer download dos eventos especificados pelos parâmetros de sessão, execute o comando a seguir:

```
$ bx cf at events download -o events.log 21b19aeb-3d32-4c60-b912-517609c62db2
 6.70 KiB / 3.06 KiB [================================================================================================================================================================] 219.03% 8.60 MiB/s 0s
Download Successful
```

* O parâmetro `-o` especifica um arquivo de saída.
* O ID de sessão é especificado por último. Você obtém o valor do ID de sessão da saída do comando `cf at session create`.
* O indicador de progresso é movido de 0 a 100% conforme os eventos são transferidos por download.

O formato dos dados transferidos por download é compactado como JSON. 

Para saber mais sobre o comando `cf at download`, consulte a [Referência da CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#download).

Use `bx cf at help download` para obter ajuda por meio da linha de comandos.

## Etapa 5: excluir a sessão
{: #step5}

Após a conclusão do download, exclua a sessão. 

O número de sessões é limitado. Uma sessão não é excluída automaticamente. Deve-se excluir manualmente as sessões que não são necessárias. 

```
$ bx cf at session delete 21b19aeb-3d32-4c60-b912-517609c62db2
+---------+------------------------+
| name    | value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```

Para saber mais sobre o comando `cf at session delete`, consulte a [Referência da CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#session_delete).

Use `bx cf at session help delete` para obter ajuda por meio da linha de comandos.

## Etapa 6: excluir eventos do Activity Tracker manualmente
{: #step6}

Você tem controle de sua própria retenção de eventos no {{site.data.keyword.cloudaccesstrailshort}}. É possível excluir eventos manualmente ou automatizar a exclusão de eventos.

Para excluir eventos manualmente, execute o comando `cf at delete`. Por
exemplo,

```
$ bx cf at delete -s 2017-07-25 -e 2017-07-25
Deleted successfully
"6 logs were deleted,freeing 13737 bytes."
```

Para saber mais sobre o comando `cf at delete`, consulte a [Referência da CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#delete).

Use `bx cf at help delete` para obter ajuda por meio da linha de comandos.

**Nota:** para excluir os eventos automaticamente, é possível configurar uma política de retenção usando o comando da CLI `cf at option`. Para obter mais informações, veja [Referência da CLI](/docs/services/cloud-activity-tracker/cli/at_cli.html#option)


