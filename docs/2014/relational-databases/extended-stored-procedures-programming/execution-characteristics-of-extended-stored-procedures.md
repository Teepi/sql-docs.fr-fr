---
title: Caractéristiques d’exécution des procédures stockées étendues | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], executing
- executing extended stored procedures [SQL Server]
ms.assetid: 6fe1f7e8-cc02-49df-8a2a-d47a96ec3567
caps.latest.revision: 33
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b8b0f8e2b720336deb008b47dc5041d5ece3f55c
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084621"
---
# <a name="execution-characteristics-of-extended-stored-procedures"></a>Caractéristiques d'exécution des procédures stockées étendues
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 L'exécution d'une procédure stockée étendue présente les caractéristiques suivantes :  
  
-   La fonction de procédure stockée étendue est exécutée sous le contexte de sécurité [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   La fonction de procédure stockée étendue s'exécute dans l'espace de processus de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Le thread associé à l'exécution de la procédure stockée étendue est le même que celui utilisé pour la connexion cliente.  
  
    > [!IMPORTANT]  
    >  Avant d'ajouter des procédures stockées étendues au serveur et d'octroyer à d'autres utilisateurs l'autorisation de les exécuter, il est conseillé à l'administrateur système de revoir chaque procédure stockée étendue afin de s'assurer qu'elle n'intègre aucun code nuisible ou malveillant.  
  
-  
  
 Une fois la procédure stockée étendue DLL est chargée, la DLL reste chargée dans l’espace d’adressage du serveur jusqu'à ce que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est arrêté ou l’administrateur décharge explicitement la DLL à l’aide de DBCC *nom_dll* (gratuit).  
  
 La procédure stockée étendue peut être exécutée à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] comme procédure stockée à l'aide de l'instruction EXECUTE :  
  
```  
EXECUTE @retval = xp_extendedProcName @param1, @param2 OUTPUT  
```  
  
## <a name="parameters"></a>Paramètres  
 \@ *retval*  
 Est une valeur de retour.  
  
 \@ *param1*  
 Paramètre d'entrée.  
  
 \@ *param2*  
 Paramètre d'entrée/sortie.  
  
> [!CAUTION]  
>  Les procédures stockées étendues offrent une amélioration des performances et étendent les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Toutefois, comme la DLL de procédure stockée étendue et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] partagent le même espace d'adressage, une procédure problématique peut affecter le fonctionnement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de façon défavorable. Bien que les exceptions levées par la DLL de procédure stockée étendue soient gérées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il est possible d'endommager les zones de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. À titre de mesure de sécurité, seuls les administrateurs systèmes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent ajouter des procédures stockées étendues à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces procédures doivent être testées entièrement avant d'être installées.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de procédures stockées étendues](database-engine-extended-stored-procedures-programming.md)   
 [Interrogation des procédures stockées étendues installées dans SQL Server](querying-extended-stored-procedures-installed-in-sql-server.md)  
  
  
