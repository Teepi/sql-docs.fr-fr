---
title: MSdbms_datatype (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdbms_datatype
- MSdbms_datatype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype system table
ms.assetid: 606168cc-79a8-442f-ab43-936f8f884d72
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10e748d771414e9dee552a0e0f7ecdc643ba298a
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103537"
---
# <a name="msdbmsdatatype-transact-sql"></a>MSdbms_datatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSdbms_datatype** table contient la liste complète des types de données natifs sur chaque système de gestion prises en charge de la base de données (SGBD) utilisé comme un serveur de publication ou un abonné dans la réplication de bases de données hétérogènes. Cette table est stockée dans le **msdb** base de données.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**datatype_id**|**Int**|Identifie chaque type de données unique.|  
|**ID DBMS**|**Int**|Identifie le SGBD auquel appartient le type.|  
|**type**|**sysname**|Nom du type de données (natif).|  
|**CreateParams**|**Int**|Bitmap qui décrit la combinaison de longueur, précision et échelle applicable à chaque type de données, à savoir :<br /><br /> **0 x 1** = précision.<br /><br /> **0 x 2** = mise à l’échelle.<br /><br /> **0 x 4** = longueur.|  
  
## <a name="remarks"></a>Notes  
 Cette table contient des entrées pour les types de données SQL Server, car une instance de SQL Server peut s’abonner à une base de données non SQL Server et publier vers un abonné non SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Spécifier des mappages de types de données pour un serveur de publication Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
