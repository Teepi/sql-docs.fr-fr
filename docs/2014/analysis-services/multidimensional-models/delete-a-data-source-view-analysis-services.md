---
title: Supprimer une vue de Source de données (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting data source views
- data source views [Analysis Services], deleting
- removing data source views
ms.assetid: ae3f5ca0-ecbf-4b52-8386-eb457719d854
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c8d04731a4b555b6e4afe9c8697fc5c4f907a9a1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284017"
---
# <a name="delete-a-data-source-view-analysis-services"></a>Supprimer une vue de source de données (Analysis Services)
  Si vous n’utilisez plus de vue de source de données (DSV) dans un projet OLAP, vous pouvez la supprimer du projet dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
 La suppression d'une vue DSV est définitive. Vous ne pouvez pas restaurer une vue DSV supprimée dans un projet ou une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Les vues de source de données (DSV) dont dépendent d’autres objets ne peuvent pas être supprimées d’une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ouverte par [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] en mode en ligne. Pour supprimer une vue DSV d'un projet qui est connecté à une base de données s'exécutant sur un serveur, vous devez d'abord supprimer tous les objets de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui dépendent de cette vue DSV avant de supprimer la vue DSV elle-même.  
  
 La suppression d'une vue DSV invalidera d'autres objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui dépendent d'elle ; par conséquent, avant de supprimer la vue DSV, vous verrez la liste des objets qui deviendront non valides une fois la vue DSV supprimée. Examinez cette liste avec soin pour vous assurer qu'elle n'inclut pas les objets que vous vous attendez toujours à utiliser.  
  
 ![Supprimer la boîte de dialogue objets](../media/ssas-olapdsv-deleteobjects.gif "boîte de dialogue Supprimer les objets")  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](data-source-views-in-multidimensional-models.md)   
 [Modifier les propriétés d’une vue de Source de données &#40;Analysis Services&#41;](change-properties-in-a-data-source-view-analysis-services.md)  
  
  
