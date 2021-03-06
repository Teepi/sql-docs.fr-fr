---
title: Sys.dm_os_host_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/10/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sys.dm_os_host_info
- sys.dm_os_host_info_TSQL
- dm_os_host_info
- dm_os_host_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_host_info dynamic management view
ms.assetid: 9bb6ef86-957b-4ca1-ad20-ca2f8460a86d
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: b64a026b1fcb4ce959b8a60938b73ccdb3c6c352
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39553449"
---
# <a name="sysdmoshostinfo-transact-sql"></a>sys.dm_os_host_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Retourne une ligne qui affiche des informations de version de système d’exploitation.  
  
|Nom de colonne |Type de données |Description |  
|-----------------|---------------|-----------------|  
|**host_platform** |**nvarchar (256)** |Le type de système d’exploitation : Windows ou Linux |
|**host_distribution** |**nvarchar (256)** |Description du système d’exploitation. |
|**host_release**|**nvarchar (256)**|Version du système d'exploitation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows (numéro de version). Pour obtenir la liste de valeurs et les descriptions, consultez [Version de système d’exploitation (Windows)](http://msdn.microsoft.com/library/ms724832\(VS.85\).aspx). <br> Pour Linux, retourne une chaîne vide. |  
|**host_service_pack_level**|**nvarchar (256)**|Niveau du Service Pack du système d'exploitation Windows. <br> Pour Linux, retourne une chaîne vide. |  
|**host_sku**|**Int**|ID de référence (SKU) Windows. Pour obtenir la liste des ID de référence (SKU) et des descriptions, consultez [GetProductInfo, fonction](http://msdn.microsoft.com/library/ms724358.aspx). Autorise la valeur NULL. <br> Pour Linux, retourne la valeur NULL. |  
|**os_language_version**|**Int**|Identificateur des paramètres régionaux (LCID) du système d'exploitation. Pour obtenir la liste des valeurs LCID et des descriptions, consultez [ID de paramètres régionaux assignés par Microsoft](http://go.microsoft.com/fwlink/?LinkId=208080). Ne peut pas avoir la valeur null.|  

## <a name="remarks"></a>Notes  
Cette vue est similaire à [sys.dm_os_windows_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md), ajout de colonnes pour différencier Windows et Linux.
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
Le `SELECT` autorisation sur `sys.dm_os_host_info` est accordé à la `public` rôle par défaut. Si révoqué, nécessite `VIEW SERVER STATE` autorisation sur le serveur.   
 
>  [!CAUTION]
>  Depuis la version [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.3, [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] version 17 nécessite `SELECT` autorisation sur `sys.dm_os_host_info` pour vous connecter à [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Si `SELECT` autorisation est révoquée sur `public`, seuls les utilisateurs avec `VIEW SERVER STATE` autorisation peut se connecter avec la version la plus récente de SSMS. (Autres outils, tels que `sqlcmd.exe` peut se connecter sans `SELECT` autorisation sur `sys.dm_os_host_info`.)

  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne toutes les colonnes à partir de la **sys.dm_os_host_info** vue.  
  
```  
SELECT host_platform, host_distribution, host_release, 
    host_service_pack_level, host_sku, os_language_version  
FROM sys.dm_os_host_info;  
```  

Voici un exemple de résultat défini sur Windows :
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Windows   |Windows Server 2012 R2 Standard    |6.3    |   |7  |1033 |  

Voici un exemple jeu de résultats sur Linux :
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Linux |Ubuntu |16.04  |   |NULL   |1033 |  

  
## <a name="see-also"></a>Voir aussi  
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_windows_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)  
 

