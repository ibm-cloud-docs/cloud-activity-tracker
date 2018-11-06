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


# Configurazione della politica di conservazione degli eventi
{: #configuring_retention_policy}

Utilizza il comando **ibmcloud at option** per visualizzare e configurare la politica di conservazione che definisce il numero massimo di giorni in cui gli eventi vengono conservati in {{site.data.keyword.cloudaccesstrailshort}}. Per impostazione predefinita, la politica di conservazione è disabilitata e gli eventi vengono conservati indefinitamente. Dopo che il periodo di conservazione è scaduto, gli eventi vengono eliminati automaticamente.
{:shortdesc}

Puoi impostare la stessa politica di conservazione per tutti gli spazi nell'account o personalizzare il periodo di conservazione di uno spazio. 


## Disabilitazione della politica di conservazione degli eventi di uno spazio
{: #disable_retention_policy_space}

Per disabilitare una politica di conservazione, completa la seguente procedura:

1. Accedi a {{site.data.keyword.Bluemix_notm}}. 

    Esegui il comando [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) per accedere a {{site.data.keyword.Bluemix_notm}} e poi esegui il comando [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) per configurare l'organizzazione e lo spazio in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
	
2. Imposta il periodo di conservazione su **-1** per disabilitare il periodo di conservazione. Esegui il comando:

    ```
    ibmcloud at option -r -1
    ```
    {: codeblock}
    
**Esempio**
    
Ad esempio, per disabilitare il periodo di conservazione per uno spazio con ID *d35da1e3-b345-475f-8502-bx cfgh436902a3*, immetti il seguente comando:

```
ibmcloud at option -r -1
```
{: codeblock}

L'output è:

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        -1 |
+-----------------------------------------+-----------+
```
{: screen} 



## Controllo della politica di conservazione dei log di uno spazio
{: #check_retention_policy_space}

Per ottenere il periodo di conservazione impostato per uno spazio {{site.data.keyword.Bluemix_notm}}, completa la seguente procedura:

1. Accedi a {{site.data.keyword.Bluemix_notm}}. 

    Esegui il comando [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) per accedere a {{site.data.keyword.Bluemix_notm}} e poi esegui il comando [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) per configurare l'organizzazione e lo spazio in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
	
2. Ottieni il periodo di conservazione. Esegui il comando:

    ```
    ibmcloud at option
    ```
    {: codeblock}

    L'output per l'ID spazio *d35da1e3-b345-475f-8502-bx cfgh436902a3* è 30 giorni:

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## Verifica della politica di conservazione dei log per tutti gli spazi in un account
{: #check_retention_policy_account}

Per ottenere il periodo di conservazione impostato per ogni spazio {{site.data.keyword.Bluemix_notm}} in un account, completa la seguente procedura:

1. Accedi a {{site.data.keyword.Bluemix_notm}}. 

    Esegui il comando [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) per accedere a {{site.data.keyword.Bluemix_notm}} e poi esegui il comando [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) per configurare l'organizzazione e lo spazio in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
    
2. Ottieni il periodo di conservazione di ogni spazio nell'account. Esegui il comando:

    ```
    ibmcloud at option -a
    ```
    {: codeblock}
	
	dove *-a* indica che le informazioni includono tutti gli spazi nell'account.

    Ad esempio, l'output di esecuzione del comando è:

    ```
    +-----------------------------------------+-----------+
    |               SPACEID                   | RETENTION |
    +-----------------------------------------+-----------+
    | d35da1e3-b345-475f-8502-bx cfgh436902a3 |        30 |
    +-----------------------------------------+-----------+
    | fdew45e3-b345-4365-8502-bx cfghrfthy5a3 |        30 |
    +-----------------------------------------+-----------+
    ```
    {: screen}
    

## Impostazione della politica di conservazione dei log nell'account
{: #set_retention_policy_space}

Per impostare il periodo di conservazione per un account {{site.data.keyword.Bluemix_notm}}, completa la seguente procedura:

1. Accedi a {{site.data.keyword.Bluemix_notm}}. 

    Esegui il comando [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) per accedere a {{site.data.keyword.Bluemix_notm}} e poi esegui il comando [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) per configurare l'organizzazione e lo spazio in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
	
2. Imposta il periodo di conservazione. Esegui il comando:

    ```
    ibmcloud at option -r Number_of_days - a
    ```
    {: codeblock}
    
    dove 
	* *-r* è l'opzione che deve essere specificata per impostare un periodo di conservazione.
	* *Number_of_days* è un numero intero che definisce il numero di giorni in cui vuoi conservare gli eventi. 
	* *-a* indica che la richiesta si applica a tutti gli spazi nell'account.
    
    
**Esempio**
    
Ad esempio, per conservare un qualsiasi tipo di log nel tuo account solo per 15 giorni, immetti il seguente comando:

```
ibmcloud at option -r 15 -a
```
{: codeblock}

L'output elenca una voce per ogni spazio nell'account, incluse le informazioni sul periodo di conservazione:

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |        15 |
+-----------------------------------------+-----------+
| fdew45e3-b345-4365-8502-bx cfghrfthy5a3 |        15 |
+-----------------------------------------+-----------+
```
{: screen}

## Configurazione della politica di conservazione dei log di uno spazio
{: #set_retention_policy_account}

Per visualizzare il periodo di conservazione per un spazio {{site.data.keyword.Bluemix_notm}}, completa la seguente procedura:

1. Accedi a {{site.data.keyword.Bluemix_notm}}. 

    Esegui il comando [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) per accedere a {{site.data.keyword.Bluemix_notm}} e poi esegui il comando [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) per configurare l'organizzazione e lo spazio in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.
    
2. Imposta il periodo di conservazione. Esegui il comando:

    ```
    ibmcloud at option -r Number_of_days
    ```
    {: codeblock}
    
    dove 
	* *-r* è l'opzione che deve essere specificata per impostare un periodo di conservazione.
	* *Number_of_days* è un numero intero che definisce il numero di giorni in cui vuoi conservare gli eventi.
    
    
**Esempio**
    
Ad esempio, per conservare gli eventi disponibili in uno spazio per un anno, immetti il seguente comando:

```
ibmcloud at option -r 365
```
{: codeblock}

L'output è:

```
+-----------------------------------------+-----------+
|               SPACEID                   | RETENTION |
+-----------------------------------------+-----------+
| d35da1e3-b345-475f-8502-bx cfgh436902a3 |       365 |
+-----------------------------------------+-----------+
```
{: screen}


