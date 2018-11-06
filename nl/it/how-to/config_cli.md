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


# Configurazione della CLI del programma di traccia dell'attività
{: #config_cli}

Il servizio {{site.data.keyword.cloudaccesstraillong}} include una CLI (command line interface) che puoi utilizzare per gestire i tuo eventi nel cloud. Puoi utilizzare il plugin {{site.data.keyword.Bluemix_notm}} per visualizzare lo stato degli eventi, per scaricare gli eventi e per configurare la politica di conservazione degli eventi. La CLI offre diversi tipi di assistenza: il supporto generale per informazioni sulla CLI e i comandi supportati, il supporto sul comando per informazioni su come utilizzare un comando o il supporto su un comando secondario per informazioni su come utilizzare i comandi secondari di un comando.
{:shortdesc}


## Installazione del plugin {{site.data.keyword.cloudaccesstrailshort}} dal repository {{site.data.keyword.Bluemix_notm}} 
{: #install_cli_repo}

Per installare la CLI di {{site.data.keyword.cloudaccesstrailshort}}, completa la seguente procedura:

1. Installa la CLI {{site.data.keyword.Bluemix_notm}}.

   Per ulteriori informazioni, consulta [Installazione della CLI {{site.data.keyword.Bluemix_notm}}](/docs/cli/reference/ibmcloud/download_cli.html#install_use).
   
2. Scopri il nome del plugin nel repository. Esegui il seguente comando:

    ```
    ibmcloud plugin repo-plugins
    ```
    {: codeblock}
    
    Il nome del plugin è **activity-tracker**.

3. Installa il plugin {{site.data.keyword.cloudaccesstrailshort}}. Esegui il seguente comando:

    ```
    ibmcloud plugin install activity-tracker -r Bluemix
    ```
    {: codeblock}
 
4. Verifica che il plugin {{site.data.keyword.cloudaccesstrailshort}} sia installato.
  
    Ad esempio, immetti il seguente comando per visualizzare l'elenco di plugin installati:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
    L'output è simile al seguente:
   
    ```
    ibmcloud plugin list
    Listing installed plug-ins...

    Plugin Name               Version   
    activity-tracker          3.3.0   
    ```
    {: screen}


## Installazione del plugin {{site.data.keyword.cloudaccesstrailshort}} da un file
{: #install_cli}

Per installare la CLI di {{site.data.keyword.cloudaccesstrailshort}}, completa la seguente procedura:

1. Installa la CLI {{site.data.keyword.Bluemix_notm}}.

   Per ulteriori informazioni, consulta [Installazione della CLI {{site.data.keyword.Bluemix_notm}}](/docs/cli/reference/ibmcloud/download_cli.html#install_use).

2. Installa il plugin {{site.data.keyword.cloudaccesstrailshort}}. 

    * Per Linux, consulta [Installazione del plugin {{site.data.keyword.cloudaccesstrailshort}} su Linux](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_linux).
    * Per Windows, consulta [Installazione del plugin {{site.data.keyword.cloudaccesstrailshort}} su Windows](/docs/services/cloud-activity-tracker/how-to/config_cli.html#install_cli_windows).
    * Per Mac OS X, consulta [Installazione del plugin {{site.data.keyword.cloudaccesstrailshort}} su Mac OS X ](/docs/services//cloud-activity-tracker/how-to/config_cli.html#install_cli_mac).
 
3. Verifica l'installazione del plugin CLI.
  
    Ad esempio, controlla la versione del plugin. Esegui il seguente comando:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
    L'output è simile al seguente:
   
    ```
    ibmcloud plugin list
    Listing installed plug-ins...

    Plugin Name               Version   
    activity-tracker          3.3.0   
    ```
    {: screen}
 


## Installazione del plugin di Log Analysis su Linux da un file
{: #install_cli_linux}

Completa le seguenti istruzioni per installare il plugin Raccolta dei log su Linux:

1. Installa il plugin.

    Scarica l'ultima release del plugin CLI del servizio (activity-tracker) {{site.data.keyword.cloudaccesstrailshort}} dalla [pagina CLI {{site.data.keyword.Bluemix_notm}}](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	* Seleziona il valore della piattaforma: **linux64**. 
	
	* Fai clic su **Salva file**. 
    
2. Installa il plugin. Esegui il seguente comando:
        
    ```
    ibmcloud plugin install -f activity-tracker-linux-amd64-3.3.0
    ```
    {: codeblock}




## Installazione del plugin di Log Analysis su Windows da un file
{: #install_cli_windows}

Completa le seguenti istruzioni per installare il plugin Raccolta dei log su Windows:

1. Scarica l'ultima release del plugin CLI del servizio (activity-tracker) {{site.data.keyword.cloudaccesstrailshort}} dalla [pagina CLI {{site.data.keyword.Bluemix_notm}}](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	1. Seleziona il valore della piattaforma: **win64**. 
	2. Fai clic su **Salva file**.  
    
2. Installa il plugin. Esegui il seguente comando:
        
    ```
    ibmcloud plugin install -f activity-tracker-windows-amd64-3.3.0.exe
    ```
    {: codeblock}

	

## Installazione del plugin di Log Analysis su Mac OS X da un file
{: #install_cli_mac}

Completa le seguenti istruzioni per installare il plugin Raccolta dei log su Mac OS X:

1. Scarica l'ultima release del plugin CLI del servizio (activity-tracker) {{site.data.keyword.cloudaccesstrailshort}} dalla [pagina CLI {{site.data.keyword.Bluemix_notm}}](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins). 
	
	1. Seleziona il valore della piattaforma: **osx**. 
	2. Fai clic su **Salva file**.  
    
2. Installa il plugin. Esegui il seguente comando:
        
    ```
    ibmcloud plugin install -f activity-tracker-darwin-amd64-3.3.0
    ```
    {: codeblock}

	
	
## Disinstallazione della CLI di Log Analysis
{: #uninstall_cli}

Per disinstallare la CLI, elimina il plugin.
{:shortdesc}

Completa le seguenti istruzioni per eliminare la CLI del servizio {{site.data.keyword.cloudaccesstrailshort}}: 

1. Verifica la versione del plugin CLI installato. 
  
    Ad esempio, controlla la versione del plugin. Esegui il seguente comando:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
    L'output è simile al seguente:
   
    ```
    ibmcloud plugin list
    Listing installed plug-ins...

    Plugin Name          Version   
    activity-tracker      3.3.0   
    ```
    {: screen}
    
2. Se il plugin è installato, esegui `ibmcloud plugin uninstall` per disinstallare il plugin CLI.

    Esegui il seguente comando:
        
    ```
    ibmcloud plugin uninstall activity-tracker
    ```
    {: codeblock}
  

## Aggiornamento della CLI di Log Analysis dal repository
{: #update_cli}

Per aggiornare la CLI, esegui il comando *ibmcloud plugin update*.
{:shortdesc}

Completa le seguenti istruzioni per aggiornare la CLI del servizio {{site.data.keyword.cloudaccesstrailshort}}: 

1. Aggiorna il plugin {{site.data.keyword.cloudaccesstrailshort}}. Esegui il seguente comando:

    ```
    ibmcloud plugin update activity-tracker -r Bluemix
    ```
    {: codeblock}
 
2. Verifica l'installazione del plugin CLI.
  
    Ad esempio, verifica la versione del plugin. Esegui il seguente comando:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
    L'output è simile al seguente:
   
    ```
    ibmcloud plugin list
    Listing installed plug-ins...

    Plugin Name             Version   
    activity-tracker         3.3.0   
    ```
    {: screen}





## Come ottenere supporto generale
{: #general_cli_help}

Per ottenere le informazioni generali sulla CLI e su quali comandi sono supportati, completa la seguente procedura:

1. Accedi a uno spazio, organizzazione, regione in {{site.data.keyword.Bluemix_notm}}. 
    
2. Elenca le informazioni sui comandi supportati e sulla CLI. Esegui il seguente comando:

    ```
    ibmcloud at help 
    ```
    {: codeblock}
    
    

## Ottenere supporto per un comando
{: #command_cli_help}

Per ottenere supporto sull'utilizzo di un comando, completa la seguente procedura:

1. Accedi a uno spazio, organizzazione, regione in {{site.data.keyword.Bluemix_notm}}. 
    
2. Ottieni un elenco di comandi supportati e identifica quello di cui hai bisogno. Esegui il comando:

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. Ottenere supporto sul comando. Esegui il seguente comando:

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    dove *Command* è il nome di un comando CLI, ad esempio, *status*.



## Ottenere supporto per un comando secondario
{: #subcommand_cli_help}

Un comando può avere comandi secondari. Per ottenere supporto sui comandi secondari, completa la seguente procedura:

1. Accedi a uno spazio, organizzazione, regione in {{site.data.keyword.Bluemix_notm}}. 
    
2. Ottieni un elenco di comandi supportati e identifica quello di cui hai bisogno. Esegui il comando:

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. Ottieni supporto sul comando e identifica i comandi secondari supportati. Esegui il seguente comando:

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    dove *Command* è il nome di un comando CLI, ad esempio, *session*.

4. Ottieni supporto sul comando e identifica i comandi secondari supportati. Esegui il seguente comando:

    ```
    ibmcloud at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    dove 
    
    * *Command* è il nome di un comando CLI, ad esempio, *status*.
    * *Subcommand* è il nome di un comando secondario supportato, ad esempio, per il comando *session*, un comando secondario valido è *list*.


## Mostra i dettagli del plugin
{: #show}
  
Utilizza il comando 'ibmcloud plugin show activity-tracker' per visualizzare i dettagli del plugin. 

```
ibmcloud plugin show activity-tracker
```
{: codeblock}
    
L'output è simile al seguente:
   
```
ibmcloud plugin show activity-tracker
                                  
Plugin                         activity-tracker   
Version                        3.3.0   
SDK Version                       
Minimal CLI version required   N/A      
```
{: screen}



