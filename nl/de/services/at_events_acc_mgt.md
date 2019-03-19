---

copyright:
  years: 2016, 2019
lastupdated: "2019-01-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Kontoverwaltungsereignisse  
{: #at_events_acc_mgt}

Als Sicherheitsbeauftragter, Prüfer oder Manager können Sie den {{site.data.keyword.cloudaccesstrailfull}}-Service verwenden, um zu verfolgen, wie Benutzer und Anwendungen mit dem {{site.data.keyword.Bluemix}}-Konto interagieren. 
{:shortdesc}

Der {{site.data.keyword.cloudaccesstrailfull_notm}}-Service zeichnet vom Benutzer eingeleitete Aktivitäten auf, die den Status eines Service in der {{site.data.keyword.cloud_notm}} ändern. Weitere Informationen finden Sie in [Informationen zu {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov ).

Informationen zum Einstieg in die Überwachung der Aktionen Ihrer Benutzer finden Sie in [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla). 



## Ereignisse beim Verwalten von Konten
{: #at_events_acc_mgt_account}

In der folgenden Tabelle sind die API-Methoden aufgeführt, die ein Ereignis generieren, wenn sie aufgerufen werden:

<table>
  <caption>Aktionen, die Ereignisse generieren</caption>
  <tr>
    <th>Aktion</th>
	  <th>Beschreibung</th>
  </tr>
  <tr>
    <td>billing.account.create</td>
	  <td>Es wird ein Ereignis generiert, wenn Sie ein Konto bereitstellen, nachdem die Konto-ID zum Konto zugewiesen wurde.</td>
  </tr>
  <tr>
    <td>billing.account.update</td>
	  <td>Es wird ein Ereignis generiert, wenn Sie Informationen zu dem Konto aktualisieren.</td>
  </tr>
  <tr>
    <td>billing.account.active</td>
	  <td>Es wird ein Ereignis generiert, wenn Sie das Konto überprüfen, d. h. es wird ein Ereignis generiert, wenn das Konto aktiv wird.</td>
  </tr>
  <tr>
    <td>billing.account.subscription.create</td>
	  <td>Es wird ein Ereignis generiert, wenn Sie ein <a href="/docs/account/index.html#subscription-account">Abonnementkonto</a> erstellen.</td>
  </tr>
</table>



## Ereignisse beim Verwalten von Benutzern
{: #at_events_acc_mgt_users}

In der folgenden Tabelle sind die API-Methoden aufgeführt, die ein Ereignis generieren, wenn sie aufgerufen werden:

<table>
  <caption>Aktionen, die Ereignisse generieren</caption>
  <tr>
    <th>Aktion</th>
	  <th>Beschreibung</th>
  </tr>
  <tr>
    <td>user-management.user.create</td>
	  <td>Es wird ein Ereignis generiert, wenn Sie einem Benutzer eine Einladung schicken, um einem Konto beizutreten. </br>Der Kontoeigner kann als einzige Person des Kontos diese Aktion ausführen.</td>
  </tr>
  <tr>
    <td>user-management.user.active</td>
	  <td>Es wird ein Ereignis generiert, wenn Sie den Benutzer im Konto aktivieren. </br>Wenn der Benutzer seine E-Mail-Adresse bestätigt, wird das Ereignis generiert.</td>
  </tr>
  <tr>
    <td>user-management.account.user.delete</td>
	  <td>Es wird ein Ereignis generiert, wenn Sie einen Benutzer aus dem Konto entfernen. </br>Der Kontoeigner kann als einzige Person des Kontos diese Aktion ausführen.</td>
  </tr>
</table>

## Ereignisse beim Verwalten von Organisationen
{: #at_events_acc_mgt_org}

In der folgenden Tabelle sind die API-Methoden aufgeführt, die ein Ereignis generieren, wenn sie aufgerufen werden:

<table>
  <caption>Aktion, die Ereignisse generiert</caption>
  <tr>
    <th>Aktion</th>
	  <th>Beschreibung</th>
  </tr>
  <tr>
    <td>billing.account.org.create</td>
	  <td>Es wird ein Ereignis generiert, wenn Sie eine Organisation zu dem Konto hinzufügen.</td>
  </tr>
</table>

## Wo Sie die Ereignisse finden
{: #at_events_acc_mgt_ui}

Sie finden {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse sind in der **Kontodomäne** der Region **'Süden' der Vereinigten Staaten** (us-south) verfügbar. Weitere Informationen finden Sie in [Ereignisse für ein Konto anzeigen](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events).

Um diese Ereignisse anzeigen zu können, müssen Sie eine Instanz des {{site.data.keyword.cloudaccesstrailshort}}-Service in der Region **'Süden' der Vereinigten Staaten** ('us-south') bereitstellen. Danach müssen Sie die Benutzerschnittstelle (UI) für {{site.data.keyword.cloudaccesstrailshort}} öffnen und zu der Kontodomäne wechseln, um Ereignisse zu sehen. Weitere Informationen finden Sie in [Ereignisse für ein Konto anzeigen](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/viewing_events.html#view_acc_events_account_events). 








