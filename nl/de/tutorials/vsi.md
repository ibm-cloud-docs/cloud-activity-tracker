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


# {{site.data.keyword.BluVirtServers_short}} und {{site.data.keyword.baremetal_short}} mit {{site.data.keyword.cloudaccesstrailshort}} überwachen
{: #vsi}

In diesem Lernprogramm erfahren Sie, wie Benutzer in einem {{site.data.keyword.cloud_notm}}-Konto so konfiguriert werden, dass diese Benutzer mit {{site.data.keyword.BluVirtServers_short}} und {{site.data.keyword.baremetal_short}} erstellte Infrastrukturgeräte verwalten können und dass durch die Aktionen der Benutzer {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse generiert werden, die Sie mit {{site.data.keyword.cloudaccesstrailshort}} überwachen können.
{:shortdesc}

{{site.data.keyword.BluVirtServers}} sind skalierbare virtuelle Server, die mit dedizierten Kernen (Cores) und Speicherzuordnungen erworben werden. Sie stellen eine großartige Option dar, wenn Sie nach Rechenressourcen suchen, die in wenigen Minuten hinzugefügt werden können und Zugriff auf Features wie Imagevorlagen bieten. 
* Weitere Informationen finden Sie in [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi/vsi_about.html#about-virtual-servers).  
* Die Liste der Aktionen, durch die ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis generiert wird, finden Sie in [Von {{site.data.keyword.BluVirtServers_short}} generierte Ereignisse](/docs/vsi/vsi_activity_tracker_events.html#at_events). 

{{site.data.keyword.baremetal_short}} sind physische Single-Tenant-Server, die Ihnen Leistung und Kontrolle mit maschinennahem Zugriff auf die Hardwareressourcen bereitstellen.  
* Weitere Informationen finden Sie in [{{site.data.keyword.baremetal_long}}](/docs/bare-metal/about.html#about). 
* Die Liste der Aktionen, durch die ein {{site.data.keyword.cloudaccesstrailshort}}-Ereignis generiert wird, finden Sie in [Von {{site.data.keyword.baremetal_short}} generierte Ereignisse](/docs/bare-metal/bm-activity-tracker-events.html#at_events). 

**Damit ein Benutzer {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse für {{site.data.keyword.BluVirtServers_short}} und {{site.data.keyword.baremetal_short}} generieren kann, benötigt er Zugriff auf Infrastrukturressourcen in der IBM Cloud-Konsole.**
{: tip}

## Schritt 1: Softlayer-Konto mit einem {{site.data.keyword.cloud_notm}}-Konto verknüpfen
{: #vsi_step1}

** Zum Generieren von {{site.data.keyword.cloudaccesstrailshort}}-Ereignissen muss das Softlayer-Konto mit einem {{site.data.keyword.cloud_notm}}-Konto verknüpft sein. Weitere Informationen finden Sie in [Zur IBMid wechseln und Konten verknüpfen](/docs/account?topic=account-unifyingaccounts#link_accounts). 

Beachten Sie die folgenden Informationen, wenn Sie Ihr Softlayer-Konto mit einem {{site.data.keyword.cloud_notm}}-Konto verknüpfen: 
* Alle neuen Konten erhalten automatisch eine IBMid und vorhandene SoftLayer-Konten (mit Ausnahme von föderierten SAML-Konten) werden für den Wechsel zur IBMid-Authentifizierung aktiviert. 
* Jedes SoftLayer-Konto, das mit einem {{site.data.keyword.cloud_notm}}-Konto verknüpft werden soll, muss zu einer eindeutigen IBMid mit einer eindeutigen E-Mail-Adresse gehören. 
* Für den Wechsel von Ihrem bisherigen SoftLayer-Konto zu einer IBMid müssen Sie eine IBMid erstellen und diese anschließend mithilfe Ihres Registrierungscodes bestätigen. 
* Nachdem ein Konto auf ein IBMid-Konto umgestellt wurde, können Sie das SoftLayer-Konto und das {{site.data.keyword.cloud_notm}}-Konto verknüpfen, um die kombinierten IaaS- (Infrastructure as a Service) und PaaS-Ressourcen (Platform as a Service) zu nutzen.  

Führen Sie die folgenden Schritte aus, um ein Konto zu verknüpfen: 
1. [IBMid und Registrierungscode anfordern](/docs/account/softlayerlink.html#reqIBMidandregcode)
2. [IBMid mit dem Registrierungscode bestätigen](/docs/account/softlayerlink.html#confIBMiduseregcode)
3. [IBMid-Konto verknüpfen](/docs/account/softlayerlink.html#link_user_account)


## Schritt 2: Benutzern Infrastrukturberechtigungen erteilen
{: #vsi_step2}

**Hinweis:** Wenn Sie Berechtigungen über das *{{site.data.keyword.cloud_notm}}-Infrastrukturportal* erteilen, hat der Benutzer keinen Zugriff auf die Verwaltung von Geräten über das Dashboard für die *{{site.data.keyword.cloud_notm}}-Infrastruktur* und es werden keine {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse generiert. **Sie müssen einem Benutzer Infrastrukturberechtigungen über das {{site.data.keyword.cloud_notm}}-Konto erteilen, um Geräte zu verwalten. Durch diese Aktionen werden {{site.data.keyword.cloudaccesstrailshort}}-Ereignisse generiert.**
{: tip}

Führen Sie die folgenden Schritte aus, um einem Benutzer Infrastrukturberechtigungen zu erteilen: 

1. Melden Sie sich bei {{site.data.keyword.cloud_notm}} an.

    Das {{site.data.keyword.cloud_notm}}-Dashboard finden Sie unter [http://bluemix.net ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](http://bluemix.net){:new_window}. 
    
	Nachdem Sie sich mit Ihrer Benutzer-ID und Ihrem Kennwort angemeldet haben, wird die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle geöffnet.

2. Klicken Sie in der Menüleiste auf **Verwalten** &gt; **Konto** und wählen Sie anschließend **Benutzer** aus.  

3. Wählen Sie einen Benutzer aus, dem Sie Berechtigungen zum Arbeiten mit Geräten erteilen möchten. 

4. Wählen Sie **Zugriff zuweisen** aus. 

5. Wählen Sie **Zugriff auf Ihr Softlayer-Konto zuweisen** aus. Das {{site.data.keyword.cloud_notm}}-Infrastrukturportal wird im Kontext der {{site.data.keyword.cloud_notm}} geöffnet. 

6. Legen Sie die Berechtigungen fest, die dem Benutzer für die Verwaltung von Geräten erteilt werden sollen. Wählen Sie **Portalberechtigungen** aus. Erteilen Sie dem Benutzer dann im Abschnitt **Geräte** die Berechtigungen, die er für die Verwaltung von Geräten benötigt. Beispiele: *Details zu virtuellen Servern anzeigen*, *Warmstart für den Server durchführen und IPMI-Systeminformationen anzeigen*, *Upgrades für Server durchführen* oder *Betriebssystem erneut laden und Rescue-Kernel initiieren*. 

7. Speichern Sie die Portalberechtigungen. Wenn Sie **Gerätezugriff** auswählen, werden Sie aufgefordert, die Änderungen zu speichern. Klicken Sie auf **Speichern**.

8. Legen Sie die Geräte fest, die der Benutzer verwalten kann. Wählen Sie im Abschnitt **Gerätezugriff** die physischen Geräte aus. Klicken Sie dann auf **Gerätezugriff aktualisieren**. 






