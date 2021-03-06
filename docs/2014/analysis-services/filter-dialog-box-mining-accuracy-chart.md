---
title: Filtrer la boîte de dialogue (graphique de précision d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 71e884a9-7ec4-4459-a4c4-87f6c796d478
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04630120106816c4018af0fc23cfdf30f26b15cf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272605"
---
# <a name="filter-dialog-box-mining-accuracy-chart"></a>Filtrer, boîte de dialogue (Graphique d'analyse de précision de l'exploration de données)
  La boîte de dialogue **Filtre** vous permet de générer des conditions que vous pouvez appliquer à un jeu de données. Le jeu de données peut être un jeu de données externe utilisé pour le test, ou les données de cas utilisées pour l'apprentissage d'un modèle d'exploration de données. Cette boîte de dialogue vous permet de générer des critères que vous pouvez enregistrer comme parties intégrantes de critères de filtre plus complexes dans la boîte de dialogue **Filtre de jeu de données** ou dans la boîte de dialogue **Filtre de modèle** .  
  
-   La boîte de dialogue **Filtre de jeu de données** est accessible à partir de l’onglet **Sélection d’entrée** du concepteur **Graphique d’analyse de précision de l'exploration de données** .  
  
-   La boîte de dialogue **Filtre de modèle** est accessible sous l’onglet **Modèles d’exploration de données** du concepteur d’exploration de données.  
  
 Si vous appliquez un filtre à un modèle d’exploration de données, commencez par utiliser la boîte de dialogue **Filtre de modèle** pour choisir une table. Ensuite, utilisez la boîte de dialogue **Filtre** pour générer des conditions qui s’appliquent uniquement à cette table.  
  
 Si vous créez un filtre à appliquer à un jeu de données de test externe, utilisez dans un premier temps la boîte de dialogue **Filtre de jeu de données** pour choisir une table dans la liste des tables d’une vue de source de données. Ensuite, utilisez la boîte de dialogue **Filtre** pour générer des conditions qui s’appliquent uniquement à cette table.  
  
 Après avoir créé un ensemble de conditions qui s’appliquent à une table individuelle, [!INCLUDE[clickOK](../includes/clickok-md.md)]. Les modifications que vous avez apportées dans la boîte de dialogue **Filtre** sont automatiquement ajoutées à l’expression de filtre dans la boîte de dialogue parente, **Filtre de jeu de données** ou **Filtre de modèle**.  
  
 Si vous appliquez le filtre au nouveau jeu de données, le modèle d'exploration de données existant est utilisé pour évaluer uniquement les cas du jeu de données qui remplissent les conditions. Toutefois, si vous appliquez le filtre au modèle d'exploration de données lui-même, la précision du modèle est évaluée pour uniquement les cas du modèle d'exploration de données qui répondent à ces critères.  
  
 **Pour plus d’informations :** [Test et validation &#40;exploration de données&#41;](data-mining/testing-and-validation-data-mining.md)  
  
## <a name="options"></a>Options  
 **Conditions**  
 Grille qui contient des colonnes dans lesquelles vous spécifiez des conditions sur les colonnes de la table que vous avez sélectionnée dans la boîte de dialogue **Filtre de jeu de données** .  
  
|Valeur|Description|  
|-----------|-----------------|  
|**et/ou**|Cliquez sur cette option pour spécifier s'il faut appliquer l'opérateur AND ou l'opérateur OR à la condition figurant sur cette ligne. Ces valeurs ne sont disponibles qu’une fois que vous avez sélectionné une colonne dans la liste **Colonne de la structure d’exploration de données** .|  
|**Colonne de Structure d’exploration de données**|Cliquez sur cette option pour sélectionner une colonne dans la liste des colonnes contenues dans la table que vous avez sélectionnée à partir de la source de données dans la boîte de dialogue **Filtre de jeu de données** .|  
|**Opérateur**|Sélectionnez un opérateur dans la liste. Les opérateurs disponibles dépendent du type de données de la colonne.<br /><br /> Si la colonne contient des valeurs discrètes, seuls les opérateurs suivants sont disponibles :<br /><br /> = (égal à), <>(différent de), IS NOT NULL, IS NULL.<br /><br /> Si la colonne contient des valeurs continues, les opérateurs utilisés pour les opérations « supérieur à » et « inférieur à » sont également pris en charge.|  
|**Value**|Tapez une valeur à utiliser comme condition.|  
  
## <a name="see-also"></a>Voir aussi  
 [Test et des tâches de Validation et des procédures &#40;exploration de données&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Concepteur graphique d’analyse de précision d’exploration de données &#40;exploration de données&#41;](mining-accuracy-chart-designer-data-mining.md)  
  
  
