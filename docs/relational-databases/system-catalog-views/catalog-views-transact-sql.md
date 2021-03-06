---
title: Catalogue des vues (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sql13.SysViewExpandPortal.f1
dev_langs:
- TSQL
helpviewer_keywords:
- catalog metadata [SQL Server]
- system views [SQL Server], catalog
- metadata [SQL Server], views
- catalogs [SQL Server], metadata
- catalog views [SQL Server]
- Database Engine [SQL Server], metadata
- catalog views [SQL Server], about catalog views
ms.assetid: 13bccc2f-ed3c-4b58-abd0-ca8bf34a66b8
caps.latest.revision: 45
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 79d48d8f42b3036d2a44b71048c90bf94cff3522
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39544169"
---
# <a name="system-catalog-views-transact-sql"></a>Vues de catalogue système (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les affichages catalogue retournent des informations utilisées par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Il est conseillé d'utiliser les affichages catalogue puisqu'ils représentent l'interface la plus générale vers les métadonnées de catalogue et le moyen le plus efficace pour obtenir, transformer et présenter des formulaires personnalisés de ces informations. Toutes les métadonnées de catalogue accessibles à l'utilisateur sont exposées dans des affichages catalogue.  
  
> [!NOTE]  
>  Les affichages catalogue ne contiennent pas d'informations sur la réplication, la sauvegarde, le plan de maintenance de base de données ou les données de catalogue de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Certains affichages de catalogue héritent de lignes d'autres affichages catalogue. Par exemple, le [sys.tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) hérite de la vue de catalogue le [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) vue de catalogue. L'affichage catalogue sys.objects est appelé affichage de base, et l'affichage sys.tables est appelé affichage dérivé. L'affichage catalogue sys.tables retourne les colonnes qui sont spécifiques aux tables, ainsi que toutes les colonnes retournées par l'affichage catalogue sys.objects. L'affichage catalogue sys.objects retourne des lignes pour les objets autres que les tables, notamment les procédures stockées et les vues. Lorsqu'une table est créée, les métadonnées de la table sont retournées dans les deux affichages. Bien que les deux affichages catalogue retournent différents niveaux d'informations concernant la table, il n'existe qu'une seule entrée dans les métadonnées de cette table, avec un nom et un object_id. Cela peut être résumé comme suit :  
  
-   L'affichage de base contient un sous-ensemble de colonnes et un sur-ensemble de lignes.  
  
-   L'affichage dérivé contient un sur-ensemble de colonnes et un sous-ensemble de lignes.  
  
> [!IMPORTANT]  
>  Dans les versions ultérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[msCoName](../../includes/msconame-md.md)] peut augmenter la définition de l'affichage catalogue système en ajoutant des colonnes à la fin de la liste des colonnes. Nous déconseillons l’utilisation de la syntaxe SELECT \* FROM *sys.catalog_view_name* en production code car le nombre de colonnes retourné peut changer et altérer votre application.  
  
 Les affichages catalogue de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont classés en plusieurs catégories :  
  
|||  
|-|-|  
|[Affichages catalogue de groupes de disponibilité Always On &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)|[Messages &#40;pour les erreurs&#41; affichages catalogue &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)|  
|[Affichages catalogue de base de données SQL Azure](../../relational-databases/system-catalog-views/azure-sql-database-catalog-views.md)|[Affichages catalogue de l’objet &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)|  
|[Le suivi des modifications des affichages catalogue &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)|[Affichages catalogue des fonctions de partition &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)|  
|[Affichages catalogue d’assemblys CLR &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)|[Vues de la Gestion basée sur des stratégies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)|  
|[Vues du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)|[Affichages catalogue du gouverneur de ressources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)|  
|[Espaces de données &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)|[Affichages catalogue du magasin de requêtes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)|  
|[Vues de la messagerie de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mail-views-transact-sql.md)|[Affichages catalogue de Types scalaires &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)|  
|[Affichages catalogue de témoin de mise en miroir de base de données &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/8a0c9053-5d76-4aa9-a18d-0ea1c514034d)|[Affichages catalogue de schémas &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/c516fb1c-b6ed-48ae-99c7-a78bc4336c8e)|  
|[Affichages catalogue de bases de données et fichiers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)|[Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)|  
|[Affichages catalogue de points de terminaison &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)|[Affichages catalogue relatifs à Service Broker &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql.md)|  
|[Affichages catalogue des événements étendus &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)|[Affichages catalogue de Configuration de l’échelle du serveur &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)|  
|[Vues de catalogue des propriétés étendues &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/f39fd324-efd4-4468-884c-bf77ed1a026f)|[Affichages catalogue de données spatiales](../../relational-databases/system-catalog-views/spatial-data-catalog-views.md)|  
|[Les opérations externes des affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/external-operations-catalog-views-transact-sql.md)|[SQL Data Warehouse et les vues de catalogue Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)|  
|[FileStream et les affichages catalogue FileTable &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)|[Stretch Database des vues de catalogue &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/bee78e39-e07d-4b0f-b8ad-09a01a5eb795)|  
|[Affichages catalogue de recherche en texte intégral et la recherche sémantique &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/full-text-search-and-semantic-search-catalog-views-transact-sql.md)|[Schémas XML &#40;système de Type XML&#41; affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)|  
|[Affichages catalogue de serveurs liés &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)||  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de schémas d’informations &#40;Transact-SQL&#41;](../../relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [Tables système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)   
 [Questions fréquentes (FAQ) sur l’interrogation des catalogues système SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
