---
title: MSSQLSERVER_2579 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2579 (Database Engine error)
ms.assetid: 8f929d69-8eb4-4fe9-be52-b9680a7820db
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: abcbd38497d5e7a5e942c9aba0f9bcdd784d3a8a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37418298"
---
# <a name="mssqlserver2579"></a>MSSQLSERVER_2579
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2579|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_EXTENT_OUT_OF_RANGE|  
|Texte du message|Erreur de table : l'extension P_ID, ID d'objet O_ID, ID d'index I_ID, ID de partition PN_ID, ID d'unité d'allocation A_ID (type TYPE) est en dehors des limites de cette base de données.|  
  
## <a name="explanation"></a>Explication  
 *P_ID* est un ID de page de la forme *(filenum:pageinfile)*. La valeur de *pageinfile* de cette extension est supérieure à la taille physique du fichier (*filenum*) de la base de données. L'extension est marquée comme étant allouée dans une page IAM pour l'ID d'unité d'allocation indiquée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
### <a name="look-for-hardware-failure"></a>Rechercher une défaillance matérielle  
 Exécutez les diagnostics matériels et corrigez les éventuels problèmes rencontrés. Examinez également les journaux système et des applications de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, ainsi que le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vérifier si l'erreur est due à une défaillance matérielle. Corrigez les éventuels problèmes matériels contenus dans les journaux.  
  
 Si vous avez des problèmes persistants de données endommagées, tentez d'échanger votre ordinateur, vos contrôleurs et vos lecteurs de disque contre d'autres composants. Assurez-vous que votre système n'a pas une mémoire cache d'écriture active sur le contrôleur de disque. Si vous soupçonnez qu’il s’agit là de la source du problème, contactez votre fournisseur de matériel.  
  
 Enfin, il peut s'avérer bénéfique d'utiliser un matériel totalement nouveau, avec reformatage des lecteurs de disque et réinstallation du système d'exploitation.  
  
### <a name="restore-from-backup"></a>Restaurer à partir de la sauvegarde  
 Si le problème n'est pas matériel et si une restauration réputée en bon état est disponible, restaurez la base de données à partir de la sauvegarde.  
  
### <a name="run-dbcc-checkdb"></a>Exécuter DBCC CHECKDB  
 Si aucune sauvegarde saine n'est disponible, exécutez DBCC CHECKDB sans clause REPAIR afin de déterminer l'étendue de l'altération. DBCC CHECKDB recommande une clause REPAIR à utiliser. Puis, exécutez DBCC CHECKDB avec la clause REPAIR adéquate afin de réparer les dommages.  
  
> [!CAUTION]  
>  Si vous n'êtes pas sûr de l'effet de DBCC CHECKDB avec une clause REPAIR sur vos données, contactez l'assistance technique avant d'exécuter cette instruction.  
  
 Si l'exécution de DBCC CHECKDB avec une des clauses REPAIR ne résout pas le problème, contactez l’assistance technique.  
  
### <a name="results-of-running-repair-options"></a>Résultats de l'exécution des options REPAIR  
 L'exécution de REPAIR entraînera la désallocation de l'extension de la page IAM.  
  
> [!CAUTION]  
>  Cette réparation peut entraîner une perte de données.  
  
  
