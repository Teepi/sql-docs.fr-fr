---
title: Propriétés de mémoire partagée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fe28d3a716403975170c2d0b5deea2564b688c89
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244119"
---
# <a name="shared-memory-properties"></a>Propriétés de Mémoire partagée
  La page **Protocole** de la boîte de dialogue **Propriétés de Mémoire partagée** permet d’activer ou de désactiver le protocole de mémoire partagée. Il s'agit du protocole le plus simple à utiliser et pour lequel aucun paramètre ne doit être configuré. Étant donné que les clients qui utilisent le protocole de mémoire partagée peuvent se connecter uniquement à une instance [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécutée sur le même ordinateur, ce protocole n’est généralement pas utile pour les activités de base de données. Utilisez le protocole de mémoire partagée pour débloquer une situation dans laquelle vous suspectez que les autres protocoles ne sont pas configurés correctement.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être redémarré pour activer ou désactiver le protocole.  
  
## <a name="options"></a>Options  
 **Activé**  
 Les valeurs possibles sont **Yes** et **No**. Le protocole de mémoire partagée est activé par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d’un protocole réseau](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Création d'une chaîne de connexion valide à l'aide du protocole de mémoire partagée](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
