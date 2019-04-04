---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, Cloud Foundry events, CF

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


# Cloud Foundry-Ereignisse
{: #cf}

Verwenden Sie den {{site.data.keyword.cloudaccesstrailfull}}-Service, um die Interaktion mit zentralen Services der Plattform in der {{site.data.keyword.Bluemix}} zu verfolgen. 
{:shortdesc}


Die folgende Liste liefert einen Abriss der wichtigsten Plattformtasks, die Ereignisse an den {{site.data.keyword.cloudaccesstrailshort}}-Service senden: 

* Bereitstellen eines Service, Entfernen eines Service und Ändern des Namens eines Service.
* Erteilen, Aktualisieren und Entziehen von Cloud Foundry-Bereichsrollen für Benutzer in dem Konto.
* Erstellen eines Plattform-API-Schlüssels, Umbenennen eines Plattformschlüssels und Löschen eines Plattformschlüssels.


## Bei der Interaktion mit Katalogservices generierte Ereignisse
{: #cf_catalog}

Wenn Sie einen Service bereitstellen, einen Service entfernen oder den Namen eines Service ändern, wird ein Ereignis generiert und an diejenige Bereichsdomäne in {{site.data.keyword.cloudaccesstrailshort}} gesendet, die dem Cloud Foundry-Bereich zugeordnet ist, in dem der Service im Konto verfügbar ist. 

Beispiel: Sie stellen Service A im Bereich (Space) B in der Region 'Vereinigte Staaten (Süden)' bereit. Ein Ereignis wird generiert. Damit Sie das Ereignis sehen können, müssen Sie den {{site.data.keyword.cloudaccesstrailshort}} in der Region 'Vereinigte Staaten (Süden)' bereitstellen, und zwar in demselben Bereich, in dem Sie den Service bereitgestellt haben. Anschließend können Sie das Ereignis über die Benutzerschnittstelle (UI) des {{site.data.keyword.cloudaccesstrailshort}}-Service anzeigen.

Die folgende Tabelle enthält eine Auflistung der Katalogaktionen, die Ereignisse generieren:

<table>
  <caption>Katalogaktionen</caption>
  <tr>
    <th>Aktion</th>
	  <th>Beschreibung</th>
  <tr>
  <tr>
    <td>`audit.service_instance.create`</td>
	<td>Ein Ereignis wird erstellt, wenn Sie einen Service in einem Cloud Foundry-Bereich bereitstellen.</td>
  </tr>
  <tr>
    <td>`audit.service_instance.update`</td>
	<td>Ein Ereignis wird erstellt, wenn Sie den Namen eines Service ändern, der in einem Cloud Foundry-Bereich verfügbar ist.</td>
  </tr>
  <tr>
    <td>`audit.service_instance.delete`</td>
	<td>Ein Ereignis wird erstellt, wenn Sie einen Service aus einem Cloud Foundry-Bereich in dem Konto entfernen.</td>
  </tr>
</table>


 	

## Bei der Verwaltung von Cloud Foundry-Rollen in einem Konto generierte Ereignisse
{: #cf_cfroles} 

Wenn Sie für einen Benutzer im Konto eine Cloud Foundry-Rolle erteilen oder entziehen (löschen), wird ein Ereignis generiert und an diejenige Bereichsdomäne in {{site.data.keyword.cloudaccesstrailshort}} gesendet, die dem Cloud Foundry-Bereich zugeordnet ist, in dem die Rolle erteilt oder entzogen wird. 

Beispiel: Sie erteilen Benutzer A im Bereich B in der Region 'Vereinigte Staaten (Süden)' die Rolle *Bereichsmanager*. Ein Ereignis wird generiert. Damit Sie das Ereignis sehen können, müssen Sie den {{site.data.keyword.cloudaccesstrailshort}} in der Region 'Vereinigte Staaten (Süden)' bereitstellen, und zwar in demselben Bereich, in dem Sie die CF-Berechtigungen für den Benutzer verwalten. Anschließend können Sie das Ereignis über die Benutzerschnittstelle (UI) des {{site.data.keyword.cloudaccesstrailshort}}-Service anzeigen.


Die folgende Tabelle enthält eine Auflistung der Aktionen, durch die {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse generiert werden, wenn Sie die Cloud Foundry-Rollen eines Benutzers verwalten:

<table>
  <caption>Aktionen für die Verwaltung von Cloud Foundry-Rollen</caption>
  <tr>
    <th>Aktion</th>
	<th>Beschreibung</th>
  <tr>
  <tr>
    <td>`audit.user.space_manager_add`</td>
	<td>Einem Benutzer die Rolle *Manager* in einem Cloud Foundry-Bereich erteilen.</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_add`</td>
	<td>Einem Benutzer die Rolle *Entwickler* in einem Cloud Foundry-Bereich erteilen.</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_add`</td>
	<td>Einem Benutzer die Rolle *Auditor* in einem Cloud Foundry-Bereich erteilen.</td>
  </tr>
  <tr>
    <td>`audit.user.space_manager_remove`</td>
	<td>Die Rolle *Manager* des Benutzers in einem Cloud Foundry-Bereich löschen.</td>
  </tr>
  <tr>
    <td>`audit.user.space_developer_remove`</td>
	<td>Die Rolle *Entwickler* des Benutzers in einem Cloud Foundry-Bereich löschen.</td>
  </tr>
  <tr>
    <td>`audit.user.space_auditor_remove`</td>
	<td>Die Rolle *Auditor* des Benutzers in einem Cloud Foundry-Bereich löschen.</td>
  </tr>
</table>






	
 	
 	
