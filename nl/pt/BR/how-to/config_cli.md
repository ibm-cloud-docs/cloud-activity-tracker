---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, config CLI

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

# Configurando a CLI do Activity Tracker
{: #config_cli}

O serviço do {{site.data.keyword.cloudaccesstraillong}} inclui uma interface da linha de comandos (CLI) que pode ser usada para gerenciar os seus eventos na nuvem. É possível usar o plug-in do {{site.data.keyword.cloud_notm}} para visualizar o status dos eventos, fazer download de eventos e configurar a política de retenção. A CLI oferece diferentes tipos de ajuda: ajuda geral para aprender sobre a CLI e comandos suportados, ajuda de comando para aprender como usar um comando ou ajuda de subcomando para aprender como usar um subcomando para um comando.
{:shortdesc}

O {{site.data.keyword.cloudaccesstrailfull}} foi descontinuado. A partir de 9 de maio de 2019, não é possível fornecer novas instâncias do {{site.data.keyword.cloudaccesstrailshort}}. As instâncias existentes do plano premium são suportadas até 30 de setembro de 2019. Para continuar o monitoramento da atividade de sua conta do {{site.data.keyword.cloud_notm}}, provisione uma instância do [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


## Instalando o plug-in do {{site.data.keyword.cloudaccesstrailshort}} por meio do repositório do {{site.data.keyword.cloud_notm}}
{: #install_cli_repo}

Para instalar a CLI do {{site.data.keyword.cloudaccesstrailshort}}, conclua as etapas a seguir:

1. Instale a CLI do {{site.data.keyword.cloud_notm}}.

   Para obter mais informações, consulte [Instalando a CLI do {{site.data.keyword.cloud_notm}} ](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).
   
2. Descubra o nome do plug-in no repositório. Execute o seguinte comando:

    ```
    ibmcloud plugin repo-plugins
    ```
    {: codeblock}
    
    O nome do plug-in é **activity-tracker**.

3. Instale o plug-in do {{site.data.keyword.cloudaccesstrailshort}}. Execute o seguinte comando:

    ```
    ibmcloud plugin install activity-tracker
    ```
    {: codeblock}
 
4. Verifique se o plug-in do {{site.data.keyword.cloudaccesstrailshort}} está instalado.
  
    Por exemplo, execute o comando a seguir para ver a lista de plug-ins que estão instalados:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## Instalando o plug-in do {{site.data.keyword.cloudaccesstrailshort}} por meio de um arquivo
{: #install_cli}

Para instalar a CLI do {{site.data.keyword.cloudaccesstrailshort}}, conclua as etapas a seguir:

1. Instale a CLI do {{site.data.keyword.cloud_notm}}.

   Para obter mais informações, consulte [Instalando a CLI do {{site.data.keyword.cloud_notm}} ](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).

2. Instale o plug-in do {{site.data.keyword.cloudaccesstrailshort}}.

    * Para Linux, consulte [Instalando o plug-in do {{site.data.keyword.cloudaccesstrailshort}} no Linux](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#install_cli_linux).
    * Para Windows, consulte [Instalando o plug-in do {{site.data.keyword.cloudaccesstrailshort}} no Windows](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#install_cli_windows).
    * Para Mac OS X, consulte [Instalando o plug-in do {{site.data.keyword.cloudaccesstrailshort}} no Mac OS X](/docs/services//cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#install_cli_mac).
 
3. Verifique a instalação do plug-in da CLI.
  
    Por exemplo, verifique a versão do plug-in. Execute o seguinte comando:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## Instalando o plug-in do {{site.data.keyword.cloudaccesstrailshort}} no Linux por meio de um arquivo
{: #install_cli_linux}

Conclua as etapas a seguir para instalar o plug-in no Linux:

1. Instale o plug-in.

    Faça download da liberação mais recente do plug-in da CLI do serviço {{site.data.keyword.cloudaccesstrailshort}} (activity-tracker) [na página da CLI do {{site.data.keyword.cloud_notm}}![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://plugins.cloud.ibm.com/ui/repository.html){:new_window}.
	
	* Selecione o valor de plataforma: **linux64**. 
	
	* Clique em **Salvar arquivo**. 
    
2. Instale o plug-in. Execute o seguinte comando:
        
    ```
    ibmcloud plugin install -f activity-tracker-linux-amd64-3.3.0
    ```
    {: codeblock}




## Instalando o plug-in do {{site.data.keyword.cloudaccesstrailshort}} no Windows por meio de um arquivo
{: #install_cli_windows}

Conclua as etapas a seguir para instalar o plug-in no Windows:

1. Faça download da liberação mais recente do plug-in da CLI do serviço {{site.data.keyword.cloudaccesstrailshort}} (activity-tracker) [na página da CLI do {{site.data.keyword.cloud_notm}}![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://plugins.cloud.ibm.com/ui/repository.html){:new_window}. 
	
	1. Selecione o valor de plataforma: **win64**. 
	2. Clique em **Salvar arquivo**.  
    
2. Instale o plug-in. Execute o seguinte comando:
        
    ```
    ibmcloud plugin install -f activity-tracker-windows-amd64-3.3.0.exe
    ```
    {: codeblock}

	

## Instalando o plug-in do {{site.data.keyword.cloudaccesstrailshort}} no Mac OS X por meio de um arquivo
{: #install_cli_mac}

Conclua as etapas a seguir para instalar o plug-in no Mac OS X:

1. Faça download da liberação mais recente do plug-in da CLI do serviço {{site.data.keyword.cloudaccesstrailshort}} (activity-tracker) [na página da CLI do {{site.data.keyword.cloud_notm}}![Ícone de link externo](../../../icons/launch-glyph.svg "Ícone de link externo")](https://plugins.cloud.ibm.com/ui/repository.html){:new_window}.
	
	1. Selecione o valor da plataforma `osx`. 
	2. Clique em **Salvar arquivo**.  
    
2. Instale o plug-in. Execute o seguinte comando:
        
    ```
    ibmcloud plugin install -f activity-tracker-darwin-amd64-3.3.0
    ```
    {: codeblock}

	
	
## Desinstalando a CLI do {{site.data.keyword.cloudaccesstrailshort}}
{: #uninstall_cli}

Para desinstalar a CLI, exclua o plug-in.
{:shortdesc}

Conclua as etapas a seguir para desinstalar a CLI do serviço {{site.data.keyword.cloudaccesstrailshort}}:

1. Verifique a versão do plug-in da CLI que está instalada.
  
    Por exemplo, verifique a versão do plug-in. Execute o seguinte comando:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
2. Se o plug-in estiver instalado, execute o `ibmcloud plugin uninstall` para desinstalar o plug-in da CLI.

    Execute o seguinte comando:
        
    ```
    ibmcloud plugin uninstall activity-tracker
    ```
    {: codeblock}
  

## Atualizando a CLI do {{site.data.keyword.cloudaccesstrailshort}} por meio do repositório
{: #update_cli}

Para atualizar a CLI, execute o comando *ibmcloud plugin update*.
{:shortdesc}

Conclua as etapas a seguir para atualizar a CLI de serviço do {{site.data.keyword.cloudaccesstrailshort}}:

1. Atualize o plug-in do {{site.data.keyword.cloudaccesstrailshort}}. Execute o seguinte comando:

    ```
    ibmcloud plugin update activity-tracker
    ```
    {: codeblock}
 
2. Verifique a instalação do plug-in da CLI.
  
    Por exemplo, verifique a versão do plug-in. Execute o seguinte comando:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    





## Obtendo ajuda geral
{: #general_cli_help}

Para obter informações gerais sobre a CLI e quais comandos são suportados, conclua as etapas a seguir:

1. Efetue login em uma região, uma organização e um espaço no {{site.data.keyword.cloud_notm}}. 
    
2. Liste informações sobre os comandos suportados e a CLI. Execute o seguinte comando:

    ```
    ibmcloud at help 
    ```
    {: codeblock}
    
    

## Obtendo ajuda sobre um comando
{: #command_cli_help}

Para obter ajuda sobre como usar um comando, conclua as etapas a seguir:

1. Efetue login em uma região, uma organização e um espaço no {{site.data.keyword.cloud_notm}}. 
    
2. Obtenha a lista de comandos suportados e identifique aquele que você precisa. Execute o
comando:

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. Obter ajuda sobre o comando. Execute o seguinte comando:

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    Em que *Command* é o nome de um comando da CLI, por exemplo, *status*.



## Obtendo ajuda sobre um subcomando
{: #subcommand_cli_help}

Um comando pode ter subcomandos. Para obter ajuda sobre subcomandos, conclua as etapas a seguir:

1. Efetue login em uma região, uma organização e um espaço no {{site.data.keyword.cloud_notm}}. 
    
2. Obtenha a lista de comandos suportados e identifique aquele que você precisa. Execute o
comando:

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. Obtenha ajuda sobre o comando e identifique os subcomandos suportados. Execute o seguinte comando:

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    Em que *Command* é o nome de um comando da CLI, por exemplo, *session*.

4. Obtenha ajuda sobre o comando e identifique os subcomandos suportados. Execute o seguinte comando:

    ```
    ibmcloud at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    Em que 
    
    *Command* é o nome de um comando da CLI, por exemplo, *status*.

    *Subcommand* é o nome de um subcomando suportado. Por exemplo, para o comando *session*, um subcomando válido é *list*.


## Mostre os detalhes do plug-in
{: #show}
  
Use o comando 'ibmcloud plugin show activity-tracker' para mostrar os detalhes do plug-in. 

```
ibmcloud plugin show activity-tracker
```
{: codeblock}
    




