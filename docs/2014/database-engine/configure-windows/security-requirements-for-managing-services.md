---
title: Spécifications de sécurité pour la gestion des services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent service, security
- services [SQL Server], security
- SQL Server services, security
- WMI Providers [SQL Server]
- server configuration [SQL Server]
- security [SQL Server], services
- services [SQL Server], WMI
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
caps.latest.revision: 27
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0fb5a41efec39b85c0633a3612097a7b643a69e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37160890"
---
# <a name="security-requirements-for-managing-services"></a>Spécifications de sécurité pour la gestion des services
  Pour gérer les services [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, utilisez le Gestionnaire de configuration SQL Server ou [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour gérer les services sur des serveurs clusters, utilisez l'Administrateur de cluster.  
  
 Pour gérer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et définir les options de configuration du serveur, vous devez être membre du rôle serveur fixe **serveradmin** ou **sysadmin** . Les membres du groupe **Administrateurs** Windows peuvent démarrer et arrêter des services et configurer les options serveur fournies par Windows.  
  
> [!NOTE]  
>  Pour bien fonctionner, les comptes utilisés pour les services doivent être configurés correctement au niveau du domaine, du système de fichiers et des autorisations de Registre. Pour plus d’informations sur les autorisations requises, consultez [Configurer les comptes de service Windows et les autorisations](configure-windows-service-accounts-and-permissions.md).  
  
## <a name="windows-management-instrumentation"></a>Windows Management Instrumentation  
 Le Gestionnaire de configuration SQL Server et [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilisent Windows Management Instrumentation pour afficher et modifier une partie des propriétés de serveur. Pour gérer les services et obtenir l'état des services, l'utilisateur doit posséder les droits nécessaires pour accéder à l'objet WMI. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], voici les pages de propriétés de serveur qui utilisent WMI :  
  
-   Démarrage automatique des services  
  
-   Paramètres de démarrage  
  
-   Sécurité  
  
-   Paramètres divers du serveur  
  
## <a name="related-tasks"></a>Related Tasks  
 [Configurer WMI pour afficher l'état du serveur dans les outils SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## <a name="related-content"></a>Contenu associé  
 [Fournisseur WMI pour les concepts de gestion de configuration](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
