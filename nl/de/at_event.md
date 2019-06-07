---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, event fields

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



# Ereignisfelder
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse basieren auf dem CADF-Standard (CADF = Cloud Auditing Data Federation). 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} wird nicht mehr verwendet. Ab 09. Mai 2019 können keine neuen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen mehr bereitgestellt werden. Vorhandene Instanzen des Premium-Plans werden bis 30. September 2019 unterstützt. Wenn Sie die Aktivitäten Ihres {{site.data.keyword.cloud_notm}}-Kontos weiterhin verfolgen möchten, stellen Sie eine Instanz von [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) bereit.
{: deprecated}

## Initiatorfelder
{: #initiator}

Die folgende Tabelle enthält eine Auflistung der allgemeinen Felder, die für ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis verfügbar sind:

| Feldname | Beschreibung | Wert |
|------------|-------------|-------|
| `initiator.id` | ID des Initiators der Aktion. </br></br>Gültige Typen von Initiatoren sind `IBMID`, `Service-ID` und `CF-Benutzer-ID (CF - Cloud Foundry)`. | Beispiel einer IBMid: `IBMid-000000XXX2` </br>Beispiel einer Service-ID: `iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14` </br>Beispiel einer CF-Benutzer-ID: `7666666b-23ae-4a34-8569-cu75tgdr4da3` |
| `initiator.name` | Benutzername des Benutzers, der die Aktion eingeleitet hat. | Beispielsweise eine E-Mail-Adresse. |
| `initiator.typeURI` | Typ der Ereignisquelle. | Gültige Werte sind *service/security/account/user*, *service/security/clientid* und *service/security/account/serviceid*. |
| `initiator.credential.type` | Typ des Berechtigungsnachweises für die Initiator-ID. | Gültige Werte sind *user*, *token* und *apikey*. |
{: caption="Tabelle 1. Allgemeine Initiatorfelder" caption-side="top"} 

  

## Zielfelder
{: #target}

Die folgende Tabelle enthält eine Auflistung der allgemeinen Zielfelder, die für ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis verfügbar sind:

| Feldname | Beschreibung | Wert |
|------------|-------------|-------|
| `target.id` | Cloudressourcenname (CRN) der Ressource, auf der die Aktion ausgeführt wird. </br>Weitere Informationen finden Sie in [CRN-Format](/docs/overview?topic=overview-crn#format-crn). | Beispiel: `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1` |
| `target.name` | Lesbarer Name der Cloudressource, auf der die Aktion ausgeführt wird. |  |
| `target.typeURI` | Typ der Cloudressource, auf der die Aktion ausgeführt wird. </br>Dieses Feld hat das Format **serviceName/objectType**, wobei `serviceName` der Name des Service ist. | Beispiel: `iam-am/policy` oder `cloud-object-storage/bucket/acl` |
{: caption="Tabelle 2. Allgemeine Zielfelder" caption-side="top"} 


 
## Aktionsfelder
{: #action}

Die folgende Tabelle enthält eine Auflistung der allgemeinen Aktionsfelder, die für ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis verfügbar sind:

| Feldname | Beschreibung | Wert |
|------------|-------------|-------|
| `action` | Aktion, die das Ereignis auslöst. </br>Dieses Feld hat das Format **serviceName.objectType.action**, wobei `serviceName` der Name des Service ist. </br>Weitere Informationen zu Aktionswerten für Ereignisse, die von einem Service generiert werden, finden Sie in <a href="/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-cloud_services#cloud_services">Cloud-Services</a>. | Beispiel: `iam-identity.serviceid-apikey.login` |
| `eventTime` | Gibt anhand einer Zeitmarke an, wann das Ereignis erstellt wurde. </br>Das Datum wird in koordinierter Weltzeit (UTC - Coordinated Universal Time) dargestellt. </br>Das Format entspricht ISO 8601. | Beispiel: `2017-10-19T19:07:50.32+0000` |
{: caption="Tabelle 3. Allgemeine Aktionsfelder" caption-side="top"} 



## Ergebnisfelder
{: #outcomes}

Die folgende Tabelle enthält eine Auflistung der allgemeinen Ergebnisfelder, die für ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis verfügbar sind:

| Feldname | Beschreibung | Wert |
|------------|-------------|-------|
| `outcome` | Ergebnis der Aktion. | Gültige Werte sind *success*, *failure* und *pending*. |
| `reason.reasonCode` | Numerisches Feld, das den HTTP-Antwortcode enthält. | Beispiel: *200* für ein erfolgreiches Ergebnis |
| `severity` | Definiert das Sicherheitsrisiko, das eine Aktion für die Cloud darstellen könnte. | Gültige Werte sind *normal*, *warning* und *critical*. </br></br>**Normal** ist für Routineaktionen in der Cloud festgelegt. Beispiele: Eine Instanz starten oder ein Token aktualisieren. </br></br>**Warning** ist für Aktionen festgelegt, bei denen eine Cloudressource aktualisiert wird oder Änderungen an ihren Metadaten vorgenommen werden. Beispiele: Die Version eines Workerknotens aktualisieren, ein Zertifikat umbenennen oder eine Serviceinstanz umbenennen. </br></br>**Critical** ist für Aktionen festgelegt, die sich auf die Sicherheit in der Cloud auswirken. Beispiele: Berechtigungsnachweise eines Benutzers ändern, Daten löschen, unbefugter Zugriff für das Arbeiten mit einer Cloudressource. |
{: caption="Tabelle 4. Allgemeine Ergebnisfelder" caption-side="top"} 


