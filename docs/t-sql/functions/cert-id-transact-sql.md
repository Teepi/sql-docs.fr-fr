---
title: CERT_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CERT_ID
- CERT_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], certificates
- CERT_ID function
- IDs [SQL Server], certificates
- certificates [SQL Server], IDs
ms.assetid: 59cc06f5-272e-4936-8afe-afba7aba8eea
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7083a4dbfc87b33d9c00f6c84d0cf18047338e6c
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/04/2018
ms.locfileid: "37783890"
---
# <a name="certid-transact-sql"></a>CERT_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Cette fonction retourne la valeur d’ID d’un certificat.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
Cert_ID ( 'cert_name' )  
```  
  
## <a name="arguments"></a>Arguments  
**'** *cert_name* **'**  

Nom d’un certificat dans la base de données.
  
## <a name="return-types"></a>Types de retour
 **Int**  
  
## <a name="remarks"></a>Notes   
La vue de catalogue [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) affiche les noms de certificat.
  
## <a name="permissions"></a>Autorisations  
Nécessite des autorisations sur le certificat, et nécessite que l’appelant ne se soit pas vu refuser l’autorisation VIEW DEFINITION pour le certificat. Pour plus d’informations sur les autorisations de certificat, consultez [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md#permissions).
  
## <a name="examples"></a>Exemples  
Cet exemple retourne l’ID d’un certificat appelé `ABerglundCert3`.
  
```sql
SELECT Cert_ID('ABerglundCert3');  
GO  
```  
  
## <a name="see-also"></a>Voir aussi
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)
  
  
