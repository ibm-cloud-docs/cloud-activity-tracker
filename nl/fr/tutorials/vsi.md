---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-01"

keywords: IBM Cloud, Activity Tracker, VSI events, tutorial

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


# Surveillance des serveurs {{site.data.keyword.BluVirtServers_short}} et {{site.data.keyword.baremetal_short}} avec {{site.data.keyword.cloudaccesstrailshort}}
{: #vsi}

Utilisez ce tutoriel pour apprendre à configurer des utilisateurs dans un compte {{site.data.keyword.cloud_notm}} pour que vous puissiez surveiller les événements {{site.data.keyword.cloudaccesstrailshort}} générés par ces utilisateurs lorsqu'ils utilisent des serveurs {{site.data.keyword.BluVirtServers_short}} et {{site.data.keyword.baremetal_short}}.
{:shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} est obsolète. A compter du 9 mai 2019, vous ne pourrez plus mettre à disposition de nouvelles instances {{site.data.keyword.cloudaccesstrailshort}}. Les instances de plan existantes sont prises en charge jusqu'au 30 septembre 2019. Pour continuer à surveiller l'activité de votre compte {{site.data.keyword.cloud_notm}}, mettez à disposition une instance du [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

Les serveurs {{site.data.keyword.BluVirtServers}} sont des serveurs virtuels évolutifs qui sont achetés avec des coeurs dédiés et des allocations de mémoire. Ils constituent un très bon choix si vous recherchez des ressources de calcul, qui peuvent être ajoutées en quelques minutes, avec un accès à des fonctions telles que des modèles d'image. 
* Pour plus d'informations, voir [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers). 
* Pour obtenir la liste des actions qui génèrent un événement {{site.data.keyword.cloudaccesstrailshort}}, voir [Evénements générés par {{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-at_events#at_events).

Les serveurs {{site.data.keyword.baremetal_short}} sont des serveurs physiques à service exclusif, offrant performance et contrôle avec un accès de bas niveau aux ressources matérielles. 
* Pour plus d'informations, voir [{{site.data.keyword.baremetal_long}}](/docs/bare-metal?topic=bare-metal-about#about).
* Pour obtenir la liste des actions qui génèrent un événement {{site.data.keyword.cloudaccesstrailshort}}, voir [Evénements générés par {{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-bm-at-events#bm-at-events).

**Pour pouvoir générer des événements {{site.data.keyword.cloudaccesstrailshort}} pour les serveurs {{site.data.keyword.BluVirtServers_short}} et {{site.data.keyword.baremetal_short}}, l'utilisateur doit avoir accès aux ressources d'infrastructure dans la console IBM Cloud.**
{: tip}

## Etape 1. Liaison du compte Softlayer à un compte {{site.data.keyword.cloud_notm}}
{: #vsi_step1}

** Pour générer des événements {{site.data.keyword.cloudaccesstrailshort}}, le compte Softlayer doit être lié à un compte {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [Passage à l'IBMid et liaison des comptes](/docs/account?topic=account-unifyingaccounts#link_accounts).

Tenez compte des informations suivantes lorsque vous liez votre compte Softlayer à un compte {{site.data.keyword.cloud_notm}} :
* Tous les nouveaux comptes reçoivent automatiquement un IBMid et les comptes SoftLayer existants, à l'exception des comptes fédérés SAML, sont activés pour passer à l'authentification par IBMid.
* Chaque compte SoftLayer que vous prévoyez de lier à un compte {{site.data.keyword.cloud_notm}} doit appartenir à un IBMid unique associé à une adresse électronique unique.
* Pour faire basculer votre compte SoftLayer existant vers un IBMid, vous devez créez un IBMid, puis utiliser votre code d'enregistrement pour le confirmer.
* Une fois qu'un compte a basculé sur un compte IBMid, vous pouvez lier le compte SoftLayer et le compte {{site.data.keyword.cloud_notm}} pour utiliser une combinaison de ressources IaaS (infrastructure sous forme de services) et de ressources PaaS (plateforme sous forme de services). 

Pour lier un compte, procédez comme suit :
1. [Demandez un IBMid et un code d'enregistrement](/docs/account?topic=account-unifyingaccounts#reqIBMidandregcode)
2. [Confirmez votre IBMid avec le code d'enregistrement](/docs/account?topic=account-unifyingaccounts#confIBMiduseregcode)
3. [Effectuez la liaison de votre compte IBMid](/docs/account?topic=account-unifyingaccounts#link_user_account)


## Etape 2. Octroi de droits d'infrastructure aux utilisateurs
{: #vsi_step2}

**Remarque :** Si vous octroyez des droits à partir du *portail de l'infrastructure {{site.data.keyword.cloud_notm}}*, l'utilisateur n'a pas accès au tableau de bord d'*infrastructure {{site.data.keyword.cloud_notm}}* pour gérer les périphériques et les événements {{site.data.keyword.cloudaccesstrailshort}} ne sont pas générés. **Vous devez octroyer un droit d'infrastructure à l'utilisateur via le compte {{site.data.keyword.cloud_notm}} pour gérer les périphériques. Ces actions génèrent des événements {{site.data.keyword.cloudaccesstrailshort}}.**
{: tip}

Pour octroyer un droit d'infrastructure à l'utilisateur, procédez comme suit :

1. [Connectez-vous à {{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/login){:new_window}.
    
	Après que vous vous êtes connecté avec votre ID utilisateur et votre mot de passe, l'interface utilisateur {{site.data.keyword.cloud_notm}} s'ouvre.

2. Dans la barre de menus, cliquez sur **Gérer** &gt; **Compte**, puis sélectionnez **Utilisateurs**. 

3. Choisissez un utilisateur auquel vous souhaitez octroyer des droits de gestion des périphériques.

4. Sélectionnez **Affecter un accès**.

5. Sélectionnez **Affecter l'accès à votre compte Softlayer**. Le portail d'infrastructure {{site.data.keyword.cloud_notm}} s'ouvre dans le contexte d'{{site.data.keyword.cloud_notm}}.

6. Définissez les droits que vous souhaitez octroyer à l'utilisateur pour gérer les périphériques. Sélectionnez **Autorisations du portail**. Puis, dans la section **Périphériques**, octroyez à l'utilisateur les droits dont il a besoin pour gérer les périphériques. Vous pouvez, par exemple, modifier les droits pour `Afficher les détails du serveur virtuel`, `Réamorcer le serveur et afficher les informations système IPMI`, `Mettre à niveau un serveur` ou `Recharger le système d'exploitation et initier le noyau de secours`.

7. Sauvegardez les droits d'accès au portail. Lorsque vous sélectionnez **Accès Terminal**, vous êtes invité à sauvegarder les modifications. Cliquez sur **Sauvegarder**.

8. Définissez les périphériques que l'utilisateur peut gérer. Dans la section **Accès Terminal**, sélectionnez les périphériques physiques. Cliquez ensuite sur **Mettre à jour l'accès à l'unité**.






