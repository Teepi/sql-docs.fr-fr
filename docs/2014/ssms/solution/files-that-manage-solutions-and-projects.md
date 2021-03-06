---
title: Fichiers gérant les solutions et les projets | Microsoft Docs
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
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b2e52799292a0272cc31efb6fb6d31ca5285731e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257805"
---
# <a name="files-that-manage-solutions-and-projects"></a>Fichiers gérant les solutions et les projets
  Cette rubrique décrit les types de fichiers propres à [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Par défaut, toutes les solutions et leurs projets sont créés dans \Mes documents\SQL Server Management Studio\Projects.  
  
## <a name="management-studio-solution-files"></a>Fichiers solutions Management Studio  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] utilise d’autres types de fichiers que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio. Cela signifie que vous ne pouvez pas ouvrir une solution [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou dans Visual Studio. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Les fichiers solutions permettent à l’Explorateur de solutions d’afficher une interface graphique pour gérer vos fichiers.  
  
|Extension|Type de fichier|Description|Créé par|  
|---------------|---------------|-----------------|----------------|  
|.ssmssln|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Objet Solution|Fournit l’environnement avec des références à l’emplacement sur le disque des projets, des éléments de projets et de la solution [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
  
## <a name="management-studio-project-files"></a>Fichiers projet Management Studio  
 À l'instar des solutions qui contiennent des fichiers solutions qui gèrent les objets d'une solution, les projets contiennent des fichiers projet. Le type de fichier projet créé par [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour un projet dépend du modèle utilisé pour créer le projet. Le tableau ci-dessous décrit le type de fichier créé pour chaque projet.  
  
|Extension|Modèle de projet|  
|---------------|----------------------|  
|.ssmssqlproj|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Projet de script|  
|.ssmsasproj|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projet de script|  
  
## <a name="location-of-solution-level-files"></a>Emplacement des fichiers de niveau solution  
 Par défaut, les fichiers de niveau solution sont créés dans le répertoire physique du premier projet créé avec la solution. Vous pouvez spécifier un répertoire pour la solution lors de la création d'une solution ou lors de la création d'un nouveau projet.  
  
 Si votre structure de répertoires est identique à la structure logique affichée dans l'Explorateur de solutions, il est plus facile de trouver et de partager les fichiers solutions et projet avec d'autres développeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer des fichiers avec encodage](manage-files-with-encoding.md)   
 [Fichiers divers](miscellaneous-files.md)   
 [Explorateur de solutions](solution-explorer.md)   
 [Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md)   
 [Projets &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md)   
 [Contrôle de code source de l'Explorateur de solutions](../../database-engine/solution-explorer-source-control.md)  
  
  
