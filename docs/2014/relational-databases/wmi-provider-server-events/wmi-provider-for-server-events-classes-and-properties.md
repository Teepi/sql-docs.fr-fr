---
title: Fournisseur WMI pour les événements serveur Classes et propriétés | Microsoft Docs
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
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
caps.latest.revision: 33
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 53e9629a8e3bad2ee14f61453a15dfe558165f05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152230"
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a>Fournisseur WMI pour les classes et propriétés d'événements serveur
  Les événements serveur suivants composent le modèle de programmation du fournisseur WMI pour les événements serveur. Deux catégories principales d'événements peuvent être interrogées en émettant des requêtes WQL sur le fournisseur. Il s'agit des événements DDL (Data Definition Language) et des événements de trace. Les événements de Service Broker QUEUE_ACTIVATION et BROKER_QUEUE_DISABLED peuvent également être interrogés. Notez la nature inclusive des arborescences suivantes. L'événement DDL_ASSEMBLY_EVENTS, par exemple, inclut tout événement ALTER_ASSEMBLY, CREATE_ASSEMBLY et DROP_ASSEMBLY. De la même façon, l'événement TRC_FULL_TEXT inclut tout événement FT_CRAWL_ABORTED, FT_CRAWL_STARTED et FT_CRAWL_STOPPED. ALL_EVENTS couvre tous les événements DDL, événements de trace, QUEUE_ACTIVATION et BROKER_QUEUE_DISABLED.  
  
 Pour savoir quelles propriétés d'un événement ou d'un groupe d'événements peuvent être interrogées, reportez-vous au schéma d'événement. Par défaut, le schéma d'événement est installé dans le répertoire suivant : [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events .xsd.  
  
 Ou bien, vous pouvez consulter le schéma d’événement publié à [ http://schemas.microsoft.com/sqlserver ](http://go.microsoft.com/fwlink/?linkid=43100).  
  
 Par exemple, si vous consultez l'événement ALTER_DATABASE, vous apprendrez que son événement parent est DDL_SERVER_LEVEL_EVENTS et que ses propriétés sont `TSQLCommand` et `DatabaseName`. Cet événement hérite également des propriétés `SQLInstance`, `PostTime`, `ComputerName`, `SPID` et `LoginName`. Il ne possède pas d'événements enfants.  
  
> [!NOTE]  
>  Les procédures stockées système qui exécutent des opérations de type DDL peuvent également déclencher des notifications d'événements. Testez vos notifications d'événements pour déterminer leur réponse aux procédures stockées du système qui sont exécutées. Par exemple, l’instruction CREATE TYPE et **sp_addtype** procédure stockée activeront toutes deux une notification d’événement qui est créée sur un événement CREATE_TYPE. Pour plus d’informations, consultez[événements DDL](../../relational-databases/triggers/ddl-events.md).  
  
 **Événements de langage de définition de données et les groupes d’événements**  
  
 ![Fournisseur WMI pour les événements événements arborescence](../../../2014/database-engine/dev-guide/media/sql-wmi-ddl-events-ktm.gif "fournisseur WMI pour l’arborescence de d’événements de serveur")  
  
 **Événements de trace et groupes d’événements**  
  
 ![Événements de trace et groupes d’événements](../../../2014/database-engine/dev-guide/media/sql-wmi-trc-all-events.gif "et groupes d’événements de Trace")  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseur WMI pour les Concepts des événements de serveur](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)   
 [Utilisation de WQL avec le fournisseur WMI pour les événements de serveur](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  
