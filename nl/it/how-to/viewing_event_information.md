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


# Visualizzazione di informazioni sull'evento
{: #viewing_event_status}

Utilizza il comando `ibmcloud at status` per ottenere le informazioni sugli eventi raccolti e archiviati in {{site.data.keyword.cloudaccesstrailshort}} per uno spazio {{site.data.keyword.Bluemix}}.
{:shortdesc}

Puoi ottenere le informazioni sulla dimensione del log di eventi teh, il numero di record e se gli eventi sono disponibili o meno per l'analisi in Kibana.  

Completa la seguente procedura per visualizzare le informazioni sul log degli eventi:

## Passo 1: Accedi a {{site.data.keyword.Bluemix_notm}}
{: #prereq}

Accedi a {{site.data.keyword.Bluemix_notm}}. Completa la seguente
procedura:

1. Esegui il comando [ibmcloud login](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login) per accedere a {{site.data.keyword.Bluemix_notm}}.
2. Esegui il comando [ibmcloud target](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target) per impostare l'organizzazione e lo spazio in cui vuoi eseguire il provisioning del servizio {{site.data.keyword.cloudaccesstrailshort}}.

**Nota:** imposta l'organizzazione e lo spazio in cui viene eseguito il provisioning di {{site.data.keyword.cloudaccesstrailshort}}.

## Passo 2: Identifica quali eventi sono disponibili
{: #step2}

Utilizza il comando `ibmcloud at status` per visualizzare le informazioni sugli eventi disponibili in un dominio dello spazio.

* Per ottenere le informazioni sugli eventi in un dominio dello spazio, esegui il comando `ibmcloud at status`.
* Per ottenere le informazioni sugli eventi nel dominio dell'account, esegui il comando `ibmcloud at status` con l'opzione `-a`.

```
$ ibmcloud at status -a -s YYYY-MM-DD -e YYYY-MM-DD 
```
{: codeblock}
    
dove
    
* *-a* viene utilizzato per specificare che la richiesta venga applicata al dominio dell'account.
* *-s* viene utilizzato per impostare la data di inizio in UTC (Universal Coordinated Time): *YYYY-MM-DD*.
* *-e* viene utilizzato per impostare la data di fine in UTC (Universal Coordinated Time): *YYYY-MM-DD*.

Ad esempio, per visualizzare quali eventi sono disponibili per le ultime 2 settimane in un dominio dello spazio, immetti il seguente comando:

```
$ ibmcloud at status
```
{: codeblock}
    
Ad esempio, l'output di esecuzione di questo comando è:
    
```
+------------+--------+------------+
|    DATE    |  COUNT | SEARCHABLE |
+------------+--------+------------+
| 2017-07-24 |    16  |    None    |
+------------+--------+------------+
| 2017-07-25 |   1224 |    All     |
+------------+--------+------------+
```
{: screen}

**Nota:** il servizio {{site.data.keyword.cloudaccesstrailshort}} è un servizio globale che utilizza UTC (Coordinated Universal Time). I giorni sono definiti come giorni UTC. Per ottenere gli eventi per un giorno con ora locale specifico, potresti dover scaricare più giorni UTC.
	














