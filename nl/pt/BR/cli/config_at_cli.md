---

copyright: years: 2016, 2017 lastupdated: "2017-09-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Configurando a CLI do Activity Tracker
{: #config_at_cli}

O serviço {{site.data.keyword.cloudaccesstraillong}} inclui uma interface da linha de comandos (CLI) que pode ser usada para gerenciar seus eventos na nuvem. A CLI é um plug-in Cloud Foundry (CF). É possível usar comandos para visualizar o status dos eventos, para fazer download de eventos, para restaurar eventos, para descartar eventos e para configurar a política de retenção de eventos.
{:shortdesc}


## Instalando a CLI do Activity Tracker
{: #install_cli}

Para instalar a CLI do {{site.data.keyword.cloudaccesstrailshort}}, conclua as etapas a seguir:

1. Instale a CLI do {{site.data.keyword.Bluemix_notm}}.

    Para obter mais informações, veja [Instalar por meio de shell](/docs/cli/reference/bluemix_cli/download_cli.html#shell_install).
	
	Por exemplo, para instalar a CLI do {{site.data.keyword.Bluemix_notm}} no Linux, execute o comando a seguir:
	
	```
	curl -fsSL https://clis.ng.bluemix.net/install/linux | sh
	```
	{: codeblock}

2. Instale o plug-in CF do {{site.data.keyword.cloudaccesstrailshort}}.

    * Para Linux, veja [Instalando a CLI do {{site.data.keyword.cloudaccesstrailshort}} no Linux](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_linux).
    * Para Windows, veja [Instalando a CLI do {{site.data.keyword.cloudaccesstrailshort}} no Windows](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_windows).
    * Para Mac OS X, veja [Instalando a CLI do {{site.data.keyword.cloudaccesstrailshort}} no Mac OS X](/docs/services/cloud-activity-tracker/cli/config_at_cli.html#install_cli_mac).
 
3. Verifique a instalação do plug-in da CLI.
  
    Por exemplo, verifique a versão do plug-in. Execute o seguinte comando:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    A saída é semelhante ao seguinte:
   
    ```
    Chamando 'cf plugins'...

    Listing Installed Plugins...
    OK

    Nome do plug-in Versão Nome do comando Ajuda do comando IBM-ActivityTracker 3.0.2 at Plug-in do IBM Activity Tracker.
    ```
    {: screen}

	
## Instalando a CLI do Activity Tracker no Linux
{: #install_cli_linux}

Conclua as etapas a seguir para instalar o plug-in CF do {{site.data.keyword.cloudaccesstrailshort}} no Linux:

1. Instale o plug-in CLI do {{site.data.keyword.cloudaccesstrailshort}}.

    1. Faça download da liberação mais recente do plug-in da CLI do serviço {{site.data.keyword.cloudaccesstrailshort}} por meio da [página da CLI do Bluemix](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 
	
		Selecione o valor de plataforma: **linux64**. 
		Clique em **Salvar arquivo**. 
    
    2. Descompacte o plug-in.
    
        Por exemplo, para descompactar o arquivo ZIP do `activitytracker-cli-linux_x64_v3.0.2.gz`, execute o comando a seguir:
        
        ```
        gunzip activitytracker-cli-linux_x64_v3.0.2.gz
        ```
        {: codeblock}

    3. Torne o arquivo executável.
    
        Por exemplo, para tornar o arquivo `activitytracker-cli-linux_x64_v3.0.2` executável, execute o comando a seguir:
        
        ```
        chmod a+x activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

    4. Instale o plug-in CF de log.
    
        Por exemplo, para tornar o arquivo `activitytracker-cli-linux_x64_v3.0.2` executável, execute o comando a seguir:
        
        ```
        bx cf install-plugin -f activitytracker-cli-linux_x64_v3.0.2
        ```
        {: codeblock}

2. Verifique a instalação do plug-in da CLI.
  
    Por exemplo, verifique a versão do plug-in. Execute o seguinte comando:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    A saída é semelhante ao seguinte:
   
    ```
    Chamando 'cf plugins'...

    Listing Installed Plugins...
    OK

    Nome do plug-in Versão Nome do comando Ajuda do comando IBM-ActivityTracker 3.0.2 at Plug-in do IBM Activity Tracker.
    ```
    {: screen}


## Instalando a CLI do Activity Tracker no Windows
{: #install_cli_windows}

Conclua as etapas a seguir para instalar o plug-in CF do {{site.data.keyword.cloudaccesstrailshort}} no Windows:

1. Faça download da liberação mais recente do plug-in da CLI do serviço {{site.data.keyword.cloudaccesstrailshort}} por meio da [página da CLI do Bluemix](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins). 
	
	1. Selecione o valor de plataforma: **win64**. 
	2. Clique em **Salvar arquivo**.  
    
2. Execute o comando **cf install-plugins** para instalar o plug-in do {{site.data.keyword.cloudaccesstrailshort}} no Windows. 

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	em que *PluginName* é o nome do arquivo que foi transferido por download.
	
    Por exemplo, para instalar o plug-in no Windows, execute o comando a seguir em uma janela do terminal:
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    Quando o plug-in é instalado, você obtém a mensagem a seguir: `Plug-in IBM-ActivityTracker instalado com êxito.`

3. Verifique a instalação do plug-in da CLI.
  
    Por exemplo, verifique a versão do plug-in. Execute o seguinte comando:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    A saída é semelhante ao seguinte:
   
    ```
    Chamando 'cf plugins'...

    Listing Installed Plugins...
    OK

    Nome do plug-in Versão Nome do comando Ajuda do comando IBM-ActivityTracker 3.0.2 at Plug-in do IBM Activity Tracker.
    ```
    {: screen}



## Instalando a CLI do Activity Tracker no Mac OS X
{: #install_cli_mac}

Conclua as etapas a seguir para instalar o plug-in CF do {{site.data.keyword.cloudaccesstrailshort}} no Mac OS X:

1. Faça download da liberação mais recente do plug-in CLI do serviço {{site.data.keyword.cloudaccesstrailshort}} por meio de [a página CLI do Bluemix](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins).
	
	1. Selecione o valor de plataforma: **osx**. 
	2. Clique em **Salvar arquivo**.  
    
2. Execute o comando **cf install-plugin** para instalar o plug-in {{site.data.keyword.cloudaccesstrailshort}} no Mac OS X.

    ```
	bx cf install-plugin PluginName
	```
	{: codeblock}
	
	em que *PluginName* é o nome do arquivo que foi transferido por download.
	
    Por exemplo, para instalar o plug-in em um Mac OS X, execute o comando a seguir em um terminal:
	
	```
	bx cf install-plugin activitytracker-cli-mac_x64_v3.0.2
	```
	{: codeblock}
	
    Quando o plug-in é instalado, você obtém a mensagem a seguir: `Plug-in IBM-ActivityTracker instalado com êxito.`

3. Verifique a instalação do plug-in da CLI.
  
    Por exemplo, verifique a versão do plug-in. Execute o seguinte comando:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    A saída é semelhante ao seguinte:
   
    ```
    Chamando 'cf plugins'...

    Listing Installed Plugins...
    OK

    Nome do plug-in Versão Nome do comando Ajuda do comando IBM-ActivityTracker 3.0.2 at Plug-in do IBM Activity Tracker.
    ```
    {: screen}

	

## Atualizando a CLI do Activity Tracker
{: #update_cli}

Conclua as etapas a seguir para atualizar o plug-in CF do {{site.data.keyword.cloudaccesstrailshort}}:

1. Faça download da liberação mais recente do plug-in CLI do serviço {{site.data.keyword.cloudaccesstrailshort}} por meio de [a página CLI do Bluemix](https://clis.ng.bluemix.net/ui/repository.html#cf-plugins).
	
	1. Selecione o valor de plataforma: **win64** para Windows, **osx** para Mac OS X ou **linux64** para Linux.
	2. Clique em **Salvar arquivo**.  
    
2. Execute o comando **cf install-plugin** para atualizar o plug-in do {{site.data.keyword.cloudaccesstrailshort}} no Windows.

    ```
	bx cf install-plugin PluginName -f
	```
	{: codeblock}
	
	em que
	
	* *PluginName* é o nome do arquivo transferido por download.
	* *-f* é a opção que indica para desinstalar a versão antiga do plug-in e instalar a nova.
	
    Por exemplo, para atualizar o plug-in no Windows, execute o comando a seguir em uma janela do terminal:
	
	```
	bx cf install-plugin activitytracker-cli-windows_x64_v3.0.2.exe
	```
	{: codeblock}
	
    Quando o plug-in é instalado, você obtém a mensagem a seguir: `Plug-in IBM-ActivityTracker instalado com êxito.`

3. Verifique a instalação do plug-in da CLI.
  
    Por exemplo, verifique a versão do plug-in. Execute o seguinte comando:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    A saída é semelhante ao seguinte:
   
    ```
    Chamando 'cf plugins'...

    Listing Installed Plugins...
    OK

    Nome do plug-in Versão Nome do comando Ajuda do comando IBM-ActivityTracker 3.0.2 at Plug-in do IBM Activity Tracker.
    ```
    {: screen}

	
	
## Desinstalando a CLI do Activity Tracker
{: #uninstall_cli}

Para desinstalar a CLI do {{site.data.keyword.cloudaccesstrailshort}}, exclua o plug-in.
{:shortdesc}

Conclua as etapas a seguir para desinstalar a CLI do serviço {{site.data.keyword.cloudaccesstrailshort}}:

1. Verifique a versão do plug-in CLI do {{site.data.keyword.cloudaccesstrailshort}} que está instalada.

    Por exemplo, verifique a versão do plug-in. Execute o seguinte comando:
    
    ```
    bx cf plugins
    ```
    {: codeblock}
    
    A saída é semelhante ao seguinte:
   
    ```
    Listing Installed Plugins...
    OK

    Plugin Name           Version   Command Name   Command Help
    IBM-ActivityTracker   3.0.2           at       IBM Activity Tracker plug-in
    ```
    {: screen}
    
2. Se o plug-in estiver instalado, execute o `cf uninstall-plugin` para desinstalar o plug-in da CLI de criação de log.

    Execute o seguinte comando:
        
    ```
    bx cf uninstall-plugin IBM-ActivityTracker
    ```
    {: codeblock}
  
