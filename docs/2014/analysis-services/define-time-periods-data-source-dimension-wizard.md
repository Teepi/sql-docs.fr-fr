---
title: Définir des périodes (Source de données) (Assistant Dimension) | Microsoft Docs
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
- sql12.asvs.dimensionwizard.timeperioddefinition.f1
ms.assetid: a5e6b9ff-69fa-4896-a840-de2b3e063ca9
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3b62c3da0e8a92eda40d883a596e862a6c679364
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328859"
---
# <a name="define-time-periods-data-source-dimension-wizard"></a>Définir des périodes (Source de données - Assistant Dimension)
  La page **Définir des périodes** permet de définir des attributs représentant des périodes dans la dimension de temps à l'aide de colonnes dans la table indiquée sur la page **Sélectionner le type de la dimension** .  
  
> [!NOTE]  
>  Cette page ne s’affiche que si vous avez coché la case **Construire la dimension en utilisant une source de données** dans la page **Définition des dimensions** et la case **Dimension de temps** dans la page **Sélectionner le type de la dimension** .  
  
## <a name="options"></a>Options  
 **Nom de la propriété de temps**  
 Permet d'afficher les types d'attributs utilisés dans le but d'indiquer les périodes se trouvant dans les dimensions de temps. Pour plus d’informations sur les types d’attributs, consultez [Élément Type &#40;DimensionAttribute&#41; &#40;ASSL&#41;](scripting/properties/type-element-dimensionattribute-assl.md).  
  
> [!NOTE]  
>  Le type `Date` ne doit être utilisé que pour les colonnes de type de données DateTime (date et heure).  
  
 **Colonnes de Table de temps**  
 Répertorie les colonnes sur lesquelles les types d'attribut correspondant doivent s'appuyer.  
  
 Pour changer de colonne, cliquez sur la colonne, puis sélectionnez-en une autre dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 de l’Assistant Dimension](dimension-wizard-f1-help.md)   
 [Dimensions &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
