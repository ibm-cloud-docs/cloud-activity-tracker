---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, IAM

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


# Octroi de droits pour l'affichage des événements
{: #grant_permissions}

Dans {{site.data.keyword.cloud}}, vous pouvez affecter des rôles Cloud Foundry et/ou des rôles IAM à un utilisateur. Ces rôles définissent les tâches qu'un utilisateur peut effectuer lorsque vous utilisez le service {{site.data.keyword.cloudaccesstrailshort}}.  
{:shortdesc}

## Octroi de droits pour la consultation des événements de compte
{: #grant_acc_events}

Accordez les droits suivants à un utilisateur pour afficher les événements de compte dans une région :

1. Rôle *Développeur* dans un espace de la région où {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition. 

    Pour plus d'informations, voir [Octroi d'un rôle CF](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role).

2. Règle IAM pour le service {{site.data.keyword.loganalysisshort}} avec le rôle *Afficheur* dans la région. 

    Le rôle d'afficheur est le rôle IAM minimal requis. 
	
	Pour plus d'informations, voir [Octroi de droits IAM](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_iam_policy).


## Octroi de droits pour la consultation des événements d'espace
{: #grant_space_events}

Accordez le droit suivant à un utilisateur pour afficher les événements d'espace dans une région :

* Rôle *Développeur* dans l'espace de la région où {{site.data.keyword.cloudaccesstrailshort}} est mis à disposition. 

    Pour plus d'informations, voir [Octroi d'un rôle CF](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-grant_permissions#grant_cf_role).


## Octroi de droits IAM
{: #grant_iam_policy}

Pour accorder un rôle IAM à un utilisateur, tenez compte des informations suivantes :

* Vous devez être autorisé à affecter des règles à d'autres utilisateurs dans le compte, ou vous devez être le propriétaire du compte. Si vous n'êtes pas le propriétaire du compte, vous devez disposer d'une règle IAM dotée du rôle **Administrateur** pour le service {{site.data.keyword.loganalysisshort}}.

* Lorsque vous définissez une règle, les régions que vous spécifiez définissent les régions auxquelles un utilisateur peut accéder pour afficher des événements de domaine de compte.

Procédez comme suit pour accorder à un utilisateur le droit d'afficher des événements à partir d'un domaine de compte :

1. [Connectez-vous à la console {{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/login){:new_window}.
	
	Après que vous vous êtes connecté avec votre ID utilisateur et votre mot de passe, l'interface utilisateur {{site.data.keyword.cloud_notm}} s'ouvre.

2. Dans la barre de menus, cliquez sur **Gérer > Compte > Utilisateurs**. 

    La fenêtre *Utilisateurs* affiche une liste d'utilisateurs avec leur adresse électronique pour le compte actuellement sélectionné.
	
3. Si l'utilisateur est membre du compte, sélectionnez le nom de l'utilisateur dans la liste ou cliquez sur **Gérer un utilisateur** dans le menu *Actions*.

    Si l'utilisateur n'est pas membre du compte, voir [Invitation d'utilisateurs](/docs/iam?topic=iam-iamuserinv#iamuserinv).

4. Dans la section **Règles d'accès**, cliquez sur **Affecter un accès**, puis cliquez sur **Affecter l'accès aux ressources**.

    La fenêtre *Affecter l'accès à la ressource à (nom de l'utilisateur)** s'ouvre.

5. Entrez les informations concernant la règle. Le tableau ci-dessous répertorie les zones requises pour définir une règle. 

    <table>
	  <caption>Liste des zones de configuration d'une règle IAM.</caption>
	  <tr>
	    <th>Zone</th>
		<th>Valeur</th>
	  </tr>
	  <tr>
	    <td>Services</td>
		<td>*IBM Cloud Log Analysis*</td>
	  </tr>	  
	  <tr>
	    <td>Régions</td>
		<td>Vous pouvez spécifier les régions dans lesquelles l'utilisateur disposera des droits permettant d'utiliser les événements. Sélectionnez ou une plusieurs régions individuellement, ou sélectionnez **Toutes les régions en cours** pour accorder l'accès à toutes les régions.</td>
	  </tr>
	  <tr>
	    <td>Instance de service</td>
		<td>Sélectionnez *Toutes les instances de service*.</td>
	  </tr>
	  <tr>
	    <td>Rôles</td>
		<td>Sélectionnez un ou plusieurs rôles IAM. <br>Les rôles valides sont *administrateur*, *opérateur*, *éditeur* et *afficheur*.</td>
	  </tr>
     </table>
	
6. Cliquez sur **Affecter**.
	
La règle que vous configurez est applicable aux régions sélectionnées. 


## Octroi d'un rôle CF
{: #grant_cf_role}

Pour accorder un rôle CF à un utilisateur, tenez compte des informations suivantes :

* Vous devez disposer de droits dans l'organisation et l'espace qui permettent d'attribuer à l'utilisateur un rôle Cloud Foundry. 

* Seul le rôle **Développeur** permet à un utilisateur d'afficher des événements.

Procédez comme suit pour permettre à un utilisateur d'afficher les événements d'un espace :

1. [Connectez-vous à la console {{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/login){:new_window}.
	
	Après que vous vous êtes connecté avec votre ID utilisateur et votre mot de passe, l'interface utilisateur {{site.data.keyword.cloud_notm}} s'ouvre.

2. Dans la barre de menus, cliquez sur **Gérer > Compte > Utilisateurs**. 

    La fenêtre *Utilisateurs* affiche une liste d'utilisateurs avec leur adresse électronique pour le compte actuellement sélectionné.
	
3. Si l'utilisateur est membre du compte, sélectionnez le nom de l'utilisateur dans la liste ou cliquez sur **Gérer un utilisateur** dans le menu *Actions*.

    Si l'utilisateur n'est pas membre du compte, voir [Invitation d'utilisateurs](/docs/iam?topic=iam-iamuserinv#iamuserinv).

4. Sélectionnez **Accès Cloud Foundry**. Sélectionnez ensuite l'organisation.

    Les espaces disponibles dans cette organisation sont répertoriés.

5. Choisissez un espace. Puis, dans l'action de menu, sélectionnez **Editer un rôle d'espace**.

6. Sélectionnez **Développeur**.
	
7. Cliquez sur **Sauvegarder un rôle**.




