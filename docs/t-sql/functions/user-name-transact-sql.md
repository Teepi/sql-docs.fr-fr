---
title: USER_NAME (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- USER_NAME
- USER_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- usernames [SQL Server]
- IDs [SQL Server], databases
- USER_NAME function
- users [SQL Server], database username
- names [SQL Server], database users
- identification numbers [SQL Server], databases
- database usernames [SQL Server]
ms.assetid: ab32d644-4228-449a-9ef0-5a975c305775
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5179a5d031dbc654f1624f4d64c3e94bf28efe40
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="username-transact-sql"></a>USER_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie le nom d'utilisateur de base de données à partir du numéro d'identification spécifié.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
USER_NAME ( [ id ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *id*  
 Numéro d'identification associé à un utilisateur de base de données. *ID*est **int**. Les parenthèses sont obligatoires.  
  
## <a name="return-types"></a>Types de retour  
 **nvarchar (256)**  
  
## <a name="remarks"></a>Notes  
 Lorsque *id* est omis, l’utilisateur actuel dans le contexte actuel est supposé. Si le paramètre contient le mot que null, retourne NULL. Lorsque USER_NAME est appelée sans spécifier un *id* après une exécution en tant qu’instruction, USER_NAME renvoie le nom de l’utilisateur avec emprunt d’identité. Si un principal Windows accède à la base de données par l'intermédiaire de son appartenance à un groupe, USER_NAME renvoie le nom du principal Windows à la place du groupe.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-username"></a>A. Utilisation de USER_NAME  
 L'exemple suivant retourne le nom de l'utilisateur ayant l'ID `13`.  
  
```  
SELECT USER_NAME(13);  
GO  
```  
  
### <a name="b-using-username-without-an-id"></a>B. Utilisation de USER_NAME sans ID  
 Le code exemple suivant recherche le nom de l'utilisateur actuel sans spécifier un ID.  
  
```  
SELECT USER_NAME();  
GO  
```  
  
 Jeu de résultats (pour un utilisateur membre du rôle serveur fixe sysadmin) :  
  
 `------------------------------`  
  
 `dbo`  
  
 `(1 row(s) affected)`  
  
### <a name="c-using-username-in-the-where-clause"></a>C. Utilisation de USER_NAME dans la clause WHERE  
 Le code exemple suivant recherche dans `sysusers` la ligne dans laquelle le nom est égal au résultat de l'application de la fonction système `USER_NAME` à l'utilisateur identifié par le numéro `1`.  
  
```  
SELECT name FROM sysusers WHERE name = USER_NAME(1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `name`  
  
 `------------------------------`  
  
 `dbo`  
  
 `(1 row(s) affected)`  
  
### <a name="d-calling-username-during-impersonation-with-execute-as"></a>D. Appel de USER_NAME pendant un emprunt d'identité avec EXECUTE AS  
 Le code exemple suivant illustre le comportement de `USER_NAME` pendant l'emprunt d'identité.  
  
```  
SELECT USER_NAME();  
GO  
EXECUTE AS USER = 'Zelig';  
GO  
SELECT USER_NAME();  
GO  
REVERT;  
GO  
SELECT USER_NAME();  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DBO`  
  
 `Zelig`  
  
 `DBO`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-username"></a>E. Utilisation de USER_NAME  
 L'exemple suivant retourne le nom de l'utilisateur ayant l'ID `13`.  
  
```  
SELECT USER_NAME(13);  
```  
  
### <a name="f-using-username-without-an-id"></a>F. Utilisation de USER_NAME sans ID  
 Le code exemple suivant recherche le nom de l'utilisateur actuel sans spécifier un ID.  
  
```  
SELECT USER_NAME();  
```  
  
 Voici le jeu de résultats pour un utilisateur actuellement connecté.  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------------------------------   
User7                              
```  
  
### <a name="g-using-username-in-the-where-clause"></a>G. Utilisation de USER_NAME dans la clause WHERE  
 Le code exemple suivant recherche dans `sysusers` la ligne dans laquelle le nom est égal au résultat de l'application de la fonction système `USER_NAME` à l'utilisateur identifié par le numéro `1`.  
  
```  
SELECT name FROM sysusers WHERE name = USER_NAME(1);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
name                             
------------------------------   
User7                              
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CURRENT_TIMESTAMP &#40; Transact-SQL &#41;](../../t-sql/functions/current-timestamp-transact-sql.md)   
 [CURRENT_USER &#40; Transact-SQL &#41;](../../t-sql/functions/current-user-transact-sql.md)   
 [SESSION_USER &#40; Transact-SQL &#41;](../../t-sql/functions/session-user-transact-sql.md)   
 [Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [SYSTEM_USER &#40; Transact-SQL &#41;](../../t-sql/functions/system-user-transact-sql.md)  
  
  

