---
title: Broker:Conversation Group, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Conversation Group event class
ms.assetid: 6595bef6-9d40-42eb-a934-735622dd23fb
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b66505d8c7e33aecbe4bc52e22ded57514b77bf0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37195287"
---
# <a name="brokerconversation-group-event-class"></a>Broker:Conversation Group, classe d'événements
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génère un événement **Broker:Conversation Group** lorsque Service Broker crée un groupe de conversion ou supprime un groupe existant.  
  
## <a name="brokerconversation-group-event-class-data-columns"></a>Colonnes de données de la classe d'événement Broker:Conversation Group  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|**ClientProcessID**|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|**DatabaseID**|`int`|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**EventClass**|`int`|Type de classe d'événements capturée. Toujours **136** pour **Broker:Conversation Group**.|27|non|  
|**EventSequence**|`int`|Numéro de séquence de cet événement.|51|non|  
|**EventSubClass**|`nvarchar`|Type de sous-classe d’événements, qui fournit des informations complémentaires concernant chaque classe d’événements. Cette colonne peut contenir les valeurs suivantes :<br /><br /> **Créer**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a créé un nouveau groupe de conversation.<br /><br /> **Supprimer**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a supprimé un groupe de conversation.|21|Oui|  
|**GUID**|`uniqueidentifier`|ID du groupe de conversation que cet événement décrit.|54|non|  
|**HostName**|`nvarchar`|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**IsSystem**|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|non|  
|**LoginSid**|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|`nvarchar`|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|**ServerName**|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|**SPID**|`int`|ID du processus serveur affecté par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au processus associé au client.|12|Oui|  
|**StartTime**|`datetime`|Heure de début de l'événement, le cas échéant.|14|Oui|  
|**TransactionID**|`bigint`|ID affecté à la transaction par le système.|4|non|  
  
  
