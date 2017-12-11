---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-17"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Zum Kibana-Dashboard navigieren
{: #launch_kibana}

Sie können Kibana über die {{site.data.keyword.cloudaccesstrailshort}}-Benutzerschnittstelle in {{site.data.keyword.Bluemix}} starten oder direkt über einen Web-Browser.
{:shortdesc}
   

##  Über das Dashboard des Activity Tracker-Service zu Kibana navigieren
{: #launch_Kibana_from_at}

Die in Kibana angezeigten Aktivitätenprotokolle enthalten Ereignisse für alle Ressourcen, die im Bereich der {{site.data.keyword.Bluemix_notm}}-Organisation verfügbar sind, bei der Sie angemeldet sind und in der der {{site.data.keyword.cloudaccesstrailshort}}-Service bereitgestellt ist.

Führen Sie die folgenden Schritte aus, um Kibana über das Dashboard des {{site.data.keyword.cloudaccesstrailshort}}-Service zu starten:

1. Melden Sie sich bei Ihrem {{site.data.keyword.Bluemix_notm}}-Konto an.

    Das {{site.data.keyword.Bluemix_notm}}-Dashboard finden Sie unter [http://bluemix.net ![Symbole für externen Link](../../../../icons/launch-glyph.svg "Symbol für externen Link")](http://bluemix.net){:new_window}.
    
	Nachdem Sie sich mit Ihrer Benutzer-ID und Ihrem Kennwort angemeldet haben, wird die {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle geöffnet.

2. Wählen Sie den {{site.data.keyword.cloudaccesstrailshort}}-Service im {{site.data.keyword.Bluemix_notm}}-Dashboard aus. 
    
3. Wählen Sie die Registerkarte **Verwaltet** aus.

4. Klicken Sie auf **Erweiterte Ansicht**. 

    Das Kibana-Dashboard wird geöffnet.

Standardmäßig wird das Dashboard **ActivityTracker_Space_Dashboard_in_24h** geladen und ein Zeitfilter für die letzten 24 Stunden festgelegt. 


	
	
##  Über einen Web-Browser zu Kibana navigieren
{: #launch_Kibana_from_browser}

Die in Kibana angezeigten Protokollinformationen enthalten Ereignisse für alle Ressourcen, die im Bereich der {{site.data.keyword.Bluemix_notm}}-Organisation bereitgestellt sind, bei der Sie angemeldet sind.

Führen Sie die folgenden Schritte aus, um Kibana über einen Browser zu starten:

1. Öffnen Sie einen Web-Browser und starten Sie Kibana. Melden Sie sich anschließend bei der Kibana-Benutzerschnittstelle an.
    
    In der folgenden Tabelle sind Beispiele für die URLs zum Starten von Kibana in den angegebenen Regionen aufgelistet:
      
    <table>
          <caption>Tabelle 1. URLs zum Starten von Kibana in bestimmten Regionen</caption>
           <tr>
            <th>Region</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>Vereinigte Staaten (Süden)</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
		  <tr>
            <td>Vereinigtes Königreich</td>
            <td>[https://logmet.eu-gb.bluemix.net](https://logmet.eu-gb.bluemix.net)</td>
          </tr>
    </table>
	
	Die Kibana-Seite für Erkennung wird geöffnet.
	
2. Überprüfen Sie, dass Sie in {{site.data.keyword.Bluemix_notm}} bei dem Konto, der Organisation und dem Bereich angemeldet sind, in dem Sie Aktivitätenprotokolle anzeigen und analysieren möchten.

    Die verfügbaren Ereignisse und Protokolle für den Bereich, bei dem Sie angemeldet sind, werden angezeigt.

3. Um nach Ereignissen zu filtern, wählen Sie in der Menüleiste die Option **Öffnen** aus.

    Die Liste der gespeicherten Dashboards wird angezeigt.
	
4. Um die Ereignisse für den Bereich anzuzeigen, bei dem Sie angemeldet sind, wählen Sie **ActivityTracker_Space_Dashboard_in_24h** aus.


## Einschränkungen
{: #limitations}

 Aufgrund von Einschränkungen in Kibana können in derselben Sitzung nicht mehrere Kibana-Browserregisterkarten zum Anzeigen verschiedener Bereiche oder Konten gleichzeitig geöffnet sein. Wenn Sie zwei oder mehr Sitzungen gleichzeitig geöffnet haben und von einer Bereichsdomäne zu einer Kontodomäne wechseln (oder umgekehrt), kann dies zu Problemen führen.
	



