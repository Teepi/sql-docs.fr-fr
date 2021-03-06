---
title: SESSION_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/23/2018
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 2f29f5ba188f70313f94ac4b05f03c7fe8a0575a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052017"
---
# <a name="sessionid-transact-sql"></a>SESSION_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Retourne l’ID de la session [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] actuelle.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
SESSION_ID ( )  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne une valeur **nvarchar(32)**.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 L’ID de session est affecté à chaque connexion utilisateur lors de l’établissement de la connexion. Il persiste pendant la durée de la connexion. Lorsque la connexion se termine, l’ID de session est libéré.  
  
 L’ID de session commence par les caractères alphabétiques « SID ». Ces derniers respectent la casse et doit être mis en majuscules lorsque l’ID de session est utilisé dans des commandes [!INCLUDE[DWsql](../../includes/dwsql-md.md)].  
  
 Vous pouvez interroger la vue [sys.dm_pdw_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) pour récupérer les mêmes informations que cette fonction.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant renvoie l’ID de la session actuelle.  
  
```  
SELECT SESSION_ID();  
```  
  
## <a name="see-also"></a> Voir aussi  
 [DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)   
 [VERSION &#40;SQL Data Warehouse&#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)
  
  
