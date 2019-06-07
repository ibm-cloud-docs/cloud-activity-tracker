---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, resource controller events

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

# Serviceinstanzereignisse  
{: #at_events_rc}

Als Sicherheitsbeauftragter, Prüfer oder Manager können Sie den {{site.data.keyword.cloudaccesstrailfull}}-Service verwenden, um zu verfolgen, wie Benutzer und Anwendungen mit den {{site.data.keyword.Bluemix}}-Services interagieren. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} wird nicht mehr verwendet. Ab 09. Mai 2019 können keine neuen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen mehr bereitgestellt werden. Vorhandene Instanzen des Premium-Plans werden bis 30. September 2019 unterstützt. Wenn Sie die Aktivitäten Ihres {{site.data.keyword.cloud_notm}}-Kontos weiterhin verfolgen möchten, stellen Sie eine Instanz von [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) bereit.
{: deprecated}

Der {{site.data.keyword.cloudaccesstrailfull_notm}}-Service zeichnet vom Benutzer eingeleitete Aktivitäten auf, die den Status eines Service in der {{site.data.keyword.cloud_notm}} ändern. Weitere Informationen finden Sie in [Informationen zu {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

Informationen zum Einstieg in die Überwachung der Aktionen Ihrer Benutzer finden Sie in [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started-with-cla#getting-started-with-cla). 


## Ereignisse beim Bereitstellen und Verwalten von Serviceinstanzen
{: #at_events_rc_provision}

In der folgenden Tabelle sind die API-Methoden aufgeführt, bei deren Aufruf ein Ereignis generiert wird:

<table>
  <caption>Aktionen, die Ereignisse generieren</caption>
  <tr>
    <th>Aktion</th>
	  <th>Beschreibung</th>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.create</td>
	  <td>Es wird ein Ereignis generiert, wenn Sie eine Serviceinstanz bereitstellen.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.update</td>
	  <td>Es wird ein Ereignis generiert, wenn Sie eine Serviceinstanz umbenennen oder wenn Sie den Serviceplan ändern.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.instance.delete</td>
	  <td>Es wird ein Ereignis generiert, wenn eine Serviceinstanz gelöscht wird.</td>
  </tr>
</table>


##  Ereignisse beim Verwalten von API-Schlüsseln, die einer Serviceinstanz zugeordnet sind
{: #at_events_rc_keys}

In der folgenden Tabelle sind die API-Methoden aufgeführt, bei deren Aufruf ein Ereignis generiert wird:

<table>
  <caption>Aktionen, die Ereignisse generieren</caption>
  <tr>
    <th>Aktion</th>
	  <th>Beschreibung</th>
  </tr>
  <tr>
    <td><i>service_name</i>.key.create</td>
	  <td>Es wird ein Ereignis generiert, wenn für eine Serviceinstanz ein API-Schlüssel über den Abschnitt *Serviceberechtigungsnachweise* in der Benutzerschnittstelle (UI) der Serviceinstanz erstellt wird.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.key.delete</td>
	  <td>Es wird ein Ereignis generiert, wenn ein API-Schlüssel, der einer Serviceinstanz zugeordnet ist, aus dem Abschnitt *Serviceberechtigungsnachweise* in der Benutzerschnittstelle (UI) der Serviceinstanz gelöscht wird.</td>
  </tr>
</table>

##  Ereignisse beim Binden einer Serviceinstanz an eine App
{: #at_events_rc_bind}

In der folgenden Tabelle sind die API-Methoden aufgeführt, bei deren Aufruf ein Ereignis generiert wird:

<table>
  <caption>Aktionen, die Ereignisse generieren</caption>
  <tr>
    <th>Aktion</th>
	  <th>Beschreibung</th>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.create</td>
	  <td>Es wird ein Ereignis generiert, wenn Sie einen Serviceinstanz an eine Anwendung binden.</td>
  </tr>
  <tr>
    <td><i>service_name</i>.binding.delete</td>
	  <td>Es wird ein Ereignis generiert, wenn Sie die Bindung einer Serviceinstanz an eine Anwendung aufheben.</td>
  </tr>
</table>




## Wo Sie die Ereignisse finden
{: #at_events_rc_ui}

Sie finden {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse sind in der **Kontodomäne** der Region **'Süden' der Vereinigten Staaten** (us-south) verfügbar.

Um diese Ereignisse anzeigen zu können, müssen Sie eine Instanz des {{site.data.keyword.cloudaccesstrailshort}}-Service in der Region **'Süden' der Vereinigten Staaten** ('us-south') bereitstellen. Danach müssen Sie die Benutzerschnittstelle (UI) für {{site.data.keyword.cloudaccesstrailshort}} öffnen und zu der Kontodomäne wechseln, um Ereignisse zu sehen. 

Weitere Informationen finden Sie in [Ereignisse für ein Konto anzeigen](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events).



