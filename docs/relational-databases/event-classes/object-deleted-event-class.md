---
title: Object:Deleted, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Object:Deleted event class
ms.assetid: d4db32bc-972d-4429-809a-a62047c33e79
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 8afb41d09efe51eb19544521d8bd44fea196f9d7
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561019"
---
# <a name="objectdeleted-event-class"></a>Object:Deleted (classe d'événements)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La classe d'événements Object:Deleted indique qu'un objet a été supprimé, par exemple avec les instructions DROP INDEX et DROP TABLE. Cette classe d'événements permet de déterminer si des objets sont supprimés, par exemple par des applications ODBC qui créent fréquemment des procédures stockées temporaires.  
  
 En surveillant les colonnes de données par défaut LoginName et NTUserName en plus des classes d'événements Objects, vous pouvez déterminer le nom de l'utilisateur qui crée, supprime ou accède aux objets.  
  
## <a name="objectdeleted-event-class-data-columns"></a>Colonnes de données de la classe d'événements Object:Deleted  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|ClientProcessID|**Int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|DatabaseID|**Int**|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|DatabaseName|**nvarchar**|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|EventClass|**Int**|Type d’événement = 47.|27|non|  
|EventSequence|**Int**|Séquence d'un événement donné au sein de la demande.|51|non|  
|EventSubClass|**Int**|Type de sous-classe d'événements.<br /><br /> 0=Début<br /><br /> 1=Validation<br /><br /> 2=Annulation|21|Oui|  
|GroupID|**Int**|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|HostName|**nvarchar**|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IndexID|**Int**|ID de l'index de l'objet affecté par l'événement. Pour déterminer l'ID d'index d'un objet, utilisez la colonne index_id de l'affichage catalogue sys.indexes.|24|Oui|  
|IntegerData|**Int**|Valeur entière qui dépend de la classe d'événements capturée dans la trace.|25|Oui|  
|IsSystem|**Int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|LoginName|**nvarchar**|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).|11|Oui|  
|LoginSid|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|NTDomainName|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|NTUserName|**nvarchar**|Nom d'utilisateur Windows.|6|Oui|  
|ObjectID|**Int**|ID affecté à l'objet par le système.|22|Oui|  
|ObjectID2|**bigint**|ID de l'objet ou de l'entité associé.|56|Oui|  
|ObjectName|**nvarchar**|Nom de l'objet référencé.|34|Oui|  
|ObjectType|**Int**|Valeur représentant le type de l'objet qui intervient dans l'événement. Cette valeur correspond à la colonne de type dans sysobjects. Pour connaître les valeurs, consultez [Colonne d’événements de trace ObjectType](../../relational-databases/event-classes/objecttype-trace-event-column.md).|28|Oui|  
|RequestID|**Int**|ID de la demande contenant l'instruction.|49|Oui|  
|ServerName|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|SessionLoginName|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le nom Connexion1 et que vous exécutez une instruction en tant que Connexion2, SessionLoginName affiche Connexion1 et LoginName, Connexion2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|SPID|**Int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|StartTime|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|TransactionID|**bigint**|ID affecté par le système à la transaction.|4|Oui|  
|XactSequence|**bigint**|Jeton utilisé pour décrire la transaction en cours.|50|Oui|  
  
## <a name="see-also"></a> Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
