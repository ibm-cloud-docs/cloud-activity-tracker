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



# Zum Kibana-Dashboard navigieren
{: #launch_kibana}

Sie können Kibana von der Benutzerschnittstelle (UI) für {{site.data.keyword.cloudaccesstrailshort}} aus {{site.data.keyword.Bluemix}} oder direkt von einem Web-Browser aus starten.
{:shortdesc}
   

##  Über das Dashboard des Activity Tracker-Service zu Kibana navigieren
{: #launch_Kibana_from_at}

Die in Kibana angezeigten Aktivitätenprotokolle enthalten Ereignisse für alle Ressourcen, die im Bereich der {{site.data.keyword.cloud_notm}}-Organisation verfügbar sind, bei der Sie angemeldet sind und in der der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt wird.

Führen Sie die folgenden Schritte aus, um Kibana über das Dashboard des {{site.data.keyword.cloudaccesstrailshort}}-Service zu starten:

1. Melden Sie sich bei Ihrem {{site.data.keyword.cloud_notm}}-Konto an.

    Das {{site.data.keyword.cloud_notm}}-Dashboard finden Sie unter [https://cloud.ibm.com/login ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/login){:new_window}. 
    
	Nachdem Sie sich mit Ihrer Benutzer-ID und Ihrem Kennwort angemeldet haben, wird die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle geöffnet.

2. Wählen Sie den {{site.data.keyword.cloudaccesstrailshort}}-Service im {{site.data.keyword.cloud_notm}}-Dashboard aus. 
    
3. Wählen Sie die Registerkarte **Verwaltet** aus.

4. Zum Anzeigen von Bereichsereignissen wählen Sie **Bereichsprotokolle** im Feld *Protokolle anzeigen* aus. **Hinweis:** Dies ist die Standardansicht. Klicken Sie dann auf **In Kibana anzeigen**.  

    Das Kibana-Dashboard wird geöffnet. Das Dashboard **ActivityTracker_Space_Dashboard_in_24h** wird mit einem Zeitfilter geladen, der auf die letzten 24 Stunden gesetzt ist. 

5. Zum Anzeigen von Kontoereignissen wählen Sie **Kontoprotokolle** im Feld *Protokolle anzeigen* aus. Klicken Sie dann auf **In Kibana anzeigen**.  

    Das Dashboard **ActivityTracker_Account_Dashboard_in_24h** wird mit einem Zeitfilter geladen, der auf die letzten 24 Stunden gesetzt ist. 
	
	
##  Über einen Web-Browser zu Kibana navigieren
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

3. Wählen Sie eine **Domäne** aus. 

    Wählen Sie **Konto** aus, um Ereignisse in der Kontodomäne anzuzeigen.
    Wählen Sie **Bereich** aus, um Ereignisse in einer Bereichsdomäne anzuzeigen. 

Die in Kibana angezeigten Ereignisse entsprechen den Ereignissen, die in der Domäne gehostet werden, welche in der Region, in der Sie Kibana gestartet haben, ausgewählt wurde. 


## Einschränkungen
{: #launch_kibana_limitations}

 Aufgrund von Einschränkungen in Kibana können in derselben Sitzung nicht mehrere Kibana-Browserregisterkarten zum Anzeigen verschiedener Bereiche oder Konten gleichzeitig geöffnet sein. Wenn Sie zwei oder mehr Sitzungen gleichzeitig geöffnet haben und von einer Bereichsdomäne zu einer Kontodomäne wechseln (oder umgekehrt), kann dies zu Problemen führen.
	



