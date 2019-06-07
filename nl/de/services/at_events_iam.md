---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, IAM events

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


# IAM-Ereignisse
{: #at_events_iam}

Als Sicherheitsbeauftragter, Prüfer oder Manager können Sie den {{site.data.keyword.cloudaccesstrailfull}}-Service verwenden, um zu verfolgen, wie Benutzer und Anwendungen mit dem {{site.data.keyword.iamlong}}-Service (IAM-Service) in {{site.data.keyword.Bluemix}} interagieren. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} wird nicht mehr verwendet. Ab 09. Mai 2019 können keine neuen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen mehr bereitgestellt werden. Vorhandene Instanzen des Premium-Plans werden bis 30. September 2019 unterstützt. Wenn Sie die Aktivitäten Ihres {{site.data.keyword.cloud_notm}}-Kontos weiterhin verfolgen möchten, stellen Sie eine Instanz von [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) bereit.
{: deprecated}

Der {{site.data.keyword.cloudaccesstrailfull_notm}}-Service zeichnet vom Benutzer eingeleitete Aktivitäten auf, die den Status eines Service in der {{site.data.keyword.cloud_notm}} ändern. Weitere Informationen finden Sie in [Informationen zu {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).

Informationen zum Einstieg in die Überwachung der Aktionen Ihrer Benutzer finden Sie in [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started). 

Ein Initiator kann ein Benutzer, ein Service oder eine Anwendung sein.
{: tip}

## Ereignisse für Zugriffsgruppen verwalten
{: #at_events_iam_access}

In der folgenden Tabelle sind die Aktionen aufgelistet, die ein Ereignis generieren:

| Aktion | Beschreibung |
|----------|---------|
| `iam-groups.group.create`   | Es wird ein Ereignis generiert, wenn ein Initiator eine Zugriffsgruppe erstellt. | 
| `iam-groups.group.read`     | Es wird ein Ereignis generiert, wenn ein Initiator Informationen anzeigt, die sich auf Zugriffsgruppen beziehen. |
| `iam-groups.group.update`   | Es wird ein Ereignis generiert, wenn ein Initiator den Namen oder die Beschreibung einer Gruppe aktualisiert. |
| `iam-groups.group.delete`   | Es wird ein Ereignis generiert, wenn ein Initiator eine Zugriffsgruppe löscht. |
| `iam-groups.member.add`     | Es wird ein Ereignis generiert, wenn ein Initiator ein Mitglied zu einer Zugriffsgruppe hinzufügt. |
| `iam-groups.member.delete`  | Es wird ein Ereignis generiert, wenn ein Initiator ein Mitglied aus einer Zugriffsgruppe entfernt. |
| `iam-groups.member.read`    | Es wird ein Ereignis generiert, wenn ein Initiator die Mitgliedschaft eines Mitglieds prüft. |
| `iam-groups.rule.read`      | Es wird ein Ereignis generiert, wenn ein Initiator eine Regel in einer Zugriffsgruppe anzeigt. |
| `iam-groups.rule.create`    | Es wird ein Ereignis generiert, wenn ein Initiator eine Regel zu einer Zugriffsgruppe hinzufügt. |
| `iam-groups.rule.update`    | Es wird ein Ereignis generiert, wenn ein Initiator den Regelnamen ändert. |
| `iam-groups.rule.delete`    | Es wird ein Ereignis generiert, wenn ein Initiator eine Regel aus einer Zugriffsgruppe löscht. |
{: caption="Tabelle 1. Aktionen beim Verwalten von Zugriffsgruppen" caption-side="top"} 



## Mit Ereignissen für Service-IDs arbeiten
{: #at_events_iam_serviceids}

In der folgenden Tabelle sind die Aktionen aufgelistet, die ein Ereignis generieren:

| Aktion | Beschreibung |
|----------|---------|
| `iam-identity.account-serviceid.create` | Es wird ein Ereignis generiert, wenn ein Initiator eine Service-ID erstellt.  | 
| `iam-identity.account-serviceid.update` | Es wird ein Ereignis generiert, wenn ein Initiator eine Service-ID umbenennt oder die zugehörige Beschreibung ändert. | 
| `iam-identity.account-serviceid.delete` | Es wird ein Ereignis generiert, wenn ein Initiator eine Service-ID löscht. | 
{: caption="Tabelle 2. Aktionen beim Arbeiten mit Service-IDs" caption-side="top"} 


## Mit Ereignissen für API-Schlüssel arbeiten
{: #at_events_iam_apikeys}

In der folgenden Tabelle sind die Aktionen aufgelistet, die ein Ereignis generieren:

| Aktion | Beschreibung |
|----------|---------|
| `iam-identity.user-apikey.create`      | Es wird ein Ereignis generiert, wenn ein Initiator einen API-Schlüssel erstellt. | 
| `iam-identity.user-apikey.update`      | Es wird ein Ereignis generiert, wenn ein Initiator einen API-Schlüssel umbenennt oder die zugehörige Beschreibung ändert. |  
| `iam-identity.user-apikey.delete`      | Es wird ein Ereignis generiert, wenn ein Initiator einen API-Schlüssel löscht. |  
| `iam-identity.serviceid-apikey.create` | Es wird ein Ereignis generiert, wenn ein Initiator einen API-Schlüssel für eine Service-ID erstellt. |  
| `iam-identity.serviceid-apikey.delete` | Es wird ein Ereignis generiert, wenn ein Initiator einen API-Schlüssel für eine Service-ID löscht. |  
{: caption="Tabelle 3. Aktionen beim Arbeiten mit API-Schlüsseln" caption-side="top"} 


## Anmeldeereignisse
{: #at_events_iam_login}

In der folgenden Tabelle sind die Aktionen aufgelistet, die ein Ereignis generieren:

| Aktion | Beschreibung |
|----------|---------|
| `iam-identity.user-apikey.login`         | Es wird ein Ereignis generiert, wenn sich ein Benutzer bei der {{site.data.keyword.cloud_notm}} mit einem API-Schlüssel anmeldet. |  
| `iam-identity.serviceid-apikey.login`    | Es wird ein Ereignis generiert, wenn sich ein Benutzer bei der {{site.data.keyword.cloud_notm}} mit einem API-Schlüssel anmeldet, der einer Service-ID zugeordnet ist. |  
| `iam-identity.user-identitycookie.login` | Dieses Ereignis wird generiert, wenn ein Initiator ein neues Identitätscookie zum Ausführen einer Aktion anfordert. |
| `iam-identity.user-refreshtoken.login`   | Dieses Ereignis wird generiert, wenn sich der Initiator bei der IBM Cloud anmeldet oder wenn ein Initiator, der bereits bei der IBM Cloud angemeldet ist, ein neues Aktualisierungstoken zum Ausführen einer Aktion anfordert. |
{: caption="Tabelle 4. Aktionen bei der Benutzeranmeldung" caption-side="top"} 


## Ereignisse beim Verwalten von Richtlinien
{: #at_events_iam_policies}

In der folgenden Tabelle sind die Aktionen aufgelistet, die ein Ereignis generieren:

| Aktion | Beschreibung |
|----------|---------|
| `iam-am.policy.create` | Es wird ein Ereignis generiert, wenn ein Initiator eine Richtlinie zu einem Benutzer oder einer Zugriffsgruppe hinzufügt. |
| `iam-am.policy.delete` | Es wird ein Ereignis generiert, wenn ein Initiator die Berechtigungen für eine Richtlinie eines Benutzer oder einer Benutzergruppe ändert.|
| `iam-am.policy.update` | Es wird ein Ereignis generiert, wenn ein Initiator eine Richtlinie, die einem Benutzer oder einer Zugriffsgruppe zugewiesen ist, löscht. |
{: caption="Tabelle 5. Aktionen für Richtlinien verwalten" caption-side="top"} 


## Ereignisse anzeigen
{: #at_events_iam_ui}

Sie finden {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse sind in der **Kontodomäne** der Region **'Süden' der Vereinigten Staaten** (us-south) verfügbar.

Um diese Ereignisse anzeigen zu können, müssen Sie eine Instanz des {{site.data.keyword.cloudaccesstrailshort}}-Service in der Region **'Süden' der Vereinigten Staaten** ('us-south') bereitstellen. Danach müssen Sie die Benutzerschnittstelle (UI) für {{site.data.keyword.cloudaccesstrailshort}} öffnen und zu der Kontodomäne wechseln, um Ereignisse zu sehen. 

Weitere Informationen finden Sie in [Ereignisse für ein Konto anzeigen](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-view_acc_events#view_acc_events_account_events).



