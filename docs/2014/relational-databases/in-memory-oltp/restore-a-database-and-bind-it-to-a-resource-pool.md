---
title: Restaurer une base de données et la lier à un pool de ressources | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0d20a569-8a27-409c-bcab-0effefb48013
caps.latest.revision: 13
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: da39c50e33e894f4311fa4ab7472f60dfb626b8c
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396108"
---
# <a name="restore-a-database-and-bind-it-to-a-resource-pool"></a>Restaurer une base de données et la lier à un pool de ressources
  Même si vous disposez de suffisamment de mémoire pour restaurer une base de données avec des tables optimisées en mémoire, suivez les meilleures pratiques et liez la base de données à un pool de ressources nommé. Comme la base de données doit exister pour que vous puissiez la lier au pool, la restauration de votre base de données s'effectue en plusieurs étapes. Cette rubrique vous guide pas à pas dans ce processus.  
  
## <a name="restoring-a-database-with-memory-optimized-tables"></a>Restauration d'une base de données avec des tables optimisées en mémoire  
 Les étapes suivantes permettent de restaurer complètement la base de données IMOLTP_DB et de la lier à Pool_IMOLTP.  
  
1.  [Effectuer la restauration avec NORECOVERY](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_norecovery)  
  
2.  [Créer le pool de ressources](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_createpool)  
  
3.  [Lier la base de données et le pool de ressources](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_bind)  
  
4.  [Effectuer la restauration avec RECOVERY](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_recovery)  
  
5.  [Surveillance des performances des pools de ressources](restore-a-database-and-bind-it-to-a-resource-pool.md#bkmk_monitor)  
  
###  <a name="bkmk_NORECOVERY"></a> Effectuer la restauration avec NORECOVERY  
 Lorsque vous restaurez une base de données avec l'option NORECOVERY, la base de données est créée et l'image disque est restaurée sans consommer de mémoire.  
  
```tsql  
RESTORE DATABASE IMOLTP_DB   
   FROM DISK = 'C:\IMOLTP_test\IMOLTP_DB.bak'  
   WITH NORECOVERY  
```  
  
###  <a name="bkmk_createPool"></a> Créer le pool de ressources  
 Le code [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant crée un pool de ressources nommé Pool_IMOLTP avec la moitié de la mémoire disponible.  Une fois le pool créé, Resource Governor est reconfiguré afin d'inclure Pool_IMOLTP.  
  
```tsql  
CREATE RESOURCE POOL Pool_IMOLTP WITH (MAX_MEMORY_PERCENT = 50);  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
###  <a name="bkmk_bind"></a> Lier la base de données et le pool de ressources  
 Utilisez la fonction système `sp_xtp_bind_db_resource_pool` pour lier la base de données au pool de ressources. La fonction accepte deux paramètres : le nom de la base de données suivi du nom du pool de ressources.  
  
 Le code [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant définit une liaison de la base de données IMOLTP_DB au pool de ressources Pool_IMOLTP. La liaison ne prend pas effet tant que vous n'avez pas terminé l'étape suivante.  
  
```tsql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
###  <a name="bkmk_RECOVERY"></a> Effectuer la restauration avec RECOVERY  
 Lorsque vous restaurez la base de données avec récupération, la base de données est mise en ligne et toutes les données sont restaurées.  
  
```tsql  
RESTORE DATABASE IMOLTP_DB   
   WITH RECOVERY  
```  
  
###  <a name="bkmk_Monitor"></a> Surveillance des performances des pools de ressources  
 Une fois que la base de données est liée au pool de ressources nommé et qu'elle est restaurée avec récupération, surveillez l'objet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Statistiques des pools de ressources. Pour plus d'informations consultez [SQL Server, objet Resource Pool Stats](../performance-monitor/sql-server-resource-pool-stats-object.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Lier une base de données avec des tables optimisées en mémoire à un pool de ressources](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql)   
 [SQL Server, objet Resource Pool Stats](../performance-monitor/sql-server-resource-pool-stats-object.md)   
 [sys.dm_resource_governor_resource_pools](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)  
  
  
