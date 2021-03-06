---
title: Utilisez le chemin d’accès complet pour inscrire des noms de DLL de procédure stockée étendue | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- registering DLL names
- extended stored procedures [SQL Server], registering
- DLL names [SQL Server]
- full path DLL name registration [SQL Server]
ms.assetid: f648d57c-af32-4c71-9882-47b6766f3c2b
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cf09e25eb1a07e7714969fb3838859586cf6d763
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303659"
---
# <a name="use-the-full-path-to-register-extended-stored-procedure-dll-names"></a>Utiliser le chemin d'accès complet pour inscrire les noms de DLL de procédures stockées étendues
  Les procédures stockées étendues qui étaient auparavant inscrites sans le chemin d'accès complet pour le nom de la DLL risquent de ne pas fonctionner dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Les procédures stockées étendues qui étaient auparavant inscrites sans le chemin d'accès complet pour le nom de la DLL risquent de ne pas fonctionner après la mise à niveau. Ceci est dû au fait que l'ancien répertoire BINN n'est pas ajouté au nouveau chemin durant le processus de mise à niveau. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] risque de ne pas pouvoir localiser les procédures stockées étendues.  
  
## <a name="corrective-action"></a>Action corrective  
 Avant d'effectuer la mise à niveau, exécutez la procédure suivante pour chaque procédure stockée étendue qui n'a pas été inscrite avec un nom de chemin complet :  
  
1.  Exécutez sp_dropextendedproc pour supprimer la procédure stockée étendue.  
  
2.  Exécutez sp_addextendedproc pour inscrire la procédure stockée étendue avec le nom de chemin complet.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
