---
title: "Accorder l’accès utilisateur à un serveur de rapports | Documents Microsoft"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
caps.latest.revision: 54
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a92c37165b8142b7e96a8bb99dee43ea5f12e247
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="grant-user-access-to-a-report-server"></a>Accorder l’accès utilisateur à un serveur de rapports

[!INCLUDE[ssrs-appliesto-sql2016-preview](../../includes/ssrs-appliesto-sql2016-preview.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise la sécurité basée sur les rôles pour permettre à un utilisateur d’accéder à un serveur de rapports. Dans une nouvelle installation du serveur de rapports, seuls les utilisateurs membres du groupe Administrateurs local disposent d'autorisations relatives au contenu et au fonctionnement du serveur de rapports. Pour rendre le serveur de rapports accessible à d’autres utilisateurs, vous devez créer des attributions de rôles qui mappent des comptes d’utilisateurs ou de groupes à un rôle prédéfini spécifiant une collection de tâches.

 **Serveurs de rapports en mode SharePoint :** pour un serveur de rapports configuré en mode intégré SharePoint, vous configurez l’accès à partir d’un site SharePoint à l’aide d’autorisations SharePoint. Les niveaux d'autorisation du site SharePoint déterminent l'accès au contenu du serveur de rapports et son bon fonctionnement. Vous devez être un administrateur de site pour pouvoir accorder des autorisations sur un site SharePoint. Pour plus d’informations, consultez [Accord d’autorisations sur des éléments de serveur de rapports sur un site SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md).

 **Serveurs de rapports en mode natif :** cette rubrique se concentre sur un serveur de rapports est configuré en mode natif et l’utilisation du portail web pour affecter des utilisateurs à un rôle. Il existe deux types de rôles :

- Les rôles au niveau élément permettent d'afficher, d'ajouter et de gérer le contenu du serveur de rapports, les abonnements, le traitement des rapports et l'historique de rapport. Les attributions de rôles au niveau élément sont définies sur le nœud racine (dossier de base) mais aussi sur des dossiers ou des éléments spécifiques situés plus bas dans l'arborescence.

- Les rôles de niveau système accordent l'accès aux opérations à l'échelle du site qui ne sont pas liées à un élément spécifique. Cela inclut par exemple l'utilisation du Générateur de rapports et des planifications partagées.

    Les deux types de rôles sont complémentaires et doivent être utilisés ensemble. Par conséquent, l'ajout d'un utilisateur à un serveur de rapports est une opération en deux parties. Si vous attribuez un rôle au niveau élément à un utilisateur, vous devez également lui attribuer un rôle de niveau système. Lorsque vous attribuez un rôle à un utilisateur, vous devez sélectionner un rôle déjà défini. Pour créer, modifier ou supprimer des rôles, utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Pour plus d’informations, consultez [Créer, supprimer ou modifier un rôle &#40;Management Studio&#41;](../../reporting-services/security/role-definitions-create-delete-or-modify.md).

## <a name="before-you-start"></a>Avant de commencer

Examinez la liste suivante avant d'ajouter des utilisateurs à un serveur de rapports en mode natif.

- Vous devez être membre du groupe Administrateurs local sur le serveur de rapports. Si vous déployez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sur [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] ou Windows Server 2008, vous devez effectuer une configuration supplémentaire pour pouvoir administrer un serveur de rapports localement. Pour plus d’informations, consultez [configurer un serveur de rapports en Mode natif pour l’Administration locale](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).

- Pour déléguer cette tâche à d'autres utilisateurs, créez des attributions de rôles qui mappent des comptes d'utilisateurs aux rôles Gestionnaire de contenu et Administrateur système. Les utilisateurs qui disposent d'autorisations liées aux rôles Gestionnaire de contenu et Administrateur système peuvent ajouter des utilisateurs à un serveur de rapports.

- Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], passez en revue les rôles prédéfinis pour les rôles système et les rôles d’utilisateurs pour vous familiariser avec les types de tâches de chaque rôle. Description des tâches ne sont pas visibles dans le portail web, donc vous devez être familiarisé avec les rôles avant de commencer l’ajout d’utilisateurs.

- Vous pouvez éventuellement personnaliser les rôles ou définir des rôles supplémentaires pour inclure la collection de tâches dont vous avez besoin. Par exemple, si vous envisagez d'utiliser des paramètres de sécurité personnalisés pour des éléments individuels, vous pouvez créer une définition de rôle qui permet d'afficher les dossiers.

### <a name="to-add-a-user-or-group-to-a-system-role"></a>Pour ajouter un utilisateur ou un groupe à un rôle système

1. Démarrer le [portail web](../web-portal-ssrs-native-mode.md).

2. Sélectionnez le *icône d’engrenage* dans le coin supérieur droit.

3. Sélectionnez **Paramètres du site**.

4. Sélectionnez **Sécurité**.

5. Sélectionnez **ajouter un groupe ou utilisateur**.

6. Dans **groupe ou utilisateur**, entrez un utilisateur de domaine Windows ou de groupe dans ce format : \<domaine >\\< compte\>. 

    > [!NOTE]
    > Si vous utilisez l'authentification par formulaires ou la sécurité personnalisée, spécifiez le compte d'utilisateur ou de groupe en respectant le format approprié pour votre déploiement.

7. Sélectionnez un rôle de système, puis **OK**.

    Les rôles sont cumulatifs ; par conséquent, si vous sélectionnez à la fois le rôle Administrateur système et le rôle Utilisateur système, un utilisateur ou un groupe pourra effectuer les tâches incluses dans les deux rôles.

8. Répétez l'opération afin de créer des attributions pour des utilisateurs ou des groupes supplémentaires.

### <a name="to-add-a-user-or-group-to-an-item-role"></a>Pour ajouter un utilisateur ou un groupe à un rôle au niveau élément

1. Démarrer le **portail web** et recherchez l’élément de rapport pour lequel vous souhaitez ajouter un utilisateur ou un groupe.

2. Sélectionnez le **...**  (ellipse) sur un élément.

3. Dans le menu déroulant, sélectionnez **gérer**.

4. Sélectionnez **Sécurité**.

5. Sélectionnez **ajouter un groupe ou utilisateur**.

    > [!NOTE]
    > Si un élément hérite actuellement de sécurité à partir d’un élément parent, sélectionnez **personnaliser la sécurité** dans la barre d’outils pour modifier les paramètres de sécurité. Puis sélectionnez **ajouter un groupe ou utilisateur**.

6. Dans **groupe ou utilisateur**, entrez un utilisateur de domaine Windows ou de groupe dans ce format : \<domaine >\\< compte\>. Si vous utilisez l'authentification par formulaires ou la sécurité personnalisée, spécifiez le compte d'utilisateur ou de groupe en respectant le format approprié pour votre déploiement.

7. Sélectionnez un ou plusieurs définitions de rôles qui décrivent la façon dont l’utilisateur ou le groupe doit accéder à l’élément, puis sélectionnez **OK**.

8. Répétez l'opération afin de créer des attributions pour des utilisateurs ou des groupes supplémentaires.

## <a name="next-steps"></a>Étapes suivantes

[Créer et gérer des attributions de rôles](../../reporting-services/security/create-and-manage-role-assignments.md)   
[Nouvelle attribution de rôle : Modifier la Page de l’attribution de rôle &#40; Le Gestionnaire de rapports &#41;](http://msdn.microsoft.com/library/3319ced0-4b86-42af-b18d-da41a625113c)   
[Page de propriétés de sécurité, les éléments &#40; Le Gestionnaire de rapports &#41;](http://msdn.microsoft.com/library/351b8503-354f-4b1b-a7ac-f1245d978da0)   
[Attributions de rôles](../../reporting-services/security/role-assignments.md)   
[Définitions de rôles](../../reporting-services/security/role-definitions.md)  

D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)