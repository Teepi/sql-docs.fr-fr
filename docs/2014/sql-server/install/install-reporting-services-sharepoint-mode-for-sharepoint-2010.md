---
title: Installer Reporting Services en Mode SharePoint pour SharePoint 2010 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 47efa72e-1735-4387-8485-f8994fb08c8c
caps.latest.revision: 41
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 624f7347d4fdcbdf617e314ba398455b3f4b8126
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37313169"
---
# <a name="install-reporting-services-sharepoint-mode-for-sharepoint-2010"></a>Installer le mode SharePoint de Reporting Services pour SharePoint 2010
  Les procédures de cette rubrique constituent un guide d'installation sur serveur unique d'un serveur de rapports Reporting Services en mode SharePoint. Ces étapes comprennent l'exécution de l'assistant Installation de SQL Server ainsi que des tâches de configuration supplémentaires qui utilisent l'Administration centrale de SharePoint 2010. La rubrique peut également être utilisée pour des procédures individuelles dans le cadre d'une installation existante, par exemple, pour créer une application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Pour plus d’informations sur l’ajout de supplémentaires [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] serveurs à une batterie existante, consultez [ajouter un serveur de rapports supplémentaire à une batterie de serveurs &#40;SSRS Scale-out&#41; ](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md) et [ajouter un Web Reporting Services supplémentaires Serveur frontal à une batterie de serveurs](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010|  
  
 Une installation de serveur unique est utile pour les scénarios de développement et de tests mais n'est pas recommandée pour les environnements de production.  
  
> [!NOTE]  
>  Pour plus d’informations sur la mise à niveau et qui n’existe [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation d’en mode SharePoint vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], consultez [mise à niveau et migrer Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  

  
##  <a name="bkmk_prereq"></a> Conditions préalables  
  
-   > [!IMPORTANT]  
    >  Le gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] n'est plus nécessaire ou pris en charge pour configurer et administrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint. Utilisez l'Administration centrale pour configurer un serveur de rapports en mode SharePoint. Pour plus d’informations, consultez [gérer une Application de Service Reporting Services SharePoint](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).  
  
-   Consultez les rubriques suivantes pour connaître les conditions requises, y compris les produits SharePoint 2010 :  
  
    -   [Notes de publication en ligne](https://msdn.microsoft.com/library/dn169381.aspx)
  
    -   [Instructions d’utilisation des fonctionnalités BI de SQL Server dans une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
-   Cette rubrique ne traite pas de l'installation des produits SharePoint 2010. Pour plus d’informations, consultez [des conseils pour l’utilisation des fonctionnalités SQL Server BI dans une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md).  
  
-   Ces procédures permettent de configurer un serveur de rapports [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et ne fonctionnent pas pour les versions précédentes du serveur de rapports. Les versions antérieures du serveur de rapports n'utilisaient pas l'architecture de service partagé SharePoint. Par exemple, les serveurs de rapports SQL Server 2008 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et les serveurs de rapports SQL Server 2008 R2 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
-   Vérifiez le **Administration SharePoint 2010** service est démarré dans le Gestionnaire de serveur Windows.  
  
 ![Composants SSRS sur une installation 1 server](../../../2014/sql-server/install/media/rs-deployment-1-server.gif "composants SSRS sur une installation 1 server")  
  
### <a name="database-considerations-for-a-single-server-configuration"></a>Considérations relatives aux bases de données pour la configuration d'un serveur unique  
  
-   Les produits et technologies SharePoint et Reporting Services utilisent des bases de données relationnelles SQL Server pour stocker les données d'application.  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] requiert une instance compatible d'édition d'évaluation de SQL Server du moteur SQL.  
  
-   Les produits SharePoint peuvent utiliser une instance de base de données existante. Si une instance du moteur de base de données n’est pas installée, le programme d’installation de produits SharePoint installe SQL Server Express Edition pour les bases de données SharePoint.  
  
-   L'instance de serveur de rapports ne peut pas utiliser l'édition SQL Server Express pour sa base de données. Toutefois, l'instance de l'édition SQL Server Express qui est installée par le produit SharePoint peut exister côte à côte avec d'autres éditions du moteur de base de données.  
  

  
##  <a name="bkmk_install_SSRS"></a> Installer le serveur de rapports Reporting Services en mode SharePoint  
  
1.  Exécutez l'Assistant Installation de SQL Server.  
  
2.  Cliquez sur **Installation** dans la partie gauche de l'Assistant, puis cliquez sur **Nouvelle installation autonome SQL Server ou ajout de fonctionnalités à une installation existante**.  
  
3.  Cliquez sur **OK** dans la page **Règles de support du programme d'installation** , si toutes les règles sont passées.  
  
4.  Cliquez sur **Installer** dans la page **Fichiers de support du programme d'installation** .  
  
5.  Cliquez sur **suivant** une fois que les fichiers de support sont installés et les règles de support affichent l’état **transmis**. Examinez tout avertissement ou problème bloquant.  
  
6.  Sur le **clé de produit** page, tapez votre clé ou acceptez la valeur par défaut de l’édition « Enterprise Evaluation ».  
  
     Cliquez sur **Suivant**.  
  
7.  Lisez et acceptez les termes du contrat de licence. Microsoft vous remercie d'accepter d'envoyer des données d'utilisation des fonctionnalités dans le but d'améliorer ces fonctionnalités et la prise en charge.  
  
     Cliquez sur **Suivant**.  
  
8.  Sélectionnez **Installation de fonctionnalités SQL Server** sur le **rôle d’installation** page.  
  
     Cliquez sur **Suivant**.  
  
     ![Installation des fonctionnalités SQL Server pour le rôle d’installation](../../../2014/sql-server/install/media/rs-setuprole.gif "Installation des fonctionnalités SQL Server pour le rôle d’installation")  
  
9. Sélectionnez ce qui suit dans la page **Sélection de fonctionnalités** :  
  
    -   **Reporting Services – SharePoint**  
  
    -   **Reporting Services-complément pour les produits SharePoint 2010**. ![Remarque](../../../2014/reporting-services/media/rs-fyinote.png "Remarque")l’option de l’Assistant installation pour installer le complément est une nouveauté avec le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mise en production.  
  
    -   Si vous n’avez pas déjà une instance de SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)], vous pouvez également sélectionner **Services moteur de base de données** et **outils d’administration complets** pour un environnement complet.  
  
     Cliquez sur **Suivant**.  
  
     ![Sélection des fonctionnalités SSRS pour le mode SharePoint](../../../2014/sql-server/install/media/rs-setupfeatureselection-sharepoint-with-circles.gif "sélection des fonctionnalités SSRS pour le mode SharePoint")  
  
10. Cliquez sur **suivant** sur le **règles d’Installation** page. Examinez tout avertissement ou problème bloquant.  
  
11. Si vous avez sélectionné les services de moteur de base de données, acceptez l'instance par défaut de **MSSQLSERVER** dans la page **Configuration de l'instance** et cliquez sur **Suivant**. L'architecture de service partagé de Reporting Services n'est pas basée sur une « instance » SQL Server comme l'était la précédente architecture de Reporting Services.  
  
12. Examinez la page **Espace disque nécessaire** et cliquez sur **Suivant**.  
  
13. Sur le **Configuration du serveur** page type des informations d’identification appropriées. Si vous souhaitez utiliser les fonctionnalités de données d'alerte ou d'abonnement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous devez modifier le **Type de démarrage** de SQL Server Agent en **automatique**.  
  
     Cliquez sur **Suivant**.  
  
14. Si vous avez sélectionné les services de moteur de base de données, la page **Configuration du moteur de base de données** s'affiche où vous pouvez ajouter les comptes appropriés à la liste des administrateurs SQL puis cliquer sur **Suivant**.  
  
15. Dans la page **Configuration de Reporting Services** , l'option **Installer uniquement** devrait être sélectionnée. Cette option installe les fichiers de serveur de rapports et ne configure pas l’environnement SharePoint pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Lors de l’installation de SQL Server est terminée, suivez les autres sections de cette rubrique pour configurer l’environnement SharePoint. Cela inclut l'installation du service partagé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et la création des applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
     ![rs_SQL11_SETUP_SSRS_configpage_withcircles](../../../2014/sql-server/install/media/rs-kj-setup-ssrs-configpage-withcircles.gif "rs_SQL11_SETUP_SSRS_configpage_withcircles")  
  
16. Aidez Microsoft à améliorer les fonctionnalités et services de SQL Server en activant la case à cocher pour envoyer les rapports d'erreurs dans la page **Rapport d'erreurs** .  
  
     Cliquez sur **Suivant**.  
  
17. Examinez tout avertissement, puis cliquez sur **Suivant** dans la page **Règles de configuration de l'installation** .  
  
18. Dans la page **Prêt pour l'installation** , lisez le résumé d'installation, puis cliquez sur **Suivant**. Le résumé inclut un **Reporting Services** nœud qui contiendra la valeur de mode d’installation **SharePointFilesOnlyMode** ainsi que les informations de compte.  
  

  
##  <a name="bkmk_install_SSRS_sharedservice"></a> Installez et démarrez le Service SharePoint de Reporting Services  
 ![Contenu relatif à PowerShell](../../../2014/reporting-services/media/rs-powershellicon.jpg "Contenu relatif à PowerShell")  
  
> [!NOTE]  
>  Si vous installez dans une batterie de serveurs SharePoint existante, **vous n’avez pas besoin** toutes les étapes de cette section. Le service SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a été installé et démarré lors de l'exécution de l'Assistant Installation de SQL Server dans la section précédente.  
  
 Les fichiers nécessaires ont été installés dans le cadre de l'assistant Installation de SQL Server, mais les services doivent être enregistrés dans la batterie de serveurs SharePoint. Le [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] version introduit la prise en charge de PowerShell pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint. Les étapes suivantes vous guident dans l'ouverture de SharePoint Management Shell et l'exécution des applets de commande :  
  
1.  Cliquez sur le bouton **Démarrer** .  
  
2.  Cliquez sur le **produits Microsoft SharePoint 2010** groupe.  
  
3.  Avec le bouton droit **SharePoint 2010 Management Shell** cliquez sur **exécuter en tant qu’administrateur**.  
  
4.  Exécutez la commande PowerShell suivante pour installer le service SharePoint. Si la commande est correctement exécutée, une nouvelle ligne apparaît dans le shell de gestion. Aucun message n'est retourné au shell de gestion lorsque la commande est correctement exécutée :  
  
    ```  
    Install-SPRSService  
    ```  
  
5.  Exécutez la commande PowerShell suivante pour installer le proxy de service :  
  
    ```  
    Install-SPRSServiceProxy  
    ```  
  
6.  Exécutez la commande PowerShell suivante pour démarrer le service ou reportez-vous aux notes suivantes pour accéder aux instructions de démarrage du service de l'Administration centrale de SharePoint :  
  
    ```  
    get-spserviceinstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
    ```  
  
 Vous pouvez également démarrer le service depuis l'Administration centrale de SharePoint au lieu d'exécuter la troisième commande PowerShell. Les étapes suivantes sont également utiles pour vérifier que le service fonctionne.  
  
1.  Dans l'Administration centrale de SharePoint, cliquez sur **Gérer les services sur le serveur** dans le groupe **Paramètres système** .  
  
2.  Repérez le **service SQL Server Reporting Services** et cliquez sur **Démarrer** dans la colonne Action.  
  
3.  L'état du service Reporting Services passe d' **Arrêté** à **Démarré**. Si le service Reporting Services n'est pas dans la liste, installez-le à l'aide de PowerShell.  
  
    > [!NOTE]  
    >  Si le service Reporting Services reste à la **démarrage** état et ne passe pas à **démarré**, vérifiez que le service « Administration SharePoint 2010 » est démarré dans le Gestionnaire de serveur Windows.  
  

  
##  <a name="bkmk_create_serrviceapplication"></a> Créer une Application de Service Reporting Services  
 Cette section fournit les étapes pour créer une application de service et une description des propriétés, si vous consultez une application de service existante.  
  
1.  Dans l'Administration centrale de SharePoint, sous le groupe **Gestion des applications** , cliquez sur **Gérer les applications de service**.  
  
2.  Dans le ruban SharePoint, cliquez sur le bouton **Nouveau** .  
  
3.  Dans le menu Nouveau, cliquez sur **Application de service SQL Server Reporting Services**.  
  
    > [!WARNING]  
    >  Si le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] option n’apparaît pas dans la liste, il est un **indication que le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service partagé n’est pas installé**. Examinez la section précédente sur l'utilisation des applets de commande PowerShell pour installer le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
4.  Dans la page **Créer une application de service SQL Server Reporting Services** , entrez un nom pour l'application. Si vous créez plusieurs applications de service Reporting Services, un nom descriptif ou une convention d'affectation de noms peut vous aider à organiser votre administration et vos opérations de gestion.  
  
5.  Dans la section **Pool d’applications** , créez un pool d’applications pour l’application (recommandé). Vous pouvez utiliser le même nom pour le nouveau pool d'applications et pour l'application de service afin de simplifier votre administration actuelle.  
  
     Sélectionnez ou créez un compte géré pour le pool d'applications. Veillez à spécifier un compte d'utilisateur de domaine. Un compte d'utilisateur de domaine autorise l'utilisation de la fonctionnalité Compte géré de SharePoint, qui vous permet de mettre à jour des mots de passe et des informations sur le compte dans un seul emplacement. Des comptes de domaine sont requis si vous prévoyez une montée en puissance parallèle du déploiement incluant des instances de service supplémentaires qui s'exécuteront sous la même identité.  
  
6.  Dans le **Serveur de base de données**, utilisez le serveur actuel ou choisissez un autre serveur SQL Server.  
  
7.  Dans **Nom de la base de données** , la valeur par défaut est `ReportingService_<guid>`, qui est un nom de base de données unique. Si vous tapez une nouvelle valeur, tapez une valeur unique.  
  
8.  Dans **Authentification de la base de données**, la valeur par défaut est Authentification Windows. Si vous choisissez **Authentification SQL**, reportez-vous au guide de l'administrateur SharePoint pour des recommandations concernant l'utilisation de ce type d'authentification dans un déploiement SharePoint.  
  
9. Dans la section **Association d'application Web** , sélectionnez l'application Web à configurer pour l'accès de l'application de service Reporting Services actuelle. Vous pouvez associer une application de service Reporting Services à une application Web. Si toutes les applications Web actuelles sont déjà associées à une application de service Reporting Services, un message d'avertissement apparaît.  
  
10. Cliquez sur **OK**.  
  
11. Le processus de création d'une application de service peut durer plusieurs minutes. Lorsqu'il est terminé, vous voyez s'afficher un message de confirmation et un lien vers la page **Configurer les abonnements et les alertes** . Terminez l'étape de configuration si vous souhaitez utiliser les fonctionnalités d'abonnement et d'alerte [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Pour plus d’informations, consultez [Configurer les abonnements et les alertes pour les applications de service de SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).  
  
 ![Contenu relatif à PowerShell](../../../2014/reporting-services/media/rs-powershellicon.jpg "contenu relatif à PowerShell") pour plus d’informations sur l’utilisation de PowerShell pour créer un [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] application de service, consultez [pour créer une Application de Service Reporting Services à l’aide de PowerShell](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md#bkmk_powershell_create_ssrs_serviceapp).  
  

  
##  <a name="bkmk_powerview"></a> Activer la fonctionnalité de Collection de sites Power View.  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], une fonctionnalité de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] complément pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition, est une fonctionnalité de collection de sites. Elle est activée automatiquement pour les collections de sites racine et celles créés après l'installation de la macro complémentaire [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Si vous envisagez d'utiliser [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], vous devez vérifier que la fonctionnalité est activée.  
  
 Si vous installez le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint 2010 après l'installation du produit SharePoint 2010, la fonctionnalité d'intégration du serveur de rapports et la fonctionnalité d'intégration Power View sont activées uniquement pour les collections de sites racine. Pour les autres collections de sites, activez manuellement les fonctionnalités.  
  
#### <a name="to-activate-the-power-view-feature"></a>Pour activer la fonctionnalité Power View  
  
1.  Ouvrez votre navigateur sur le site SharePoint souhaité.  
  
2.  Cliquez sur **Actions du site**.  
  
3.  Cliquez sur **Paramètres du site**.  
  
4.  Cliquez sur **Fonctionnalités de la collection de sites** dans le groupe Administration de la collection de sites.  
  
5.  Recherchez **Fonctionnalité d'intégration de Power View** dans la liste.  
  
6.  Cliquez sur **Activer**.  
  
 Cette procédure doit être exécutée par collection de sites. Pour plus d’informations, consultez [activer le serveur de rapports et Power View Integration Features in SharePoint](../../reporting-services/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md) .  
  
##  <a name="bkmk_additional_config"></a> Configuration supplémentaire  
 Cette section décrit les étapes de configuration supplémentaires qui sont importantes dans la plupart des déploiements de SharePoint.  
  
###  <a name="bkmk_provision_agent"></a> Configurer les abonnements et les alertes  
 Les fonctionnalités d'abonnement et d'alerte de données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peuvent exiger la configuration des autorisations de SQL Server Agent. Si un message d'erreur apparaît indiquant que SQL Server Agent est obligatoire alors que vous avez vérifié qu'il s'exécute, mettez à jour les autorisations. Cliquez sur le lien **Configurer les abonnements et les alertes** dans la page de création réussie d'application de service pour accéder à une autre page dans laquelle vous pouvez configurer SQL Server Agent. L'étape de configuration est nécessaire si votre déploiement dépasse les limites des machines, par exemple lorsque l'instance de base de données SQL Server se trouve sur un autre ordinateur. Pour plus d’informations, consultez [Configurer les abonnements et les alertes pour les applications de service de SSRS](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md).  
  

  
### <a name="configure-e-mail-for-a-service-application"></a>Configurez la messagerie électronique pour une application de service  
 La fonctionnalité d'alertes de données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] envoie des alertes via des messages électroniques. Pour envoyer du courrier électronique, vous devrez peut-être configurer votre application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et modifier l'extension de remise par messagerie pour l'application de service. Si vous prévoyez d'utiliser l'extension de remise par messagerie pour la fonctionnalité d'abonnement d' [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , les paramètres de courrier électronique sont nécessaires. Pour plus d’informations, consultez [configuration de la messagerie pour une Application de Service Reporting Services &#40;SharePoint 2010 et SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)  
  

  
### <a name="add-reporting-services-content-types"></a>Ajoutez des types de contenu Reporting Services  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit des types de contenu prédéfinis pour gérer les fichiers de sources de données partagées (.rsds), les modèles de rapports (.smdl) et les fichiers de définition de rapport (.rdl) du Générateur de rapports. L'ajout à une bibliothèque des types de contenu **Rapport du Générateur de rapports**, **Modèle de rapport**et **Source de données du rapport** active la commande **Nouveau** , qui permet de créer de nouveaux documents de ce type. Pour plus d’informations, consultez [ajouter Types serveur de rapports contenus dans une bibliothèque &#40;Reporting Services en Mode intégré SharePoint&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).  
  

  
### <a name="activate-the-file-sync-feature"></a>Activez la fonctionnalité Synchronisation de fichiers  
 Si les utilisateurs téléchargent fréquemment des éléments de rapport publiés directement vers des bibliothèques de documents SharePoint, la fonctionnalité de synchronisation de fichiers de serveur de rapports vous sera très utile. La fonctionnalité de synchronisation de fichiers synchronise le catalogue du serveur de rapports avec les éléments des bibliothèques de documents à des intervalles plus fréquents. Pour plus d’informations, consultez [activer la fonctionnalité de synchronisation de fichier de serveur de rapports dans Administration centrale de SharePoint](../../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Applets de commande PowerShell pour Reporting Services SharePoint Mode](../../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)   
 [Fonctionnalités prises en charge par les éditions de SQL Server 2012](http://go.microsoft.com/fwlink/?linkid=232473)   
 [Service SharePoint Reporting Services et Applications de Service](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)  
  
  
