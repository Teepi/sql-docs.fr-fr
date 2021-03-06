---
title: Modifier l’ordre des colonnes dans une table | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], change order in a table
- column order, change
ms.assetid: cd99ef56-9085-431a-a0fc-58e7add5399f
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f78859e33b009b5e3e54fa6432c34dd1349180df
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230672"
---
# <a name="change-column-order-in-a-table"></a>Modifier l'ordre des colonnes dans une table
  Vous pouvez changer l'ordre des colonnes dans le Concepteur de tables dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
> [!CAUTION]  
>  Changer l'ordre des colonnes d'une table peut avoir une incidence sur le code et les applications qui dépendent de l'ordre spécifique des colonnes. Il peut s'agir de requêtes, de vues, de procédures stockées, de fonctions définies par l'utilisateur et d'applications clientes. Prenez toutes les précautions nécessaires avant de changer l'ordre des colonnes. La recommandation est de spécifier l'ordre dans lequel les colonnes sont renvoyées au niveau de l'application et de la requête. Vous ne pouvez pas compter sur l'utilisation de SELECT * pour retourner toutes les colonnes dans une commande prévue d'après l'ordre dans lequel elles sont définies dans la table. Spécifiez toujours le nom des colonnes dans vos requêtes et applications dans l'ordre dans lequel vous souhaitez qu'elles apparaissent.  
  
 **Dans cette rubrique**  
  
-   **Pour changer l'ordre des colonnes à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-change-the-column-order"></a>Pour changer l'ordre des colonnes  
  
1.  Dans l’ **Explorateur d’objets**, cliquez avec le bouton droit sur la table dont vous souhaitez réorganiser les colonnes et cliquez sur **Conception**.  
  
2.  Sélectionnez la case à gauche du nom de la colonne à réordonner.  
  
3.  Faites glisser la colonne vers un autre emplacement dans la table.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 **Pour changer l'ordre des colonnes**  
  
 Cette tâche ne peut pas être effectuée à l'aide d'instructions Transact-SQL.  
  
###  <a name="TsqlExample"></a>  
