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


# Accès au tableau de bord Kibana
{: #launch_kibana}

Vous pouvez lancer Kibana depuis l'interface utilisateur d'{{site.data.keyword.cloudaccesstrailshort}} dans {{site.data.keyword.Bluemix}} ou directement depuis un navigateur Web.
{:shortdesc}
   

##  Accès à Kibana depuis le tableau de bord du service Activity Tracker
{: #launch_Kibana_from_at}

Les journaux d'activité qu'affiche Kibana incluent les événements de toutes les ressources déployées dans l'espace de l'organisation {{site.data.keyword.Bluemix_notm}} à laquelle vous êtes connecté et où le service {{site.data.keyword.cloudaccesstrailshort}} est à disposition.

Effectuez les étapes suivantes pour lancer Kibana depuis le tableau de bord du service {{site.data.keyword.cloudaccesstrailshort}} :

1. Connectez-vous à votre compte {{site.data.keyword.Bluemix_notm}}.

    Le tableau de bord {{site.data.keyword.Bluemix_notm}} se trouve à l'adresse suivante : [http://bluemix.net ![External link icon](../../../../icons/launch-glyph.svg "External link icon")](http://bluemix.net){:new_window}.
    
	Après que vous vous êtes connecté avec votre ID utilisateur et votre mot de passe, l'interface utilisateur {{site.data.keyword.Bluemix_notm}} s'ouvre.

2. Sélectionnez le service {{site.data.keyword.cloudaccesstrailshort}} à partir du tableau de bord {{site.data.keyword.Bluemix_notm}}. 
    
3. Sélectionnez l'onglet **Géré**.

4. Cliquez sur **Vue avancée**. 

    Le tableau de bord Kibana s'ouvre.

Par défaut, le tableau de bord **ActivityTracker_Space_Dashboard_in_24h** se charge ainsi qu'un filtre de temps défini sur les dernières 24 heures. 


	
	
##  Accès à Kibana depuis un navigateur Web
{: #launch_Kibana_from_browser}

Les informations de journal qu'affiche Kibana incluent les événements de toutes les ressources déployées dans l'espace de l'organisation {{site.data.keyword.Bluemix_notm}} à laquelle vous êtes connecté.

Pour lancer Kibana depuis un navigateur, procédez comme suit :

1. Ouvrez un navigateur Web et lancez Kibana. Ensuite, connectez-vous à l'interface utilisateur Kibana.
    
    Par exemple, le tableau suivant indique l'adresse URL que vous devez utiliser pour lancer Kibana par région :
      
    <table>
          <caption>Tableau 1. URL permettant de lancer Kibana par région</caption>
           <tr>
            <th>Région</th>
            <th>URL</th>
          </tr>
          <tr>
            <td>Sud des Etats-Unis</td>
            <td>[https://logging.ng.bluemix.net](https://logging.ng.bluemix.net) </td>
          </tr>
		  <tr>
            <td>Royaume-Uni</td>
            <td>[https://logmet.eu-gb.bluemix.net](https://logmet.eu-gb.bluemix.net)</td>
          </tr>
    </table>
	
	La page Discover s'ouvre dans Kibana.
	
2. Vérifiez que vous êtes connecté au compte, à l'organisation et à l'espace {{site.data.keyword.Bluemix_notm}} dont vous voulez afficher et analyser les journaux d'activité.

    Vous pouvez afficher les événements et les journaux disponibles dans l'espace auquel vous êtes connecté.

3. Pour filtrer les événements, sélectionnez **Ouvrir** dans la barre de menus.

    La liste des tableaux de bord sauvegardés s'affiche.
	
4. Pour afficher les événements pour l'espace auquel vous êtes connecté, sélectionnez **ActivityTracker_Space_Dashboard_in_24h**.


##   Limitations
{: #limitations}

 En raison de limitations dans Kibana, vous ne pouvez pas ouvrir simultanément plusieurs onglets de navigateur Kibana dans la même session pour afficher différents espaces ou comptes. Par conséquent, si vous avez deux sessions ou plus ouvertes en même temps et que vous modifiez le domaine d'espace à compte, ou inversement, vous risquez d'être confronté à des problèmes.
	



