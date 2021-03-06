---
title: SQLBindCol | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ed7d85356fe38833a030cf2f6f9bb4626f0644d1
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411238"
---
# <a name="sqlbindcol"></a>SQLBindCol
  En règle générale, tenez compte des conséquences de l’utilisation de **SQLBindCol** pour convertir des données. Les conversions de liaison sont des processus clients. Ainsi, par exemple, l'extraction d'une valeur à virgule flottante liée à une colonne de type character conduit le pilote à effectuer localement la conversion du type de données float en character lorsqu'une ligne est extraite. La fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT peut être utilisée pour reporter le coût de la conversion des données sur le serveur.  
  
 Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut retourner plusieurs jeux de lignes de résultats à l'issue de l'exécution d'une même instruction. Chaque jeu de résultats doit être lié séparément. Pour plus d’informations sur la liaison de plusieurs jeux de résultats, consultez [SQLMoreResults](sqlmoreresults.md).  
  
 Le développeur peut lier des colonnes à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-types de données C spécifiques à l’aide de la *TargetType* valeur `SQL_C_BINARY`. Les colonnes liées à des types propres à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sont pas portables. Les types de données ODBC C propres à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont définis correspondent aux définitions de types de DB-Library. Or les développeurs DB-Library portant des applications souhaiteront peut-être tirer parti de cette fonctionnalité.  
  
 Troncation de données de création de rapports est un processus coûteux pour les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client. Vous pouvez éviter la troncation en veillant à ce que toutes les mémoires tampons de données liées soient suffisamment grandes pour retourner des données. Pour les données de type character, la largeur doit inclure l'espace nécessaire pour un indicateur de fin de chaîne lorsque le comportement par défaut du pilote pour l'indicateur de fin de chaîne est utilisé. Par exemple, la liaison un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char (5)** colonne vers un tableau de cinq caractères entraîne la troncation de chaque valeur extraite. La liaison de la même colonne à un tableau de six caractères évite la troncation en fournissant un élément de type character dans lequel stocker l'indicateur de fin null. [SQLGetData](sqlgetdata.md) peut être utilisé pour récupérer efficacement des données de type character ou binary sans troncation.  
  
 Pour les types de données de valeur élevée, si la mémoire tampon fournie par l'utilisateur n'est pas suffisamment grande pour contenir la valeur entière de la colonne, `SQL_SUCCESS_WITH_INFO` est retourné et l'avertissement « Troncation à droite de la chaîne de données » est affiché. L'argument `StrLen_or_IndPtr` contient le nombre de chars/octets stockés dans la mémoire tampon.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>Prise en charge par SQLBindCol des fonctionnalités de date et heure améliorées  
 Résultat des valeurs de colonnes de types date/heure sont converties comme décrit dans [Conversions à partir de SQL vers C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Notez que pour récupérer des colonnes time et datetimeoffset comme structures correspondantes (`SQL_SS_TIME2_STRUCT` et **SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType* doit être spécifié en tant que `SQL_C_DEFAULT` ou `SQL_C_BINARY`.  
  
 Pour plus d’informations, consultez [améliorations Date / heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>Prise en charge de SQLBindCol des table UDT CLR volumineuses  
 **SQLBindCol** prend en charge les types CLR volumineux définis par l’utilisateur (UDT). Pour plus d’informations, consultez [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLBindCol, fonction](http://go.microsoft.com/fwlink/?LinkId=59327)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
