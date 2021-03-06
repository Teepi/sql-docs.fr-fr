---
title: Copier un état de facette de gestion basée sur des stratégies dans un fichier XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2eb0cbc05660a71e9058261f627d3b26cf68560d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198859"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a>Copier un état de facette de gestion basée sur des stratégies dans un fichier XML
  Cette rubrique explique comment copier l'état d'une facette de gestion basée sur des stratégies dans un fichier XML dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour copier un état de facette dans un fichier XML à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Les procédures de cette rubrique nécessite l’appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a>Pour copier un état de facette dans un fichier XML  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un objet d’instance, une base de données ou un objet de base de données, puis cliquez sur **Facettes**.  
  
2.  Dans la boîte de dialogue *Afficher les facettes –***nom_objet*, cliquez sur **Exporter l’état actuel en tant que stratégie**.  
  
3.  Dans la boîte de dialogue **Exporter en tant que stratégie** , tapez le nom et le chemin du fichier ou utilisez le bouton Parcourir (**...**) pour rechercher le fichier, puis tapez le nom du fichier XML. Pour plus d'informations sur les options disponibles dans cette boîte de dialogue, consultez [Export As Policy Dialog Box](export-as-policy-dialog-box.md).  
  
4.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  
