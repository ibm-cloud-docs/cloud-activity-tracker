---

copyright:
  years: 2016, 2018
lastupdated: "2018-07-07"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# Activity Tracker-Ereignisfelder
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse basieren auf dem CADF-Standard (CADF = Cloud Auditing Data Federation). 
{:shortdesc}

## Initiatorfelder
{: #initiator}

Die folgende Tabelle enthält eine Auflistung der allgemeinen Felder, die für ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis verfügbar sind:

<table>
  <caption>Allgemeine Initiatorfelder</caption>
  <tr>
    <th>Feldname</th>
	  <th>Beschreibung</th>
    <th>Wert</th>
  </tr>
  <tr>
    <td>initiator.id</td>
	  <td>ID des Initiators der Aktion. </br>Es gibt zwei Typen von Initiator: IBMid und Service-ID.</td>
    <td>Beispiel einer IBMid: IBMid-000000XXX2 </br>Beispiel einer Service-ID: iam-ServiceId-12345678-0165-4c89-847d-9660b1632e14</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	  <td>Benutzername des Benutzers, der die Aktion eingeleitet hat.</td>
    <td></td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	  <td>Typ der Ereignisquelle.</td>
    <td>Gültige Werte: *service/security/account/user*, *service/security/clientid*, *service/security/account/serviceid*</td>
  </tr>
  <tr>
    <td>initiator.credential.type</td>
	  <td>Typ des Berechtigungsnachweises für die Initiator-ID. </td>
    <td>Gültige Werte: *user*, *token*, *apikey*</td>
  </tr>
</table>

## Zielfelder
{: #target}

Die folgende Tabelle enthält eine Auflistung der allgemeinen Zielfelder, die für ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis verfügbar sind:

<table>
  <caption>Allgemeine Zielfelder</caption>
  <tr>
    <th>Feldname</th>
	  <th>Beschreibung</th>
    <th>Wert</th>
  </tr>
  <tr>
    <td>target.id</td>
	  <td>Cloudressourcenname (CRN) der Ressource, auf der die Aktion ausgeführt wird. </br>Weitere Informationen finden Sie in [CRN-Format](/docs/overview/crn.html#format).</td>
    <td>Beispiel: `crn:v1:bluemix:public:cloud-object-storage:global:a/12345678e6232019c6567c9123456789:fr56et47-befb-440a-a223c-12345678dae1:bucket:bucket1`</td>
  </tr>
  <tr>
    <td>target.name</td>
	  <td>Lesbarer Name des Namens der Cloudressource, auf der die Aktion ausgeführt wird.</td>
    <td></td>
  </tr>
  <tr>
    <td>target.typeURI</td>
    <td>Typ der Cloudressource, auf der die Aktion ausgeführt wird. </br>Dieses Feld hat das Format **serviceName/objectType**, wobei 'servicename' den Namen des Service angibt. </td>
	  <td>Beispiel: `iam-am/policy` oder `cloud-object-storage/bucket/acl`</td>
  </tr>
</table>
 
## Aktionsfelder
{: #action}

Die folgende Tabelle enthält eine Auflistung der allgemeinen Aktionsfelder, die für ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis verfügbar sind:

<table>
  <caption>Allgemeine Aktionsfelder</caption>
  <tr>
    <th>Feldname</th>
	  <th>Beschreibung</th>
    <th>Wert</th>
  </tr>
  <tr>
    <td>action</td>
	  <td>Aktion, die das Ereignis auslöst. </br>Dieses Feld hat das Format **serviceName.objectType.action**, wobei 'servicename' den Namen des Service angibt. </br>Informationen zu Ereignissen, die durch einen Service generiert werden, finden Sie in <a href="/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services">Cloud-Services</a>.</td>
    <td>Beispiel: *iam-identity.serviceid-apikey.login*</td>
  </tr>
  <tr>
    <td>eventTime</td>
	  <td>Gibt anhand einer Zeitmarke an, wann das Ereignis erstellt wurde. </br>Das Datum wird in koordinierter Weltzeit (UTC - Universal Time Coordinated) dargestellt. </br>Das Format entspricht ISO 8601.</td>
    <td>Beispiel: 2017-10-19T19:07:50.32+0000<td>
  </tr>
</table>

## Ergebnisfelder
{: #outcomes}

Die folgende Tabelle enthält eine Auflistung der allgemeinen Ergebnisfelder, die für ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis verfügbar sind:

<table>
  <caption>Allgemeine Ergebnisfelder</caption>
  <tr>
    <th>Feldname</th>
	  <th>Beschreibung</th>
    <th>Wert</th>
  </tr>
  <tr>
    <td>outcome</td>
	  <td>Ergebnis der Aktion. </td>
    <td>Gültige Werte: *success* (Erfolgreich), *failure* (Fehler), *pending* (Anstehend)</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	  <td>Numerisches Feld, das den HTTP-Antwortcode enthält. </td>
    <td>Beispiel: *200* für ein erfolgreiches Ergebnis </td>
  </tr>
  <tr>
    <td>severity</td>
	  <td>Definiert das Sicherheitsrisiko, das eine Aktion für die Cloud darstellen könnte. </td>
    <td>Gültige Werte: *normal* (Normal), *warning* (Warnung), *critical* (Kritisch) </br></br>**Normal** ist für Routineaktionen in der Cloud festgelegt. Beispiel: Starten einer Instanz, Neuanzeigen eines Tokens </br></br>**Warning** ist für Aktionen festgelegt, bei denen eine Cloudressource aktualisiert wird oder Änderungen an ihren Metadaten vorgenommen werden. Beispiel: Aktualisieren der Version eines Workerknotens, Umbenennen eines Zertifikats, Umbenennen einer Serviceinstanz </br></br>**Critical** ist für Aktionen festgelegt, die sich auf die Sicherheit in der Cloud auswirken. Beispiel: Ändern der Berechtigungsnachweise für einen Benutzer, Löschen von Daten, unbefugter Zugriff zum Arbeiten mit einer Cloud-Ressource </td>
  </tr>
</table>
