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


# Berechtigungen zum Anzeigen von Ereignissen erteilen
{: #grant_permissions}

In {{site.data.keyword.Bluemix}} können Sie einem Benutzer Cloud Foundry-Rollen, IAM-Rollen oder beide Typen von Rollen zuweisen. Diese Rollen definieren, welche Tasks ein Benutzer beim Arbeiten mit dem {{site.data.keyword.cloudaccesstrailshort}}-Service ausüben kann.  
{:shortdesc}

## Berechtigungen zum Anzeigen von Ereignissen für ein Konto erteilen
{: #grant_acc_events}

Erteilen Sie einem Benutzer die folgenden Berechtigungen, damit er Ereignisse für ein Konto in einer Region anzeigen kann:

1. Rolle *Entwickler* in einem Bereich (Space) der Region, in der {{site.data.keyword.cloudaccesstrailshort}} bereitgestellt wird. 

    Weitere Informationen finden Sie in [CF-Rolle erteilen](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role).

2. IAM-Richtlinie für den {{site.data.keyword.loganalysisshort}}-Service mit der Rolle *Anzeigeberechtigter* (Viewer) in der Region. 

    Die Rolle des Anzeigeberechtigten ist die erforderliche minimale IAM-Rolle. 
	
	Weitere Informationen finden Sie im Abschnitt [IAM-Berechtigungen erteilen](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_iam_policy).


## Berechtigungen zum Anzeigen von Ereignissen für einen Bereich (Space) erteilen
{: #grant_space_events}

Erteilen Sie einem Benutzer die folgende Berechtigung, damit er Ereignisse für einen Bereich (Space) in einer Region anzeigen kann:

* Rolle *Entwickler* in dem Bereich (Space) der Region, in der {{site.data.keyword.cloudaccesstrailshort}} bereitgestellt wird. 

    Weitere Informationen finden Sie in [CF-Rolle erteilen](/docs/services/cloud-activity-tracker/how-to/grant_permissions.html#grant_cf_role).


## IAM-Berechtigungen erteilen
{: #grant_iam_policy}

Wenn Sie einem Benutzer eine IAM-Rolle zuordnen möchten, berücksichtigen Sie die folgenden Informationen:

* Sie müssen über die Berechtigung zum Zuweisen von Richtlinien zu anderen Benutzern im Konto verfügen oder Sie müssen der Kontoeigner sein. Wenn Sie nicht der Kontoeigner sind, müssen Sie über eine IAM-Richtlinie mit der Rolle **Administrator** für den {{site.data.keyword.loganalysisshort}}-Service verfügen.

* Wenn Sie eine Richtlinie definieren, so definieren Sie durch die Regionen, die Sie angeben, in welchen Regionen ein Benutzer Zugriff zum Anzeigen von Domänenereignissen erteilt wird.

Führen Sie die folgenden Schritte aus, um einem Benutzer Berechtigungen zum Anzeigen von Ereignissen einer Kontodomäne zu erteilen:

1. Melden Sie sich bei der {{site.data.keyword.cloud_notm}}-Konsole an.

    Öffnen Sie einen Web-Browser und starten Sie das {{site.data.keyword.cloud_notm}}-Dashboard: [http://bluemix.net ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](http://bluemix.net){:new_window}
	
	Nachdem Sie sich mit Ihrer Benutzer-ID und Ihrem Kennwort angemeldet haben, wird die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle geöffnet.

2. Klicken Sie in der Menüleiste auf **Verwalten > Konto > Benutzer**. 

    Im Fenster *Benutzer* wird eine Liste der Benutzer für das gegenwärtig ausgewählte Konto mit den zugehörigen E-Mail-Adressen angezeigt.
	
3. Wenn der Benutzer ein Mitglied des Kontos ist, wählen Sie den zugehörigen Benutzernamen aus der Liste aus oder klicken Sie auf im Menü *Aktionen* auf die Option **Benutzer verwalten**.

    Wenn der Benutzer nicht Mitglied des Kontos ist, lesen Sie in [Benutzer einladen](/docs/iam/iamuserinv.html#iamuserinv) nach.

4. Klicken Sie im Abschnitt **Zugriffsrichtlinien** auf **Zugriff zuweisen** und wählen Sie dann **Zugriff auf Ressourcen zuweisen** aus.

    Das Fenster *Ressourcenzugriff zuweisen zu 'Benutzername'** wird geöffnet.

5. Geben Sie Informationen zur Richtlinie ein. Die folgende Tabelle enthält eine Auflistung der Felder, die zum Definieren einer Richtlinie erforderlich sind: 

    <table>
	  <caption>Liste der Felder zum Konfigurieren einer IAM-Richtlinie</caption>
	  <tr>
	    <th>Feld</th>
		<th>Wert</th>
	  </tr>
	  <tr>
	    <td>Services</td>
		<td>*IBM Cloud Log Analysis*</td>
	  </tr>	  
	  <tr>
	    <td>Regionen</td>
		<td>Sie können die Regionen angeben, für die dem Benutzer der Zugriff auf die Arbeit mit Ereignissen erteilt wird. Wählen Sie eine oder mehrere Regionen einzeln aus oder wählen Sie die Option **Alle aktuellen Regionen** aus, um Zugriff auf alle Regionen zu erteilen.</td>
	  </tr>
	  <tr>
	    <td>Serviceinstanz</td>
		<td>Wählen Sie *Alle Serviceinstanzen* aus.</td>
	  </tr>
	  <tr>
	    <td>Rollen</td>
		<td>Wählen Sie eine oder mehrere IAM-Rollen aus. <br>Die folgenden Rollen sind gültig: *Administrator*, *Bediener* (Operator), *Bearbeiter* (Editor) und *Anzeigeberechtigter* (Viewer).</td>
	  </tr>
     </table>
	
6. Klicken Sie auf **Zuweisen**.
	
Die Richtlinie, die Sie konfigurieren, gilt für die ausgewählten Regionen. 


## CF-Rolle erteilen
{: #grant_cf_role}

Wenn Sie einem Benutzer eine CF-Rolle zuordnen möchten, berücksichtigen Sie die folgenden Informationen:

* Sie müssen über Berechtigungen in der Organisation und dem Bereich (Space) verfügen, um dem Benutzer eine Cloud-Foundry-Rolle zuweisen zu können. 

* Nur die Rolle **Entwickler** ermöglicht einem Benutzer das Anzeigen von Ereignissen.

Führen Sie die folgenden Schritte aus, um einem Benutzer den Zugriff zum Anzeigen von Ereignissen in einem Bereich (Space) zu erteilen:

1. Melden Sie sich bei der {{site.data.keyword.cloud_notm}}-Konsole an.

    Öffnen Sie einen Web-Browser und starten Sie das {{site.data.keyword.cloud_notm}}-Dashboard: [http://bluemix.net ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](http://bluemix.net){:new_window}
	
	Nachdem Sie sich mit Ihrer Benutzer-ID und Ihrem Kennwort angemeldet haben, wird die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle geöffnet.

2. Klicken Sie in der Menüleiste auf **Verwalten > Konto > Benutzer**. 

    Im Fenster *Benutzer* wird eine Liste der Benutzer für das gegenwärtig ausgewählte Konto mit den zugehörigen E-Mail-Adressen angezeigt.
	
3. Wenn der Benutzer ein Mitglied des Kontos ist, wählen Sie den zugehörigen Benutzernamen aus der Liste aus oder klicken Sie auf im Menü *Aktionen* auf die Option **Benutzer verwalten**.

    Wenn der Benutzer nicht Mitglied des Kontos ist, lesen Sie in [Benutzer einladen](/docs/iam/iamuserinv.html#iamuserinv) nach.

4. Wählen Sie **Cloud Foundry-Zugriff** aus und wählen Sie dann eine Organisation aus.

    Es wird eine Liste der in dieser Organisation verfügbaren Bereiche (Spaces) angezeigt.

5. Wählen Sie einen Bereich (Space) aus. Wählen Sie dann im Aktionsmenü die Option **Bereichsrolle bearbeiten** aus.

6. Wählen Sie **Entwickler** aus.
	
7. Klicken Sie auf **Rolle speichern**.




