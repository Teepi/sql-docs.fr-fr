---
title: Taille d’ensemble de lignes de curseur | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c683ec4cf8b7fd430e9bddd0d126cc132880975f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412303"
---
# <a name="cursor-rowset-size"></a>Taille de l'ensemble de lignes d'un curseur
  Les curseurs ODBC peuvent extraire plusieurs lignes à la fois. Ils peuvent extraire plusieurs lignes dans chaque appel à **SQLFetch** ou [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md). Lorsque vous utilisez une base de données client/serveur, telle que Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il est plus efficace d'extraire plusieurs lignes à la fois. Le nombre de lignes retournées lors d’une extraction est appelé à la taille de l’ensemble de lignes et qu’il est spécifié en utilisant le paramètre SQL_ATTR_ROW_ARRAY_SIZE de [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 Les curseurs dont la taille de l'ensemble de lignes est supérieure à 1 sont appelés « curseurs de bloc ».  
  
 Deux options s'offrent à vous pour lier des colonnes de jeu de résultats pour des curseurs de bloc :  
  
-   Liaison selon les colonnes  
  
     Chaque colonne est liée à un tableau de variables. Chaque tableau possède un nombre d'éléments égal à la taille de l'ensemble de lignes.  
  
-   Liaison selon les lignes  
  
     Un tableau est construit à l'aide de structures qui contiennent les données et d'indicateurs pour toutes les colonnes d'une ligne. Le tableau possède un nombre de structures égal à la taille de l'ensemble de lignes.  
  
 Lorsque la liaison selon les colonnes ou lignes est utilisée, chaque appel à **SQLFetch** ou **SQLFetchScroll** remplit les tableaux liés avec les données à partir de l’ensemble de lignes récupérée.  
  
 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) peut également être utilisé pour récupérer des données de la colonne à partir d’un curseur de bloc. Étant donné que **SQLGetData** fonctionne d’une ligne à la fois, **SQLSetPos** doit être appelé pour définir une ligne spécifique dans l’ensemble de lignes que la ligne actuelle avant d’appeler **SQLGetData**.  
  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client offre une optimisation à l’aide des ensembles de lignes à récupérer un ensemble de résultats rapidement. Pour utiliser cette optimisation, définissez les attributs de curseur sur leurs valeurs par défaut (ensemble de lignes avant uniquement et en lecture seule, taille = 1) au moment **SQLExecDirect** ou **SQLExecute** est appelée. Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client définit un jeu de résultats par défaut. Cette approche est plus efficace que les curseurs côté serveur lors du transfert de résultats au client sans défilement. Après avoir exécuté l'instruction, augmentez la taille de l'ensemble de lignes et utilisez la liaison selon les colonnes ou la liaison selon les lignes. Cela vous permet de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisez un résultat par défaut définie pour envoyer efficacement des lignes de résultats au client, tandis que le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client extrait en continu des lignes des tampons réseau sur le client.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de curseur](cursor-properties.md)  
  
  
