---
title: xp_sqlmaint (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xp_sqlmaint
- xp_sqlmaint_TSQL
dev_langs: TSQL
helpviewer_keywords: xp_sqlmaint
ms.assetid: bda66e1b-6bbd-49be-b86e-37efc920e912
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 85a249bfda181c88bab2407a9d077c1414a08bb3
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="xpsqlmaint-transact-sql"></a>xp_sqlmaint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Appelle le **sqlmaint** utilitaire avec une chaîne qui contienne **sqlmaint**commutateurs. Le **sqlmaint** utilitaire exécute un ensemble d’opérations de maintenance sur une ou plusieurs bases de données.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
xp_sqlmaint 'switch_string'     
```  
  
## <a name="arguments"></a>Arguments  
 **'** *chaîne_de_commutateurs* **'**  
 Est une chaîne contenant le **sqlmaint** commutateurs de l’utilitaire. Les commutateurs et leurs valeurs doivent être séparés par un espace.  
  
 Le **- ?** commutateur n’est pas valide pour **xp_sqlmaint**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 Aucun. Retourne une erreur si le **sqlmaint** utilitaire échoue.  
  
## <a name="remarks"></a>Notes  
 Si cette procédure est appelée par un utilisateur connecté à l’aide de l’authentification SQL Server, le **- U «***login_id***»** et **-P «***mot de passe***»** commutateurs sont ajoutés à *chaîne_de_commutateurs* avant l’exécution. Si l’utilisateur est connecté avec l’authentification Windows, *chaîne_de_commutateurs* est transmis sans modification à **sqlmaint**.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, `xp_sqlmaint` appelle `sqlmaint` pour réaliser des contrôles d'intégrité, créer un fichier de rapport et mettre à jour `msdb.dbo.sysdbmaintplan_history`.  
  
```  
EXEC xp_sqlmaint '-D AdventureWorks2012 -PlanID 02A52657-D546-11D1-9D8A-00A0C9054212   
   -Rpt "C:\Program Files\Microsoft SQL Server\MSSQL\LOG\DBMaintPlan2.txt" -WriteHistory  -CkDB -CkAl';   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The command(s) executed successfully.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire sqlmaint](../../tools/sqlmaint-utility.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  