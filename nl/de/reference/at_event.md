---

copyright:
  years: 2016, 2017

lastupdated: "2017-09-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Activity Tracker-Ereignisfelder
{: #at_event}

{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse basieren auf dem CADF-Standard (CADF = Cloud Auditing Data Federation).
{:shortdesc}

## Ereignisfelder
{: #fields}

In der folgenden Tabelle sind die Felder aufgelistet, die für die Analyse eines {{site.data.keyword.cloudaccesstrailshort}}-Ereignisses verfügbar sind:

<table>
  <caption>Tabelle 1. Für die Ereignisüberwachung verfügbare Felder</caption>
  <tr>
    <th>Feldname</th>
	<th>Status</th>
	<th>Beschreibung</th>
  </tr>
  <tr>
    <td>outcome</td>
	<td>Erforderlich</td>
	<td>Gültige Werte sind: *success*, *failure*.</td>
  </tr>
  <tr>
    <td>typeURI</td>
	<td>Erforderlich</td>
	<td>Dieses Feld ist auf den Wert *http://schemas.dmtf.org/cloud/audit/1.0/event* gesetzt.</td>
  </tr>
  <tr>
    <td>eventType</td>
	<td>Erforderlich</td>
	<td>Dieses Feld ist auf den Wert *activity* gesetzt.</td>
  </tr>
  <tr>
    <td>eventTime</td>
	<td>Erforderlich</td>
	<td>Das Datum wird als ISO-Zeichenfolge dargestellt, z. B. *2017-09-17 15:15:32.396 +0000 UTC*.</td>
  </tr>
  <tr>
    <td>action</td>
	<td>Erforderlich</td>
	<td>Dieses Feld gibt die Aktion an, durch die das Ereignis ausgelöst wurde (z. B. *read.ibm-key-protect.secrets*).</td>
  </tr>
  <tr>
    <td>id</td>
	<td>Optional</td>
	<td>Dieses Feld enthält die UUID des Ereignisses.</td>
  </tr>
  <tr>
    <td>initiator.id</td>
	<td>Erforderlich</td>
	<td>Dieses Feld enthält die ID für die Quelle des Ereignisses (z. B. eine Instanz-ID).</td>
  </tr>
  <tr>
    <td>initiator.name</td>
	<td>Optional</td>
	<td>Dieses Feld stellt einen lesbaren Namen für die Quelle des Ereignisses bereit (z. B. eine Benutzer-ID).</td>
  </tr>
  <tr>
    <td>initiator.typeURI</td>
	<td>Erforderlich</td>
	<td>Dieses Feld gibt den Typ der Ereignisquelle an (z. B. *service/security/account/user*).</td>
  </tr>
  <tr>
    <td>initiator.host.agent</td>
	<td>Optional</td>
	<td>Dieses Feld gibt den Client an, der zum Senden der Anforderung verwendet wurde (z. B. *python-neutronclient*) oder Browserinformationen.</td>
  </tr>
  <tr>
    <td>initiator.host.address</td>
	<td>Optional</td>
	<td>Dieses Feld enthält die IP-Adresse des Initiators.</td>
  </tr>
  <tr>
    <td>target.id</td>
	<td>Erforderlich</td>
	<td>Dieses Feld enthält die ID des Zielservice.</td>
  </tr>
  <tr>
    <td>target.name</td>
	<td>Erforderlich</td>
	<td>Dieses Feld enthält den lesbaren Namen des Zielservice (z. B. *ibm-key-protect*).</td>
  </tr>
  <tr>
    <td>target.typeURI</td>
	<td>Erforderlich</td>
	<td>Dieses Feld enthält den Typ des Ereignisziels (z. B. *service/ibm-key-protect/secrets*).</td>
  </tr>
  <tr>
    <td>target.host.address</td>
	<td>Optional</td>
	<td>Dieses Feld enthält die IP-Adresse oder URL des Zielservice (z. B. *xxx.bluemix.net*).</td>
  </tr>
  <tr>
    <td>observer.name</td>
	<td>Erforderlich</td>
	<td>Dieses Feld ist auf den folgenden Wert gesetzt: *ActivityTracker*.</td>
  </tr>
  <tr>
    <td>observer.id</td>
	<td>Erforderlich</td>
	<td>Dieses Feld enthält Informationen zu der Ressource, die das CADF-Ereignis erstellt und speichert (z. B. *activitytracker.ng.bluemix.net*).</td>
  </tr>
  <tr>
    <td>observer.typeURI</td>
	<td>Erforderlich</td>
	<td>Dieses Feld wird auf den folgenden Wert gesetzt: *service/security/edge/activity-tracker*.</td>
  </tr>
  <tr>
    <td>reason.reasonCode</td>
	<td>Optional</td>
	<td>Dieses Feld enthält den HTTP-Antwortcode, z. B. *200* für 'success' (Erfolg).</td>
  </tr>
  <tr>
    <td>reason.reasonType</td>
	<td>Erforderlich</td>
	<td>Dieses Feld enthält Informationen zum Ursachencode (reasonCode), wenn diese Angabe im Feld *reason.reasonCode* bereitgestellt wird.</td>
  </tr>
</table>

 

