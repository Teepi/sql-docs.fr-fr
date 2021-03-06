---
title: Configurer des comptes de connexion pour la mise en miroir de base de données ou des groupes de disponibilité AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- logins [SQL Server], database mirroring
ms.assetid: e9f5287b-1325-4cda-88a6-19eaaa52a652
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ba315e277513bb0f488982dcfb84bded5cc48a73
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245259"
---
# <a name="set-up-login-accounts-for-database-mirroring-or-alwayson-availability-groups-sql-server"></a>Configurer des comptes de connexion pour la mise en miroir de bases de données ou les groupes de disponibilité AlwaysOn (SQL Server)
  Pour que deux instances de serveur se connectent au [point de terminaison de mise en miroir de bases de données](the-database-mirroring-endpoint-sql-server.md) de l'autre, le compte de connexion de chaque instance doit avoir accès à l'autre instance. Par ailleurs, chaque compte de connexion doit disposer d'une autorisation de connexion au point de terminaison de mise en miroir de bases de données de l'autre instance.  
  
 L'impact de cette condition est différent suivant que les instances de serveur s'exécutent ou non sous le même compte d'utilisateur de domaine :  
  
-   Si les instances de serveur s'exécutent sous le même compte d'utilisateur de domaine, les noms de connexion d'utilisateur corrects existent automatiquement dans les deux bases de données **master** . Cela simplifie la configuration de sécurité pour la mise en miroir de bases de données et pour les groupes de disponibilité AlwaysOn.  
  
-   Si les instances de serveur s'exécutent sous des comptes d'utilisateur différents, les connexions utilisateur sur l'instance de serveur qui héberge le serveur ou le réplica principal doivent être manuellement reproduites sur l'instance de serveur qui héberge le serveur miroir ou sur chaque instance de serveur qui héberge un réplica secondaire. Pour plus d'informations, consultez [Créer une connexion pour un compte différent](#CreateLogin) et [Accorder l'autorisation CONNECT](#GrantConnect), plus loin dans cette rubrique.  
  
    > [!IMPORTANT]  
    >  Pour créer un environnement plus sécurisé, envisagez d'utiliser des comptes de domaine distincts pour chaque instance de serveur.  
  
##  <a name="CreateLogin"></a> Créer une connexion pour un compte différent  
 Si deux instances de serveur s'exécutent sous des comptes différents, l'administrateur système doit utiliser l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE LOGIN pour créer une connexion pour le compte de service de démarrage de l'instance distante de chaque instance de serveur. Pour plus d’informations, consultez [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).  
  
> [!IMPORTANT]  
>  Si vous exécutez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous un compte qui n'appartient pas à un domaine, vous devez utiliser des certificats. Pour plus d'informations, consultez [Utiliser des certificats pour un point de terminaison de mise en miroir de bases de données &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).  
  
 Par exemple, pour l'instance de serveur sqlA qui s'exécute sous loginA, pour vous connecter à l'instance de serveur sqlB, qui s'exécute sous loginB, loginA doit exister sur sqlB et loginB doit exister sur sqlA. En outre, pour une session de mise en miroir de bases de données comprenant une instance du serveur témoin (sqlC) et dans laquelle les trois instances de serveur s'exécutent sous des comptes de domaine différents, les noms d'accès suivants doivent être créés :  
  
|Sur l'instance...|Créez des noms d'accès pour et accordez des autorisations de connexion à...|  
|--------------------|--------------------------------------------------------------|  
|sqlA|sqlB et sqlC|  
|sqlB|sqlA et sqlC|  
|sqlC|sqlA et sqlB|  
  
> [!NOTE]  
>  Il est possible de se connecter au compte de service réseau en utilisant le compte d'ordinateur plutôt qu'un utilisateur de domaine. Si le compte d'ordinateur est utilisé, il doit être ajouté en tant qu'utilisateur sur l'autre instance de serveur.  
  
##  <a name="GrantConnect"></a> Accorder l'autorisation CONNECT  
 Après avoir créé un nom d'accès sur une instance de serveur, vous devez lui accorder l'autorisation de se connecter au point de terminaison de mise en miroir de bases de données de l'instance de serveur. L'administrateur système accorde l'autorisation de connexion à l'aide d'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] GRANT. Pour plus d’informations, consultez [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Créer un compte de connexion](../../relational-databases/security/authentication-access/create-a-login.md)  
  
-   [Autoriser l’accès sur le réseau à un point de terminaison de mise en miroir de bases de données au moyen de l’authentification Windows &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).  
  
-   [Utiliser des certificats pour un point de terminaison de mise en miroir de bases de données &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md)   
 [Résolution des problèmes de configuration de mise en miroir de bases de données &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md)   
 [Résoudre les problèmes de Configuration des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
