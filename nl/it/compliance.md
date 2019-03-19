---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Conformità
{: #compliance}

[ {{site.data.keyword.Bluemix}} fornisce una piattaforma cloud e i servizi creati con gli standard di sicurezza più rigorosi di IBM.](/docs/security/compliance.html#compliance). Il servizio {{site.data.keyword.cloudaccesstraillong}} è un servizio DevOps creato per {{site.data.keyword.cloud_notm}}. 
{:shortdesc}


## Regolamento generale sulla protezione dei dati (GDPR)

Il regolamento generale sulla protezione dei dati (GDPR) cerca di creare un quadro giuridico di protezione dei dati armonizzato nella UE e ha lo scopo di ridare ai cittadini il controllo dei propri dati personali, mentre impone regole rigorose a chi ospita e ‘elabora’ questi dati, ovunque nel mondo. Il Regolamento introduce anche regole inerenti la libera circolazione di dati personali all'interno e all'esterno dell'UE. 

**Dichiarazione:** il servizio {{site.data.keyword.cloudaccesstrailshort}} archivia e visualizza i record di eventi dalle risorse cloud in esecuzione nel tuo account in {{site.data.keyword.cloud_notm}}. Le informazioni personali (PI) non devono essere incluse nelle voci di evento archiviate in {{site.data.keyword.cloudaccesstrailshort}} poiché questi dati sono accessibili ad altri utenti nella tua azienda, nonché a {{site.data.keyword.IBM_notm}} per poter abilitare il supporto del servizio cloud.

### Regioni
{: #compliance_regions}

Il servizio {{site.data.keyword.cloudaccesstrailshort}} è conforme a GDPR nelle regioni {{site.data.keyword.cloud_notm}} pubblico in cui è disponibile il servizio.


### Conservazione di dati
{: #compliance_data_retention}

Il servizio {{site.data.keyword.cloudaccesstrailshort}} include 2 repository dei dati in cui vengono archiviati i tuoi dati dell'evento: 

* Un repository in cui i dati dell'evento sono disponibili per le analisi tramite Kibana. Solo il piano lite o standard archivia i dati in questo repository. I dati sono conservati per 3 giorni.
* Un repository di archiviazione a lungo termine che ospita i dati dell'evento per il piano premium. I dati evento vengono archiviati fino a quando non configuri una politica di conservazione o li elimini manualmente. Per impostazione predefinita, gli eventi vengono conservati indefinitamente.


### Eliminazione dei dati
{: #compliance_data_deletion}

Tieni conto delle seguenti informazioni:

* Gli eventi che vengono archiviati nel repository che fornisce i dati a Kibana vengono eliminati dopo 3 giorni.

* Gli eventi che vengono archiviati nel repository a lungo termine vengono eliminati dopo alcuni giorni quando configuri una politica di conservazione o quando li elimini manualmente. 



Se passi da un piano a pagamento a un piano standard o lite, gli eventi che si trovano nel repository di archiviazione a lungo termine verranno eliminati in circa un giorno.

In qualsiasi momento, puoi aprire un ticket di supporto e richiedere che tutti i tuoi dati vengano eliminati. Per informazioni sull'apertura di un ticket di supporto IBM, consulta [Come contattare il supporto](/docs/get-support/howtogetsupport.html#getting-customer-support).



### Ulteriori informazioni
{: #compliance_info}

Per ulteriori informazioni, consulta:

[Conformità di sicurezza di {{site.data.keyword.cloud_notm}} ](/docs/security/compliance.html#compliance)

[GDPR - pagina ufficiale {{site.data.keyword.IBM_notm}}](https://www.ibm.com/data-responsibility/gdpr/)



