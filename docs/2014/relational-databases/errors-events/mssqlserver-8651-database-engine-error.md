---
title: MSSQLSERVER_8651 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 8651 (Database Engine error)
ms.assetid: 4cc3498d-5449-4c4e-b1f9-3271831c725a
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 27884929430abbfd63d365ca0a76f2184314b30f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431218"
---
# <a name="mssqlserver8651"></a>MSSQLSERVER_8651
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|8651|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|MEMGRANT_ERR|  
|Texte du message|Impossible d'exécuter l'opération demandée, car la mémoire est insuffisante. Diminuez la valeur configurée pour l'option de configuration de serveur « min memory per query ».|  
  
## <a name="explanation"></a>Explication  
 D'autres processus consomment de la mémoire du serveur (provoquant des insuffisances de mémoire dans le serveur).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Diminuez la valeur configurée pour l'option de configuration de serveur « min memory per query » ou diminuez la charge des requêtes sur le serveur.  
  
 La liste suivante présente les procédures générales à suivre pour résoudre les erreurs de mémoire.  
  
1.  Vérifiez si d'autres applications ou services consomment de la mémoire sur ce serveur. Reconfigurez les applications ou les services moins importants pour consommer moins de mémoire.  
  
2.  Commencez à recueillir des compteurs de l’analyseur de performances pour **SQL Server : Gestionnaire de tampons**, **SQL Server : Gestionnaire de mémoire**.  
  
3.  Vérifiez les paramètres de configuration de la mémoire de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suivants :  
  
    -   **Mémoire maximum du serveur**  
  
    -   **Mémoire minimum du serveur**  
  
    -   **Mémoire minimum par requête**  
  
     Identifiez les paramètres inhabituels. Si besoin est, corrigez-les. Les paramètres par défaut sont répertoriés dans la rubrique « Définition des options de configuration de serveur » de la documentation en ligne de SQL Server.  
  
4.  Vérifiez la charge de travail (par exemple, le nombre de sessions simultanées, les requêtes en cours d'exécution).  
  
 Les actions ci-dessous peuvent éventuellement augmenter la quantité de mémoire disponible pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   Si des applications autres que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consomment des ressources, essayez d'arrêter l'exécution de ces applications ou envisagez de les exécuter sur un serveur distinct. Vous relâcherez ainsi la pression sur la mémoire externe.  
  
-   Si vous avez configuré le paramètre **Mémoire maximum du serveur**, augmentez sa valeur.  
  
 Exécutez les commandes DBCC ci-dessous pour libérer plusieurs caches mémoire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
 Si le problème persiste, vous devez poursuivre vos recherches et éventuellement, réduire la charge de travail.  
  
## <a name="see-also"></a>Voir aussi  
 [DBCC FREESYSTEMCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql)   
 [DBCC FREESESSIONCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql)   
 [DBCC FREEPROCCACHE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-freeproccache-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [SQL Server, objet Gestionnaire de tampons](../performance-monitor/sql-server-buffer-manager-object.md)   
 [SQL Server, objet Memory Manager](../performance-monitor/sql-server-memory-manager-object.md)  
  
  
