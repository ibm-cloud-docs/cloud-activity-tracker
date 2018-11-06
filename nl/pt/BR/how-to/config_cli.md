---

copyright:
  years: 2016, 2018
lastupdated: "2018-09-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Configurando a CLI do Activity Tracker
{: #config_cli}

O serviço {{site.data.keyword.cloudaccesstraillong}} inclui uma interface da linha de comandos (CLI) que pode ser usada para gerenciar seus eventos na nuvem. É possível usar o plug-in do {{site.data.keyword.Bluemix_notm}} para visualizar o status dos eventos, para fazer download de eventos e para configurar a política de retenção de eventos. A CLI oferece diferentes tipos de ajuda: ajuda geral para aprender sobre a CLI e os comandos suportados, ajuda de comando para aprender como usar um comando ou ajuda de subcomando para aprender como usar um subcomando para um comando.
{:shortdesc}


## Instalando o plug-in {{site.data.keyword.cloudaccesstrailshort}} por meio do repositório do {{site.data.keyword.Bluemix_notm}}
{: #install_cli_repo}

Para instalar a CLI do {{site.data.keyword.cloudaccesstrailshort}}, conclua as etapas a seguir:

1. Instale a CLI do {{site.data.keyword.Bluemix_notm}}.

   Para obter mais informações, consulte [Instalando a CLI do {{site.data.keyword.Bluemix_notm}}](/docs/cli/reference/ibmcloud/download_cli.html#install_use).
   
2. Descubra o nome do plug-in no repositório. Execute o seguinte comando:

    ```
    ibmcloud plugin repo-plugins
    ```
    {: codeblock}
    
    O nome do plugin é **activity-tracker**.

3. Instale o plug-in {{site.data.keyword.cloudaccesstrailshort}}. Execute o seguinte comando:

    ```
    ibmcloud plugin install activity-tracker -r Bluemix
    ```
    {: codeblock}
 
4. Verifique se o plug-in do {{site.data.keyword.cloudaccesstrailshort}} está instalado.
  
    Por exemplo, execute o comando a seguir para ver a lista de plug-ins que estão instalados:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
    A saída é semelhante ao seguinte:
   
    ```
    ibmcloud plugin list Listing installed plug-ins...

    Plugin Name Version   
    activity-tracker 3.3.0   
    ```
    {: screen}


## Instalando o plug-in {{site.data.keyword.cloudaccesstrailshort}} por meio de um arquivo
{: #install_cli}

Para instalar a CLI do {{site.data.keyword.cloudaccesstrailshort}}, conclua as etapas a seguir:

1. Instale a CLI do {{site.data.keyword.Bluemix_notm}}.

   Para obter mais informações, consulte [Instalando a CLI do {{site.data.keyword.Bluemix_notm}}](/docs/cli/reference/ibmcloud/download_cli.html#install_use).

2. Instale o plug-in {{site.data.keyword.cloudaccesstrailshort}}.

    * Para Linux, veja [Instalando o plug-in {{site.data.keyword.cloudaccesstrailshort}} no Linux](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_linux).
    * Para Windows, veja [Instalando o plug-in {{site.data.keyword.cloudaccesstrailshort}} no Windows](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_windows).
    * Para Mac OS X, veja [Instalando o plug-in {{site.data.keyword.cloudaccesstrailshort}} no Mac OS X](/docs/services//cloud-activity-tracker/how-to/config_cli.html#install_cli_mac).
 
3. Verifique a instalação do plug-in da CLI.
  
    Por exemplo, verifique a versão do plug-in. Execute o seguinte comando:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
    A saída é semelhante ao seguinte:
   
    ```
    ibmcloud plugin list Listing installed plug-ins...

    Plugin Name Version   
    activity-tracker 3.3.0   
    ```
    {: screen}
 


## Instalando o plug-in Log Analysis no Linux por meio de um arquivo
{: #install_cli_linux}

Conclua as etapas a seguir para instalar o plug-in Coleção de logs no Linux:

1. Instale o plug-in.

    Faça download da liberação mais recente do plug-in da CLI do serviço {{site.data.keyword.cloudaccesstrailshort}} (rastreador de atividade) [na página da CLI do {{site.data.keyword.Bluemix_notm}}](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	* Selecione o valor de plataforma: **linux64**. 
	
	* Clique em **Salvar arquivo**. 
    
2. Instale o plug-in. Execute o seguinte comando:
        
    ```
    ibmcloud plugin install -f activity-tracker-linux-amd64-3.3.0
    ```
    {: codeblock}




## Instalando o plug-in Log Analysis no Windows por meio de um arquivo
{: #install_cli_windows}

Conclua as etapas a seguir para instalar o plug-in Coleção de logs no Windows:

1. Faça download da liberação mais recente do plug-in da CLI do serviço {{site.data.keyword.cloudaccesstrailshort}} (rastreador de atividade) [na página da CLI do {{site.data.keyword.Bluemix_notm}}](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	1. Selecione o valor de plataforma: **win64**. 
	2. Clique em **Salvar arquivo**.  
    
2. Instale o plug-in. Execute o seguinte comando:
        
    ```
    ibmcloud plugin install -f activity-tracker-windows-amd64-3.3.0.exe
    ```
    {: codeblock}

	

## Instalando o plug-in Log Analysis no Mac OS X por meio de um arquivo
{: #install_cli_mac}

Conclua as etapas a seguir para instalar o plug-in Coleção de logs no Mac OS X:

1. Faça download da liberação mais recente do plug-in da CLI do serviço {{site.data.keyword.cloudaccesstrailshort}} (rastreador de atividade) [na página da CLI do {{site.data.keyword.Bluemix_notm}}](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	1. Selecione o valor da plataforma: **osx**. 
	2. Clique em **Salvar arquivo**.  
    
2. Instale o plug-in. Execute o seguinte comando:
        
    ```
    ibmcloud plugin install -f activity-tracker-darwin-amd64-3.3.0
    ```
    {: codeblock}

	
	
## Desinstalando a CLI do Log Analysis
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
    
    A saída é semelhante ao seguinte:
   
    ```
    ibmcloud plugin list Listing installed plug-ins...

    Plugin Name Version   
    activity-tracker 3.3.0   
    ```
    {: screen}
    
2. Se o plug-in estiver instalado, execute o `ibmcloud plugin uninstall` para desinstalar o plug-in da CLI.

    Execute o seguinte comando:
        
    ```
    ibmcloud plugin uninstall activity-tracker
    ```
    {: codeblock}
  

## Atualizando a CLI do Log Analysis por meio do repositório
{: #update_cli}

Para atualizar a CLI, execute o comando *ibmcloud plugin update*.
{:shortdesc}

Conclua as etapas a seguir para atualizar a CLI de serviço do {{site.data.keyword.cloudaccesstrailshort}}:

1. Atualize o plug-in do {{site.data.keyword.cloudaccesstrailshort}}. Execute o seguinte comando:

    ```
    ibmcloud plugin update activity-tracker -r Bluemix
    ```
    {: codeblock}
 
2. Verifique a instalação do plug-in da CLI.
  
    Por exemplo, verifique a versão do plug-in. Execute o seguinte comando:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
    A saída é semelhante ao seguinte:
   
    ```
    ibmcloud plugin list Listing installed plug-ins...

    Plugin Name Version   
    activity-tracker 3.3.0   
    ```
    {: screen}





## Obtendo ajuda geral
{: #general_cli_help}

Para obter informações gerais sobre a CLI e quais comandos são suportados, conclua as etapas a seguir:

1. Efetue login em uma região, uma organização e um espaço no {{site.data.keyword.Bluemix_notm}}. 
    
2. Liste informações sobre os comandos suportados e a CLI. Execute o seguinte comando:

    ```
    ibmcloud at help
    ```
    {: codeblock}
    
    

## Obtendo ajuda sobre um comando
{: #command_cli_help}

Para obter ajuda sobre como usar um comando, conclua as etapas a seguir:

1. Efetue login em uma região, uma organização e um espaço no {{site.data.keyword.Bluemix_notm}}. 
    
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
    
    em que *Command* é o nome de um comando da CLI, por exemplo, *status*.



## Obtendo ajuda sobre um subcomando
{: #subcommand_cli_help}

Um comando pode ter subcomandos. Para obter ajuda sobre subcomandos, conclua as etapas a seguir:

1. Efetue login em uma região, uma organização e um espaço no {{site.data.keyword.Bluemix_notm}}. 
    
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
    
    em que *Command* é o nome de um comando da CLI, por exemplo, *session*.

4. Obtenha ajuda sobre o comando e identifique os subcomandos suportados. Execute o seguinte comando:

    ```
    ibmcloud at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    em que 
    
    * *Command* é o nome de um comando da CLI, por exemplo, *status*.
    * *Subcommand* é o nome de um subcomando suportado, por exemplo, para o comando *session*, um subcomando válido é *list*.


## Mostrar os detalhes do plug-in
{: #show}
  
Use o comando 'ibmcloud plugin show activity-tracker' para mostrar os detalhes do plug-in. 

```
ibmcloud plugin show activity-tracker
```
{: codeblock}
    
A saída é semelhante ao seguinte:
   
```
ibmcloud plugin show activity-tracker

Plugin                         activity-tracker
Version                        3.3.0
SDK Version
Minimal CLI version required   N/A
```
{: screen}



