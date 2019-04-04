---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, launch Kibana

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



# Kibana-Dashboard öffnen
{: #launch_kibana}

Sie können Kibana von der Benutzerschnittstelle (UI) für {{site.data.keyword.cloudaccesstrailshort}} aus {{site.data.keyword.cloud_notm}} oder direkt von einem Web-Browser aus starten.
{:shortdesc}
   

##  Kibana vom Dashboard des Activity Tracker-Service aus öffnen
{: #launch_Kibana_from_at}

Die in Kibana angezeigten Aktivitätenprotokolle enthalten Ereignisse für alle Ressourcen, die im Bereich der {{site.data.keyword.cloud_notm}}-Organisation verfügbar sind, bei der Sie angemeldet sind und in der der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt wird.

Führen Sie die folgenden Schritte aus, um Kibana über das Dashboard des {{site.data.keyword.cloudaccesstrailshort}}-Service zu starten:

1. Melden Sie sich bei Ihrem {{site.data.keyword.cloud_notm}}-Konto an.

    Das {{site.data.keyword.cloud_notm}}-Dashboard finden Sie unter [https://cloud.ibm.com/login ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/login){:new_window}.
    
	Nachdem Sie sich mit Ihrer Benutzer-ID und Ihrem Kennwort angemeldet haben, wird die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle geöffnet.

2. Wählen Sie den {{site.data.keyword.cloudaccesstrailshort}}-Service im {{site.data.keyword.cloud_notm}}-Dashboard aus. 
    
3. Wählen Sie die Registerkarte **Verwaltet** aus.

4. Zum Anzeigen von Bereichsereignissen wählen Sie **Bereichsprotokolle** im Feld *Protokolle anzeigen* aus. **Hinweis:** Dies ist die Standardansicht. Klicken Sie dann auf **In Kibana anzeigen**. 

    Das Kibana-Dashboard wird geöffnet. Das Dashboard **ActivityTracker_Space_Dashboard_in_24h** wird mit einem Zeitfilter geladen, der auf die letzten 24 Stunden gesetzt ist.

5. Zum Anzeigen von Kontoereignissen wählen Sie **Kontoprotokolle** im Feld *Protokolle anzeigen* aus. Klicken Sie dann auf **In Kibana anzeigen**. 

    Das Dashboard **ActivityTracker_Account_Dashboard_in_24h** wird mit einem Zeitfilter geladen, der auf die letzten 24 Stunden gesetzt ist.
	
	
##  Kibana von einem Web-Browser aus öffnen
{: #launch_Kibana_from_browser}

Führen Sie die folgenden Schritte aus, um Kibana über einen Browser zu starten:

1. Öffnen Sie einen Web-Browser und starten Sie Kibana in der Region, in der Sie Ereignisse überwachen möchten. Melden Sie sich anschließend bei der Kibana-Benutzerschnittstelle an.
    
    In der folgenden Tabelle sind Beispiele für die URLs zum Starten von Kibana nach Region aufgelistet:
      
    <table>
          <caption>Tabelle 1. URLs zum Starten von Kibana nach Region</caption>
           <tr>
            <th>Region</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>Deutschland</td>
            <td>[https://logging.eu-fra.bluemix.net](https://logging.eu-fra.bluemix.net) </td>
          </tr>
          <tr>
            <td>Sydney</td>
            <td>[https://logging.au-syd.bluemix.net](https://logging.au-syd.bluemix.net) </td>
          </tr>
		  <tr>
            <td>Vereinigtes Königreich</td>
            <td>[https://logging.eu-gb.bluemix.net](https://logging.eu-gb.bluemix.net)</td>
          </tr>
		  <tr>
            <td>Vereinigte Staaten (Süden)</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
    </table>
	
	Die Kibana-Seite für Erkennung wird geöffnet.
	
2. Überprüfen Sie, dass Sie bei dem {{site.data.keyword.cloud_notm}}-Konto angemeldet sind, in dem Sie Aktivitätsereignisse anzeigen und analysieren möchten.

3. Zeigen Sie Bereichs- oder Kontoereignisse an. 

* Klicken Sie in der rechten oberen Ecke des Kibana-Fensters auf die Position, an der Ihre Anmeldeinformationen angezeigt werden. 
* Unter **Domäne** wählen Sie in der Dropdown-Liste die Option für Bereich oder Konto aus. 
* Für Bereichsereignisse wählen Sie in der Dropdown-Liste **Bereich** den gewünschten Bereich aus. 
* Für Kontoereignisse wählen Sie in der Dropdown-Liste **Konto** das richtige Konto aus. 

4. Passen Sie die Suchzeit an. 

* Die Kibana-Standardsuchzeit ist auf die letzten 15 Minuten gesetzt. 
* Klicken Sie in der oberen rechten grauen Leiste auf `Letzte 15 Minuten`. 
* Wählen Sie den Zeitraum aus, für den Ereignisse angezeigt werden sollen. Die Ereignisse der letzten 3 Tage können für die Suche angegeben werden. Wählen Sie einen Zeitraum von maximal 3 Tagen aus. 

5. Filtern Sie, um nur Activity Tracker-Ereignisse anzuzeigen. 
* Bei der direkten Anzeige in Kibana werden sowohl Protokolle als auch Activity Tracker-Ereignisse aufgeführt. 
* Geben Sie in der Suchleiste `type:ActivityTracker` ein, um nur Activity Tracker-Ereignisse anzuzeigen. 

Die in Kibana angezeigten Ereignisse entsprechen den Ereignissen, die in der Domäne gehostet werden, welche in der Region, in der Sie Kibana gestartet haben, ausgewählt wurde.

## Einschränkungen
{: #launch_kibana_limitations}

* Aufgrund von Einschränkungen in Kibana können in derselben Sitzung nicht mehrere Kibana-Browserregisterkarten zum Anzeigen verschiedener Bereiche oder Konten gleichzeitig geöffnet sein. Wenn Sie zwei oder mehr Sitzungen gleichzeitig geöffnet haben und von einer Bereichsdomäne zu einer Kontodomäne wechseln (oder umgekehrt), kann dies zu Problemen führen.
* Standardmäßig kann nur der Kontoeigner Kontoereignisse anzeigen. Befolgen Sie die Anweisungen in [Ereignisse für ein Konto anzeigen](https://cloud.ibm.com/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-view_acc_events#view_acc_events), um anderen Personen die Anzeige von Kontoereignissen zu ermöglichen. 



