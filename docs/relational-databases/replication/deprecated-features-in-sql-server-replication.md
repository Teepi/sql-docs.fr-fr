---
title: Fonctionnalités dépréciées dans la réplication SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deprecated features [SQL Server replication]
ms.assetid: 46bd3edd-d6de-40a6-a015-21cce8321feb
caps.latest.revision: 67
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 23c3395ce12f5a2d60c9c2472f6c4db39394e7d6
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37353441"
---
# <a name="deprecated-features-in-sql-server-replication"></a>Fonctionnalités déconseillées dans la réplication SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique décrit les fonctionnalités de réplication déconseillées qui sont toujours disponibles dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Il est prévu que ces fonctionnalités soient supprimées dans une prochaine version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les fonctions déconseillées ne doivent pas être utilisées dans de nouvelles applications.  
  
## <a name="items-deprecated-in-includesssql15includessssql15-mdmd"></a>Éléments déconseillés dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|La réplication est prise en charge si chaque point de terminaison [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se trouve dans deux versions principales de la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par conséquent, [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ne prend pas en charge la réplication vers ou depuis [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].|  
|[!INCLUDE[ssEW](../../includes/ssew-md.md)]|La réplication est prise en charge si chaque point de terminaison [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se trouve dans deux versions principales de la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par conséquent, [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ne prend pas en charge la réplication vers ou depuis [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
  
## <a name="see-also"></a> Voir aussi  
 [Compatibilité descendante de la réplication](../../relational-databases/replication/replication-backward-compatibility.md)  
  
  
