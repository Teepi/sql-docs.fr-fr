---
title: Traitement et les emplacements de stockage (Assistant Partition) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifyprocessingandstorage.f1
ms.assetid: dda2dc57-923d-4db9-93a7-38e95770f3df
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eae2e7c380b7b0de69047079edac87d273f07d52
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286055"
---
# <a name="processing-and-storage-locations-partition-wizard"></a>Emplacements pour le traitement et le stockage (Assistant Partition)
  Utilisez la page **Emplacements pour le traitement et le stockage** pour spécifier l’instance [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]du cube qui possède la partition, ainsi que l’instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] qui stocke les données de la partition. Vous pouvez définir une partition distante en spécifiant une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] distante ou un emplacement de stockage différent de l'emplacement par défaut. Pour plus d’informations sur les partitions distantes, consultez [Partitions distantes](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md).  
  
## <a name="processing-location-options"></a>Options d'emplacement du traitement  
 **Instance de serveur actuelle**  
 Rend l'instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] active responsable du traitement de la partition.  
  
 **Source de données Analysis Services distante**  
 Rend une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] distante responsable du traitement de cette partition.  
  
 Dans la liste déroulante, sélectionnez la source de données qui représente l'instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] distante qui sera responsable du traitement de la partition.  
  
> [!NOTE]  
>  Une erreur se produit si vous sélectionnez une source de données dans laquelle la propriété de la chaîne de connexion `Initial Catalog` ne définit pas une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] valide ou si la base de données spécifiée dans la chaîne de connexion `Initial Catalog` ne prend pas en charge les partitions distantes (autrement dit, si la propriété `MasterDatasourceID` de la base de données n'est pas configurée avec une valeur valide).  
  
 **Nouveau**  
 Crée une nouvelle source de données qui représente l'instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] distante responsable du traitement de la partition.  
  
## <a name="storage-location-options"></a>Options de l'emplacement de stockage  
 **Emplacement du serveur par défaut**  
 Le dossier de données de l'instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] active est l'emplacement de stockage des données d'agrégation et d'indexation de la partition.  
  
 **Dossier spécifié**  
 Emplacement de stockage des données d'agrégation et d'indexation de la partition.  
  
 **...**  
 Affiche la boîte de dialogue **Rechercher un dossier distant** dans laquelle vous sélectionnez un dossier pour l’option **Dossier spécifié**.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 de l’Assistant de partition &#40;Analysis Services - données multidimensionnelles&#41;](partition-wizard-f1-help-analysis-services-multidimensional-data.md)   
 [Partitions &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Recherchez la boîte de dialogue dossier distant &#40;Analysis Services - données multidimensionnelles&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)  
  
  
