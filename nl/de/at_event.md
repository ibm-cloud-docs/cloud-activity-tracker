---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Ereignisfelder
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse basieren auf dem CADF-Standard (CADF = Cloud Auditing Data Federation). 
{:shortdesc}

## Initiatorfelder
{: #initiator}

Die folgende Tabelle enthält eine Auflistung der allgemeinen Felder, die für ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis verfügbar sind:

| Feldname | Beschreibung | Wert |
|------------|-------------|-------|
| `initiator.id` | ID des Initiators der Aktion. </br></br>Es gibt verschiedene Typen von Initiatoren: IBMID, Service-ID und CF-Benutzer-ID (CF - Cloud Foundry). | Beispiel einer IBMid: IBMid-000000XXX2 </br>Beispiel einer Service-ID: iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14 </br>Beispiel einer CF-Benutzer-ID: 7666666b-23ae-4a34-8569-cu75tgdr4da3 |
| `initiator.name` | Benutzername des Benutzers, der die Aktion eingeleitet hat. | Beispielsweise eine E-Mail-Adresse. |
| `initiator.typeURI` | Typ der Ereignisquelle. | Gültige Werte: *service/security/account/user*, *service/security/clientid*, *service/security/account/serviceid* |
| `initiator.credential.type` | Typ des Berechtigungsnachweises für die Initiator-ID. | Gültige Werte: *user*, *token*, *apikey* |
{: caption="Tabelle 1. Allgemeine Initiatorfelder" caption-side="top"} 

  

## Zielfelder
{: #target}

Die folgende Tabelle enthält eine Auflistung der allgemeinen Zielfelder, die für ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis verfügbar sind:

| Feldname | Beschreibung | Wert |
|------------|-------------|-------|
| `target.id` | Cloudressourcenname (CRN) der Ressource, auf der die Aktion ausgeführt wird. </br>Weitere Informationen finden Sie in [CRN-Format](/docs/overview?topic=overview-format-crn#format). | Beispiel: `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1` |
| `target.name` | Lesbarer Name des Namens der Cloudressource, auf der die Aktion ausgeführt wird. |  |
| `target.typeURI` | Typ der Cloudressource, auf der die Aktion ausgeführt wird. </br>Dieses Feld hat das Format **serviceName/objectType**, wobei 'servicename' den Namen des Service angibt. | Beispiel: `iam-am/policy` oder `cloud-object-storage/bucket/acl` |
{: caption="Tabelle 2. Allgemeine Zielfelder" caption-side="top"} 


 
## Aktionsfelder
{: #action}

Die folgende Tabelle enthält eine Auflistung der allgemeinen Aktionsfelder, die für ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis verfügbar sind:

| Feldname | Beschreibung | Wert |
|------------|-------------|-------|
| `action` | Aktion, die das Ereignis auslöst. </br>Dieses Feld hat das Format **serviceName.objectType.action**, wobei 'servicename' den Namen des Service angibt. </br>Weitere Informationen zu Aktionswerten für Ereignisse, die von einem Service generiert werden, finden Sie in <a href="/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services">Cloud-Services</a>. | Beispiel: *iam-identity.serviceid-apikey.login* |
| `eventTime` | Gibt anhand einer Zeitmarke an, wann das Ereignis erstellt wurde. </br>Das Datum wird in koordinierter Weltzeit (UTC - Universal Time Coordinated) dargestellt. </br>Das Format entspricht ISO 8601. | Beispiel: 2017-10-19T19:07:50.32+0000 |
{: caption="Tabelle 3. Allgemeine Aktionsfelder" caption-side="top"} 



## Ergebnisfelder
{: #outcomes}

Die folgende Tabelle enthält eine Auflistung der allgemeinen Ergebnisfelder, die für ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis verfügbar sind:

| Feldname | Beschreibung | Wert |
|------------|-------------|-------|
| `outcome` | Ergebnis der Aktion. | Gültige Werte: *success*, *failure*, *pending* |
| `reason.reasonCode` | Numerisches Feld, das den HTTP-Antwortcode enthält. | Beispiel: *200* für ein erfolgreiches Ergebnis |
| `severity` | Definiert das Sicherheitsrisiko, das eine Aktion für die Cloud darstellen könnte. | Gültige Werte: *normal* (Normal), *warning* (Warnung), *critical* (Kritisch) </br></br>**Normal** ist für Routineaktionen in der Cloud festgelegt. Beispiel: Starten einer Instanz, Neuanzeigen eines Tokens </br></br>**Warning** ist für Aktionen festgelegt, bei denen eine Cloudressource aktualisiert wird oder Änderungen an ihren Metadaten vorgenommen werden. Beispiel: Aktualisieren der Version eines Workerknotens, Umbenennen eines Zertifikats, Umbenennen einer Serviceinstanz </br></br>**Critical** ist für Aktionen festgelegt, die sich auf die Sicherheit in der Cloud auswirken. Beispiel: Ändern der Berechtigungsnachweise für einen Benutzer, Löschen von Daten, unbefugter Zugriff zum Arbeiten mit einer Cloud-Ressource |
{: caption="Tabelle 4. Allgemeine Ergebnisfelder" caption-side="top"} 


