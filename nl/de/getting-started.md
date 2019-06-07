---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, getting started

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


# Lernprogramm 'Einführung'
{: #getting-started}

Der {{site.data.keyword.cloudaccesstrailfull}}-Service zeichnet vom Benutzer eingeleitete Aktivitäten auf, die den Status eines Service in der {{site.data.keyword.cloud_notm}} ändern. Lernen Sie, wie Sie den {{site.data.keyword.cloudaccesstrailfull}}-Service verwenden, um die Interaktion eines Benutzers mit einem Cloud-Service zu überwachen. 
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} wird nicht mehr verwendet. Ab 09. Mai 2019 können keine neuen {{site.data.keyword.cloudaccesstrailshort}}-Instanzen mehr bereitgestellt werden. Vorhandene Instanzen des Premium-Plans werden bis 30. September 2019 unterstützt. Wenn Sie die Aktivitäten Ihres {{site.data.keyword.cloud_notm}}-Kontos weiterhin verfolgen möchten, stellen Sie eine Instanz von [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) bereit.
{: deprecated}


Die folgende Abbildung zeigt die verschiedenen Komponenten und Aktionen, die ausgeführt werden, wenn eine vom Benutzer eingeleitete Aktivität den Status eines Service ändert:

![Komponenten und Aktionen, die auftreten, wenn eine von einem Benutzer eingeleitete Aktivität den Status eines Service ändert](images/AT_f1.png "Komponenten und Aktionen, die auftreten, wenn eine vom Benutzer eingeleitete Aktivität den Status eines Service ändert")

**Hinweis:** Dieses Lernprogramm bietet Ihnen einen Einstieg in die Überwachung der Cloud-Aktivität in der Region 'Vereinigte Staaten (Süden)'.

## Vorbereitungen
{: #gs_prereqs}

* Lesen Sie die Informationen zum {{site.data.keyword.cloudaccesstrailshort}}-Service. Weitere Informationen finden Sie in [Informationen zu {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov).
* Stellen Sie fest, in welchen Regionen der Service verfügbar ist. Weitere Informationen finden Sie in [Regionen](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov_regions).
* Fordern Sie eine Benutzer-ID an, die ein Mitglied oder der Eigner eines {{site.data.keyword.cloud_notm}}-Kontos ist. [Hier registrieren ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/login){:new_window}



## Schritt 1. {{site.data.keyword.cloudaccesstrailshort}} bereitstellen
{: #gs_step1}

Beachten Sie die folgenden Informationen, wenn Sie eine Position für die Bereitstellung einer Instanz des {{site.data.keyword.cloudaccesstrailshort}}-Service auswählen:

* {{site.data.keyword.cloudaccesstrailshort}} erfasst Ereignisse in Domänen. Es gibt eine Kontodomäne pro Region und eine Bereichsdomäne (Space Domain) pro Cloud Foundry-Bereich (CF-Bereich). 

* **Zum Überwachen von globalen Kontoaktionen** müssen Sie eine Instanz des {{site.data.keyword.cloudaccesstrailshort}}-Service in der Region 'Vereinigte Staaten (Süden)' bereitstellen. Einige Beispiele für globale Aktionen sind die Bereitstellung einer Instanz, die Änderung der IAM-Richtlinie eines Benutzers oder die Einladung eines Benutzers für das Konto.

* **Zum Überwachen von Ereignissen, die durch einen im Kontext einer CF-Organisation und eines CF-Bereichs bereitgestellten Service generiert werden**, müssen Sie eine Instanz des {{site.data.keyword.cloudaccesstrailshort}}-Service in der Region und in dem Bereich bereitstellen, in der auch der Service mit den zu überwachenden Aktivitäten bereitgestellt wird. 

* **Zum Überwachen von Ereignissen, die durch einen im Kontext einer Ressourcengruppe bereitgestellten Service generiert werden**, müssen Sie eine Instanz des {{site.data.keyword.cloudaccesstrailshort}}-Service in einem Bereich in der Region bereitstellen, in der auch der Service mit den zu überwachenden Aktivitäten bereitgestellt wird. 

* Zum Bereitstellen einer Instanz muss Ihre Benutzer-ID über die **Entwicklerrolle** in dem Bereich verfügen, in dem der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt werden soll.

Führen Sie die folgenden Schritte aus, um eine Instanz des {{site.data.keyword.cloudaccesstraillong_notm}}-Service in der {{site.data.keyword.cloud_notm}} bereitzustellen:

1. [Melden Sie sich bei {{site.data.keyword.cloud_notm}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/login){:new_window} an.

    Nachdem Sie sich mit Ihrer Benutzer-ID und Ihrem Kennwort angemeldet haben, wird die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle geöffnet.

2. Klicken Sie auf **Katalog**. Die Liste der in der {{site.data.keyword.cloud_notm}} verfügbaren Services wird geöffnet.

3. Wählen Sie die Kategorie **Sicherheit und Identität** aus, um die Liste der angezeigten Services zu filtern.

    **Hinweis:** Der Service ist auch über die Kategorie **Entwicklertools** verfügbar.

4. Klicken Sie auf die Kachel **Activity Tracker**. 

5. Konfigurieren Sie die entsprechenden Informationen, um zu definieren, wo der Service bereitgestellt werden soll.

    Wenn Sie beispielsweise den Service in der Region 'Vereinigte Staaten (Süden)' bereitstellen möchten, geben Sie die Daten wie in der folgenden Tabelle angegeben ein: 

    <table>
	  <caption>Tabelle 1. Erforderliche Felder zum Bereitstellen des {{site.data.keyword.cloudaccesstrailshort}}-Service</caption>
	  <tr>
	    <th width="50%">Feld</th>
		<th width="50%">Wert</th>
	  </tr>
	  <tr>
	    <td>Region für die Bereitstellung auswählen:</td>
		<td>Vereinigte Staaten (Süden)</td>
	  </tr>
	  <tr>
	    <td>Organisation auswählen:</td>
		<td>Wählen Sie die Organisation aus, in der Sie beabsichtigen, den {{site.data.keyword.cloudaccesstrailshort}}-Service bereitzustellen.</td>
	  </tr>
	  <tr>
	    <td>Bereich auswählen</td>
		<td>Wählen Sie den Bereich (Space) aus, in dem der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt werden soll.</td>
	  </tr>
	</table>

6. Wählen Sie einen Plan aus. 

    Standardmäßig ist der Plan **Lite** ausgewählt.

	Weitere Informationen finden Sie in [Servicepläne](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov#activity_tracker_ov_plan).

7. Klicken Sie auf **Erstellen**, um eine Instanz des {{site.data.keyword.cloudaccesstrailshort}}-Service in dem Bereich zu erstellen, in dem Sie angemeldet sind.
   


## Schritt 2. Benutzern Zugriff für die Überwachung von Ereignissen erteilen
{: #gs_step2}

Zum Anzeigen von Ereignissen benötigen Sie Zugriffsberechtigungen in der {{site.data.keyword.cloud_notm}}. Die Berechtigungen hängen davon ab, ob Sie globale Kontoereignisse, Ereignisse für einen im Kontext einer Ressourcengruppe bereitgestellten Service oder Ereignisse für einen im Kontext einer CF-Organisation und eines CF-Bereichs bereitgestellten Service anzeigen möchten. 

Beachten Sie die folgenden Informationen für die **Überwachung globaler Kontoaktionen** und die **Überwachung eines im Kontext einer Ressourcengruppe bereitgestellten Service**:

* Sie müssen über eine IAM-Richtlinie für den {{site.data.keyword.loganalysisshort}}-Service mit der Rolle **Leseberechtigter** für den {{site.data.keyword.loganalysisshort}}-Service verfügen. 
* Der Kontoeigner oder ein Administrator des {{site.data.keyword.loganalysisshort}}-Service kann diese Richtlinie erteilen.

Beachten Sie die folgenden Informationen für die **Überwachung eines im Kontext einer CF-Organisation und eines CF-Bereichs bereitgestellten Service**:

* Sie müssen über die Rolle **Entwickler** für den Bereich verfügen, in dem Sie eine Instanz des {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt haben.
* Der Kontoeigner, der Organisationsmanager oder der Bereichsmanager können Ihnen die Rolle **Entwickler** für den Bereich erteilen.

**Hinweis: Sie müssen der Kontoeigner oder ein Administrator des {{site.data.keyword.loganalysisshort}}-Service sein, um einem Benutzer eine IAM-Richtlinie zu erteilen.**

### Benutzern Zugriff für die Überwachung von Kontodomänenereignissen erteilen
{: #index_acc}

Führen Sie die folgenden Schritte aus, um einem Benutzer über die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle (UI) eine IAM-Richtlinie zu erteilen:

1. [Melden Sie sich bei der {{site.data.keyword.cloud_notm}}-Konsole ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/login){:new_window} an.
2. Klicken Sie in der Menüleiste auf **Verwalten** &gt; **Sicherheit** &gt; **Identität und Zugriff** und wählen Sie anschließend **Benutzer** aus.
3. Wählen Sie in der Zeile für den Benutzer, dem Sie Zugriff zuweisen möchten, das Menü **Aktionen** aus und klicken Sie dann auf **Zugriff zuweisen**.
4. Wählen Sie **Zugriff auf Ressourcen zuweisen** aus.
5. Wählen Sie **Protokollanalyse** aus.
6. Wählen Sie **Alle Regionen** aus.
7. Wählen Sie **Alle Serviceinstanzen** aus.
8. Wählen Sie die Servicerolle **Leseberechtigter** aus.
9. Klicken Sie auf 'Zuweisen'.

### Benutzern Zugriff für die Überwachung von Bereichsdomänenereignissen erteilen
{: #gs_space}

Führen Sie die folgenden Schritte aus, um einem Benutzer über die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle die Entwicklerrolle in einem Bereich zu erteilen:

1. Melden Sie sich bei der {{site.data.keyword.cloud_notm}}-Konsole an. 

    Öffnen Sie einen Web-Browser und starten Sie das [{{site.data.keyword.cloud_notm}}-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/login){:new_window}. 
	
	Nachdem Sie sich mit Ihrer Benutzer-ID und Ihrem Kennwort angemeldet haben, wird die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle geöffnet.

2. Klicken Sie in der Menüleiste auf **Verwalten** &gt; **Sicherheit** &gt; **Identität und Zugriff** und wählen Sie anschließend **Benutzer** aus.

3. Wählen Sie den Benutzer aus.

4. Wählen Sie **Cloud Foundry-Zugriff** aus.

5. Erweitern Sie eine Organisation.

    Die Bereiche, die in dieser Organisation verfügbar sind, werden aufgelistet.

6. Wählen Sie im Aktionsmenü **Organisationsrolle bearbeiten** aus. Wählen Sie die Rolle **Auditor** im Feld *Organisationsrollen* aus. Klicken Sie anschließend auf **Rolle speichern**.

7. Wählen Sie einen Bereich aus. 

8. Wählen Sie im Aktionsmenü **Bereichsrolle bearbeiten** aus. Wählen Sie die Rolle **Entwickler** im Feld *Bereichsrollen* aus. Klicken Sie anschließend auf **Rolle speichern**.
	
7. Klicken Sie auf **Zuweisen**.



## Schritt 3. {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse generieren
{: #gs_step3}

Nachdem der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt worden ist, werden automatisch Ereignisse von den ausgewählten Cloud-Services erfasst. Weitere Informationen zu den Services, die Sie mit {{site.data.keyword.cloudaccesstrailshort}} überwachen können, sowie Informationen zu den Aktionen, durch die ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis generiert wird, finden Sie [Cloud-Services](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-cloud_services#cloud_services).

**Hinweis:** Damit ein Benutzer {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse für {{site.data.keyword.BluVirtServers_short}} und {{site.data.keyword.baremetal_short}} generieren kann, benötigt er Zugriff auf Infrastrukturressourcen in der IBM Cloud-Konsole. Weitere Informationen finden Sie in [{{site.data.keyword.BluVirtServers_short}}- und {{site.data.keyword.baremetal_short}}-Aktivität mit {{site.data.keyword.cloudaccesstrailshort}} überwachen](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-vsi#vsi).

Führen Sie das Lernprogramm [{{site.data.keyword.keymanagementserviceshort}}-Aktivität mit {{site.data.keyword.cloudaccesstrailshort}} überwachen](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-kp#kp) aus, um zu lernen, wie Ereignisse generiert werden.

## Schritt 4. Ereignisse anzeigen
{: #gs_step4}

Sie können {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse in der {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle überwachen. Sie können Ihren Plan auch auf einen Premium-Plan aufrüsten, um Ereignisse über Kibana zu überwachen. 

Beachten Sie die folgenden Informationen für die **Überwachung globaler Kontoaktionen** und die **Überwachung eines im Kontext einer Ressourcengruppe bereitgestellten Service**:

* Ereignisse werden in einer Kontodomäne erfasst.

    Es gibt eine Kontodomäne pro Region.

    Globale Kontoaktionen werden in der Kontodomäne 'Vereinigte Staaten (Süden)' erfasst.

    Ereignisse für einen Service werden in der Kontodomäne der Region erfasst, in der eine Instanz dieses Service bereitgestellt wird.

* Der Kontoeigner kann Ereignisse entweder über die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle oder in Kibana anzeigen.
* Andere Benutzer können nur Kontodomänenereignisse über Kibana anzeigen. 


Beachten Sie die folgenden Informationen für die **Überwachung eines im Kontext einer CF-Organisation und eines CF-Bereichs bereitgestellten Service**:

* Ereignisse werden in einer Bereichsdomäne erfasst. 
* Jedem CF-Bereich ist eine {{site.data.keyword.cloudaccesstrailshort}}-Bereichsdomäne zugeordnet. 
* Sie können Ereignisse entweder über die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle oder in Kibana anzeigen.

In der folgenden Tabelle ist die {{site.data.keyword.cloudaccesstrailshort}}-Domäne definiert, in der Ereignisse überwacht werden müssen:

| Überwachung                                                           | {{site.data.keyword.cloudaccesstrailshort}}-Domäne |  
|----------------------------------------------------------------------|----------------------------------------------------| 
| `Globale Kontoaktionen`                                             | Kontodomäne 'Vereinigte Staaten (Süden)'                            |  
| `Im Kontext einer Ressourcengruppe bereitgestellte Services`   | Kontodomäne                                     | 
| `Im Kontext einer CF-Organisation und eines CF-Bereichs bereitgestellte Services` | Bereichsdomäne                                       | 
{: caption="Tabelle 1. {{site.data.keyword.cloudaccesstrailshort}}-Domänen nach Ereignisquelle" caption-side="top"} 

Zum Anzeigen von Ereignissen können Sie eine der folgenden Optionen auswählen:

* [Zum Activity Tracker-Dashboard navigieren, um die Cloud-Aktivität in dem Konto zu überwachen](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui#launch_at_ui_account_view_account) 
* [Zum Activity Tracker-Dashboard navigieren, um die Cloud-Aktivität in einem Bereich zu überwachen](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui#launch_at_ui_account_view_space) 
* [Über einen Web-Browser zu Kibana navigieren](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_kibana#launch_kibana)

Wählen Sie [Zum Activity Tracker-Dashboard navigieren, um die Cloud-Aktivität in dem Konto zu überwachen](/docs/services/cloud-activity-tracker/how-to/manage-events-ui?topic=cloud-activity-tracker-launch_at_ui#launch_at_ui_account_view_account) aus, um die Ereignisse anzuzeigen, die Sie durch die Ausführung der Schritte in diesem Lernprogramm generiert haben. Wenn Sie nicht der Kontoeigner sind, rüsten Sie den Serviceplan auf und überprüfen Sie, ob Sie über die korrekten Zugriffsberechtigungen zum Anzeigen von Ereignissen verfügen. 


## Nächste Schritte
{: #gs_next_steps}

Verwenden Sie die {{site.data.keyword.cloudaccesstrailshort}}-Befehlszeilenschnittstelle (CLI), um die Ereignisse über die Befehlszeile zu verwalten. Weitere Informationen finden Sie in [Ereignisse mithilfe der Activity Tracker-CLI verwalten](/docs/services/cloud-activity-tracker/tutorials?topic=cloud-activity-tracker-tutorial2#tutorial2).



