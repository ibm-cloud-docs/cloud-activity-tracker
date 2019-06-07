---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

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
{:deprecated: .deprecated}


# Ouverture du tableau de bord Kibana
{: #launch_kibana}

Vous pouvez lancer Kibana depuis l'interface utilisateur d'{{site.data.keyword.cloudaccesstrailshort}} dans {{site.data.keyword.cloud_notm}}, ou directement depuis un navigateur Web.
{:shortdesc}
   
{{site.data.keyword.cloudaccesstrailfull}} est obsolète. A compter du 9 mai 2019, vous ne pourrez plus mettre à disposition de nouvelles instances {{site.data.keyword.cloudaccesstrailshort}}. Les instances de plan existantes sont prises en charge jusqu'au 30 septembre 2019. Pour continuer à surveiller l'activité de votre compte {{site.data.keyword.cloud_notm}}, mettez à disposition une instance du [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}


##  Ouverture de Kibana depuis le tableau de bord du service Activity Tracker
{: #launch_Kibana_from_at}

Les journaux d'activité qu'affiche Kibana incluent les événements de toutes les ressources déployées dans l'espace de l'organisation {{site.data.keyword.cloud_notm}} à laquelle vous êtes connecté et où le service {{site.data.keyword.cloudaccesstrailshort}} est à disposition.

Effectuez les étapes suivantes pour lancer Kibana depuis le tableau de bord du service {{site.data.keyword.cloudaccesstrailshort}} :

1. Connectez-vous à votre compte {{site.data.keyword.cloud_notm}}.

    Le tableau de bord {{site.data.keyword.cloud_notm}} se trouve à l'adresse suivante : [https://cloud.ibm.com/login ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/login){:new_window}.
    
	Après que vous vous êtes connecté avec votre ID utilisateur et votre mot de passe, l'interface utilisateur {{site.data.keyword.cloud_notm}} s'ouvre.

2. Sélectionnez le service {{site.data.keyword.cloudaccesstrailshort}} à partir du tableau de bord {{site.data.keyword.cloud_notm}}. 
    
3. Sélectionnez l'onglet **Géré**.

4. Pour afficher les événements d'espace, sélectionnez **Journaux d'espace** pour la zone *Afficher les journaux*. **Remarque :** Il s'agit de la vue par défaut. Cliquez ensuite sur **Afficher dans Kibana**. 

    Le tableau de bord Kibana s'ouvre. Le tableau de bord **ActivityTracker_Space_Dashboard_in_24h** se charge avec un filtre temporel défini sur les dernières 24 heures.

5. Pour afficher les événements de compte, sélectionnez **Journaux de compte** pour la zone *Afficher les journaux*. Cliquez ensuite sur **Afficher dans Kibana**. 

    Le tableau de bord **ActivityTracker_Account_Dashboard_in_24h** se charge avec un filtre temporel défini sur les dernières 24 heures.
	
	
##  Ouverture de Kibana depuis un navigateur Web
{: #launch_Kibana_from_browser}

Pour lancer Kibana depuis un navigateur, procédez comme suit :

1. Ouvrez un navigateur Web et lancez Kibana dans la région dont vous souhaitez surveiller les événements. Ensuite, connectez-vous à l'interface utilisateur Kibana.
    
    Par exemple, le tableau suivant indique l'adresse URL que vous devez utiliser pour lancer Kibana par région :
      
    <table>
          <caption>Tableau 1. URL permettant de lancer Kibana par région</caption>
           <tr>
            <th>Région</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>Allemagne</td>
            <td>`https://logging.eu-fra.bluemix.net`</td>
          </tr>
          <tr>
            <td>Sydney</td>
            <td>`https://logging.au-syd.bluemix.net` </td>
          </tr>
		  <tr>
            <td>Royaume-Uni</td>
            <td>`https://logging.eu-gb.bluemix.net`</td>
          </tr>
		  <tr>
            <td>Sud des Etats-Unis</td>
            <td>`https://logging.ng.bluemix.net`</td>
          </tr>
    </table>
	
	La page Discover s'ouvre dans Kibana.
	
2. Vérifiez que vous êtes connecté au compte {{site.data.keyword.cloud_notm}} dont vous voulez afficher et analyser les événements d'activité.

3. Affichez les événements d'espace ou de compte

* Cliquez en haut à droite de la fenêtre Kibana où sont affichées vos informations de connexion.
* Dans **Domain**, sélectionnez l'espace ou le compte dans la liste déroulante.
* Pour les événements d'espace, sélectionnez l'**espace** qui vous intéresse dans la liste déroulante Space.
* Pour les événements de compte, sélectionnez le **compte** correct dans la liste déroulante Account.

4. Ajustez la période de recherche

* Par défaut, la période de recherche de Kibana est définie sur les 15 dernières minutes.
* Cliquez sur `Last 15 minutes` sur la barre grise en haut à droite.
* Sélectionnez jusqu'où remonter pour voir les événements. Les événements des 3 derniers jours peuvent faire l'objet d'une recherche. Sélectionnez une période inférieure ou égale à 3 jours.

5. Filtrez les événements pour n'afficher que les événements Activity Tracker
* Vous pourrez n'obtenir que des événements de journaux et des événements Activity Tracker lorsque vous les visualisez directement dans Kibana.
* Sur la barre de recherche, entrez `type:ActivityTracker` pour afficher uniquement les événements Activity Tracker.

Les événements que vous voyez dans Kibana correspondent aux événements hébergés dans le domaine sélectionné dans la région où vous avez lancé Kibana.

## Limitations
{: #launch_kibana_limitations}

* En raison de limitations dans Kibana, vous ne pouvez pas ouvrir simultanément plusieurs onglets de navigateur Kibana dans la même session pour afficher différents espaces ou comptes. Par conséquent, si vous avez deux sessions ou plus ouvertes en même temps et que vous modifiez le domaine d'espace à compte, ou inversement, vous risquez d'être confronté à des problèmes.
* Par défaut, seul le propriétaire du compte peut afficher les événements de compte. Pour permettre à d'autres personnes de voir les événements de compte, suivez les instructions indiquées dans [Affichage d'événements de compte](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-view_acc_events#view_acc_events).



