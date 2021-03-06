---
title: Sys.Assemblies (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.assemblies
- assemblies_TSQL
- sys.assemblies_TSQL
- assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assemblies catalog view
ms.assetid: e321753f-293f-42ab-b225-d118713df40b
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 9513f6678be360263fc302f23a4fefc6cc71e39a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39548169"
---
# <a name="sysassemblies-transact-sql"></a>sys.assemblies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Retourne une ligne pour chaque assembly.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom de l’assembly. Unique dans la base de données.|  
|**principal_id**|**Int**|Identificateur du principal qui est propriétaire de cet assembly.|  
|**assembly_id**|**Int**|Numéro d'identification de l'assembly Unique dans une base de données.|  
|**clr_name**|**nvarchar(4000)**|Chaîne canonique qui encode le nom simple, le numéro de version, les paramètres régionaux, la clé publique, et l'architecture de l'assembly. Cette valeur identifie de façon univoque l'assembly du côté CLR (Common Language Runtime).|  
|**permission_set**|**tinyint**|Jeu d'autorisations/niveau de sécurité de l'assembly.<br /><br /> 1 = accès sécurisé<br /><br /> 2 = accès externe<br /><br /> 3 = accès non sécurisé|  
|**permission_set_desc**|**nvarchar(60)**|Description du jeu d'autorisations/niveau de sécurité de l'assembly.<br /><br /> SAFE_ACCESS<br /><br /> EXTERNAL_ACCESS<br /><br /> UNSAFE_ACCESS|  
|**is_visible**|**bit**|1 = l'assembly est visible pour inscrire des points d'entrée [!INCLUDE[tsql](../../includes/tsql-md.md)].<br /><br /> 0 = l'assembly est destiné uniquement aux appelants gérés : L'assembly fournit une implémentation interne pour d'autres assemblys de la base de données.|  
|**create_date**|**datetime**|Date de création ou d'inscription de l'assembly.|  
|**modify_date**|**datetime**|Date de modification de l'assembly.|  
|**is_user_defined**|**bit**|Indique la source de l'assembly.<br /><br /> 0 = assemblys définis par le système (tels que Microsoft.SqlServer.Types pour le **hierarchyid** type de données)<br /><br /> 1 = assemblys définis par l'utilisateur|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue d’assemblys CLR &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ASSEMBLYPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
