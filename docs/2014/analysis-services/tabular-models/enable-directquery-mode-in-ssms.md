---
title: Configurer l’accès de DirectQuery pour une base de données de modèle tabulaire ou de In-Memory | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ee6b2f55d1b630b489f65e16a39cb602d5fd5a6d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243439"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a>Configurer l'accès In-Memory ou DirectQuery pour une base de données model tabulaire
  Cette rubrique explique comment modifier les propriétés de connexion d'un modèle tabulaire qui a déjà été déployé afin d'activer l'utilisation du modèle en mode de requête directe.  
  
 Pour plus d’informations sur ces propriétés et la configuration pour les scénarios les plus courants, consultez [les scénarios de déploiement DirectQuery &#40;tabulaire SSAS&#41;](../directquery-deployment-scenarios-ssas-tabular.md).  
  
## <a name="requirements"></a>Spécifications  
 L'activation de l'utilisation du mode de requête directe sur un modèle tabulaire est un processus qui implique plusieurs étapes. Il le faut :  
  
1.  Vérifiez que le modèle n'a pas de fonctionnalités susceptibles de provoquer des erreurs de validation en mode de requête directe.  
  
2.  Modifiez le mode de stockage sur le modèle pour prendre en charge la requête directe.  
  
3.  Déployez le modèle dans un mode qui prend en charge les requêtes en mode hybride ou en mode de requête directe pur.  
  
4.  Modifiez la chaîne de connexion dans la base de données déployée pour prendre en charge le mode de requête directe.  
  
 Cette rubrique suppose que vous avez créé et validé votre modèle, et que vous devez uniquement activer l'accès aux requêtes directes à partir d'un client tel que [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].  
  
## <a name="procedure"></a>Procédure  
  
#### <a name="change-the-connection-string-properties-of-the-model"></a>Modifier les propriétés de chaîne de connexion du modèle  
  
1.  Dans SQL Server Management Studio, ouvrez l'instance sur laquelle vous avez déployé le modèle.  
  
2.  Dans l’Explorateur d’objets, cliquez sur le nom de la base de données de modèle, puis sélectionnez **propriétés**.  
  
3.  Recherchez la propriété, **DirectQueryMode**. Pour activer l'utilisation de la source de données relationnelles, cette propriété doit être définie avec l'une des valeurs suivantes :  
  
    -   **DirectQuery**  
  
    -   **InMemoryWithDirectQuery**  
  
    -   **DirectQueryWithInMemory**  
  
  
