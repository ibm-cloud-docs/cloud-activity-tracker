---

copyright:
  years: 2016, 2017
lastupdated: "2017-09-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Lernprogramm 'Einführung'
{: #getting-started-with-cla}

Der {{site.data.keyword.cloudaccesstrailfull}}-Service zeichnet vom Benutzer eingeleitete Aktivitäten auf, die den Status eines Service in der {{site.data.keyword.IBM}} Cloud ändern. In diesem Lernprogramm erfahren Sie, wie Sie mit dem {{site.data.keyword.cloudaccesstrailfull}}-Service die Interaktion eines Benutzers mit einem Cloud-Service überwachen können.
{:shortdesc}

Das Lernprogramm 'Einführung' hat die folgenden Ziele:

1. Die Vorgehensweise zum Bereitstellen des {{site.data.keyword.cloudaccesstrailshort}}-Service erläutern
2. Die Verwendung eines Cloud-Service zum Generieren von Aktivitätsereignissen erläutern, die vom {{site.data.keyword.cloudaccesstrailshort}}-Service automatisch erfasst werden. Die Ereignisse erfüllen den CADF-Standard (CADF = Cloud Auditing Data Federation).
3. Die Vorgehensweise zum Überwachen der Cloud-Aktivität eines Service unter Verwendung des vordefinierten {{site.data.keyword.cloudaccesstrailshort}}-Dashboards erläutern

Die folgende Abbildung zeigt die verschiedenen Komponenten und Aktionen, die ausgeführt werden, wenn eine vom Benutzer eingeleitete Aktivität den Status eines Service ändert:

![Komponenten und Aktionen, die auftreten, wenn eine von einem Benutzer eingeleitete Aktivität den Status eines Service ändert](images/AT_f1.png "Komponenten und Aktionen, die auftreten, wenn eine vom Benutzer eingeleitete Aktivität den Status eines Service ändert")



## Vorbereitungen
{: #prereqs}

Erstellen Sie ein [{{site.data.keyword.Bluemix_notm}}-Konto](https://console.bluemix.net/registration/). Ihre Benutzer-ID muss Mitglied eines {{site.data.keyword.Bluemix_notm}}-Kontos mit Entwicklerberechtigungen für den Bereich sein, in dem Sie den {{site.data.keyword.cloudaccesstrailshort}}-Service verwenden möchten.


## Schritt 1: Activity Tracker bereitstellen
{: #step1}

Sie müssen den {{site.data.keyword.cloudaccesstrailshort}}-Service in derselben Region und im selben Bereich bereitstellen wie den Cloud-Service, dessen Aktivität Sie überwachen möchten. Nachdem der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt wurde, werden automatisch Ereignisse von den ausgewählten Cloud-Services erfasst, die in dem betreffenden Bereich bereitgestellt sind. In [Unterstützte Cloud-Services](/docs/services/cloud-activity-tracker/cloud_services.html#cloud_services) finden Sie eine Liste der Services, deren Aktivitäten Sie mit {{site.data.keyword.cloudaccesstrailshort}} überwachen können.

**Anmerkung:** In diesem Lernprogramm erfahren Sie, wie Sie mit dem {{site.data.keyword.cloudaccesstrailshort}}-Service die Interaktion eines Benutzers mit dem Cloud-Service {{site.data.keyword.keymanagementservicelong_notm}} überwachen können. Der {{site.data.keyword.keymanagementserviceshort}}-Service ist in der Region 'Vereinigte Staaten (Süden)' verfügbar. Daher müssen Sie {{site.data.keyword.cloudaccesstrailshort}} in der Region 'Vereinigte Staaten (Süden) in demselben Bereich bereitstellen, in dem der {{site.data.keyword.keymanagementserviceshort}}-Service verfügbar ist. Informationen dazu, in welcher Region ein Service verfügbar ist, finden Sie in [Services nach Region](/docs/services/services_region.html#services_region).

Führen Sie die folgenden Schritte aus, um eine Instanz des {{site.data.keyword.cloudaccesstraillong_notm}}-Service in {{site.data.keyword.Bluemix_notm}} bereitzustellen:

1. Melden Sie sich bei Ihrem {{site.data.keyword.Bluemix_notm}}-Konto an.

    Das {{site.data.keyword.Bluemix_notm}}-Dashboard finden Sie unter [http://bluemix.net ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://bluemix.net){:new_window}.
    
	Nachdem Sie sich mit Ihrer Benutzer-ID und Ihrem Kennwort angemeldet haben, wird die {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle geöffnet.

2. Klicken Sie auf **Katalog**. Die Liste der in {{site.data.keyword.Bluemix_notm}} verfügbaren Services wird geöffnet.

3. Wählen Sie die Kategorie **Sicherheit** aus, um die Liste der angezeigten Services zu filtern.

4. Klicken Sie auf die Kachel **Activity Tracker**. 

5. Konfigurieren Sie die entsprechenden Informationen, um zu definieren, wo der Service bereitgestellt werden soll. 

    Geben Sie die Daten ein, wie in der folgenden Tabelle angegeben: 

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
		<td>Wählen Sie die Organisation aus, in der Sie Aktivitäten überwachen möchten.</td>
	  </tr>
	  <tr>
	    <td>Bereich auswählen</td>
		<td>Wählen Sie den Bereich in der ausgewählten Organisation aus, in dem Sie Aktivitäten überwachen möchten.</td>
	  </tr>
	</table>

6. Klicken Sie auf **Erstellen**, um den {{site.data.keyword.cloudaccesstrailshort}}-Service in dem {{site.data.keyword.Bluemix_notm}}-Bereich bereitzustellen, bei dem Sie angemeldet sind.
   

## Schritt 2:  Einen Cloud-Service bereitstellen 
{: #step2}
	
Führen Sie die folgenden Schritte aus, um eine Instanz des {{site.data.keyword.keymanagementserviceshort}}-Service in der {{site.data.keyword.Bluemix_notm}}-Region 'Vereinigte Staaten (Süden)' bereitzustellen:

1. Melden Sie sich bei Ihrem {{site.data.keyword.Bluemix_notm}}-Konto an.

    Das {{site.data.keyword.Bluemix_notm}}-Dashboard finden Sie unter [http://bluemix.net ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://bluemix.net){:new_window}.
	
	Nachdem Sie sich mit Ihrer Benutzer-ID und Ihrem Kennwort angemeldet haben, wird die {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle geöffnet.

2. Klicken Sie auf **Katalog**. Die Liste der in {{site.data.keyword.Bluemix_notm}} verfügbaren Services wird geöffnet.

    Wählen Sie die Kategorie **Sicherheit** aus, um die Liste der angezeigten Services zu filtern.

3. Wählen Sie die Kachel **Key Protect** aus.

4. Konfigurieren Sie die entsprechenden Informationen, um zu definieren, wo der Service bereitgestellt werden soll. 

    Geben Sie die Daten ein, wie in der folgenden Tabelle angegeben: 

    <table>
	  <caption>Tabelle 2. Erforderliche Felder zum Bereitstellen des {{site.data.keyword.keymanagementserviceshort}}-Service</caption>
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
		<td>Wählen Sie die Organisation aus, in der Sie den {{site.data.keyword.cloudaccesstrailshort}}-Service bereitstellen möchten.</td>
	  </tr>
	  <tr>
	    <td>Bereich auswählen</td>
		<td>Wählen Sie den Bereich aus, in dem Sie den {{site.data.keyword.cloudaccesstrailshort}}-Service bereitstellen möchten.</td>
	  </tr>
	</table>

5. Klicken Sie auf **Erstellen**, um den {{site.data.keyword.keymanagementserviceshort}}-Service in dem {{site.data.keyword.Bluemix_notm}}-Bereich bereitzustellen, bei dem Sie angemeldet sind.


## Schritt 3: Ein Activity Tracker-Ereignis generieren
{: # step3}

In diesem Schritt erstellen Sie mit dem {{site.data.keyword.keymanagementserviceshort}}-Service einen Sicherheitsschlüssel, um {{site.data.keyword.cloudaccesstrailshort}}-Ereignisdaten zu generieren. 

Führen Sie die folgenden Schritte aus, um ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis zu generieren:

1. Wählen Sie im {{site.data.keyword.Bluemix_notm}}-Dashboard den **Key Protect**-Service aus. Das {{site.data.keyword.keymanagementserviceshort}}-Dashboard wird geöffnet. Wählen Sie anschließend die Registerkarte **Verwalten** aus.

2. Klicken Sie auf **Schlüssel hinzufügen**. Ein neues Fenster wird geöffnet.

3. Wählen Sie **Schlüssel generieren** aus und führen Sie die folgenden Schritte aus:

    * Geben Sie einen Namen für den Schlüssel ein (z. B. *MeinErsterSchlüssel*).

    * Wählen Sie den Algorithmus für den Schlüssel aus.

    * Klicken Sie auf **Schlüssel hinzufügen**. 
	
{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse werden als Ergebnis der Erstellung eines Schlüssels generiert.

## Schritt 4: Ein Activity Tracker-Ereignis überwachen
{: #step4}

In diesem Schritt überprüfen Sie mithilfe der {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle, dass {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse generiert wurden.

Führen Sie die folgenden Schritte aus, um zu überprüfen, dass ein Ereignis erstellt wurde:

1. Wählen Sie im {{site.data.keyword.Bluemix_notm}}-Dashboard den {{site.data.keyword.cloudaccesstrailshort}}-Service aus. Das Service-Dashboard wird geöffnet.

2. Konfigurieren Sie die Ansicht, in der nach den {{site.data.keyword.keymanagementserviceshort}}-Ereignissen gesucht werden soll, die beim Bereitstellen des Service und Hinzufügen eines Schlüssels generiert wurden.

    * Wählen Sie **Bereichsprotokolle** für das Feld *Protokolle anzeigen* aus.
    * Wählen Sie **target.name** für das Feld *Suchfeld* aus.
    * Geben Sie **ibm-key-protect** in das Feld *Filter* ein.
	
    Die angezeigten Daten enthalten verfügbare {{site.data.keyword.keymanagementserviceshort}}-Ereignisse für die letzten 24 Stunden. 
	
	![Ereignisansicht in der Benutzerschnittstelle](images/bmx_ui_space_view.png "Ereignisansicht in der Benutzerschnittstelle")


## Nächste Schritte
{: #next_steps}

Verwenden Sie anschließend das vordefinierte Kibana-Dashboard in {{site.data.keyword.cloudaccesstrailshort}}, um Ereignisprotokolle zu überwachen und zu analysieren. Informationen zum Starten von Kibana finden Sie in [Zum Kibana-Dashboard](/docs/services/cloud-activity-tracker/how-to/manage-events-ui/launch_kibana.html#launch_kibana) navigieren. 

In Kibana werden die Protokolle für Bereichsaktivitäten standardmäßig im Dashboard **ActivityTracker_Space_Search_in_24h** angezeigt:

![Ereignisansicht in Kibana](images/kibana_space_view.png "Ereignisansicht in Kibana")

Sie können auch die {{site.data.keyword.cloudaccesstrailshort}}-CLI verwenden, um Ihre Ereignisse über die Befehlszeile zu verwalten. Weitere Informationen finden Sie in [Ereignisinformationen anzeigen](/docs/services/cloud-activity-tracker/how-to/manage-events-cli/viewing_event_information.html#viewing_event_status).

                                                                                                                      

