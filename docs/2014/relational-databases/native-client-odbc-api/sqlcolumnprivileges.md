---
title: SQLColumnPrivileges | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6462213fddd646c1461f0975dc89b151c192de3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425728"
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
  **SQLColumnPrivileges** retourne SQL_SUCCESS qu’il existe des valeurs ou non le*CatalogName*, *SchemaName*, *TableName*, ou  *ColumnName* paramètres. **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 **SQLColumnPrivileges** peut être exécutée sur un curseur côté serveur statique. Une tentative d’exécution **SQLColumnPrivileges** sur un curseur modifiable (dynamique ou jeu de clés) retourne SQL_SUCCESS_WITH_INFO, indiquant que le type de curseur a été modifié.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge des informations de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le *CatalogName* paramètre : *nom_serveur_lié.Nom_Catalogue*.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLColumnPrivileges, fonction](http://go.microsoft.com/fwlink/?LinkId=59335)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
