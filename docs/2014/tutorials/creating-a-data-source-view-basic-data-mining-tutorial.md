---
title: Création d’un Data Source View (didacticiel d’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c1e68a88-0f82-415d-becc-78d180d4f845
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2b64202ccd2b5f420eceeb0287407656dde1cefe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241839"
---
# <a name="creating-a-data-source-view-basic-data-mining-tutorial"></a>Création d'une vue de source de données (Didacticiel sur l'exploration de données de base)
  Une vue de source de données est créée à partir d'une source de données et définit un sous-ensemble des données, que vous pouvez ensuite utiliser dans vos structures d'exploration de données. Vous pouvez également utiliser la vue de source de données pour ajouter des colonnes, créer des colonnes calculées et des agrégats, et ajouter des vues nommées. En utilisant des vues de source de données, vous pouvez sélectionner les données qui se rapportent à un projet en particulier, établir des relations entre les tables et modifier la structure des données, sans modifier la source de données d'origine. Pour plus d’informations, consultez [Vues de sources de données dans les modèles multidimensionnels](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
### <a name="to-create-a-data-source-view"></a>Pour créer une vue de source de données  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **les vues de sources de données**, puis sélectionnez **nouvelle vue de Source de données**.  
  
2.  Dans la page **Assistant Vue de source de données** , cliquez sur **Suivant**.  
  
3.  Sur le **sélectionner une Source de données** page sous **sources de données relationnelles**, sélectionnez la source de données Adventure Works DW 2012 que vous avez créé dans la dernière tâche. Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Si vous souhaitez créer une source de données, cliquez sur **des Sources de données** puis cliquez sur **nouvelle Source de données** pour démarrer l’Assistant Source de données.  
  
4.  Sur le **sélectionner des Tables et vues** page, sélectionnez les objets suivants, puis cliquez sur la flèche droite pour les inclure dans la nouvelle vue de source de données :  
  
    -   **ProspectiveBuyer (dbo)** -table des futurs acheteurs de vélos  
  
    -   **vTargetMail (dbo)** -vue des données historiques des cours acheteurs de vélo  
  
5.  Cliquez sur **Suivant**.  
  
6.  Sur le **fin de l’Assistant** page, Adventure Works DW 2012 est nommée par défaut à la vue de source de données. Remplacez le nom par `Targeted Mailing`, puis cliquez sur **Terminer**.  
  
     La nouvelle vue de source de données s’ouvre dans le **Targeted Mailing.dsv [conception]** onglet.  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Création d’une Source de données &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Leçon suivante  
 [Leçon 2 : Création d’une Structure de publipostage ciblé &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des données d’une vue de Source &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/defining-a-data-source-view-analysis-services.md)  
  
  
