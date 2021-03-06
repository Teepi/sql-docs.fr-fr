---
title: Appliquer un filtre à un modèle d’exploration de données | Microsoft Docs
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
- model filter [data mining]
- filters [data mining]
- filtering input rows [Analysis Services]
- filtering data [Analysis Services]
ms.assetid: 4d0abeb5-e939-46d3-9097-6e0358244300
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0f550dde21f45d7850db5cc6a27d2247c565dcee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253201"
---
# <a name="apply-a-filter-to-a-mining-model"></a>Appliquer un filtre à un modèle d'exploration de données
  Si votre structure d'exploration de données contient une table imbriquée, vous pouvez appliquer un filtre à la table de cas, à la table imbriquée, ou aux deux.  
  
 La procédure suivante indique comment créer les deux types de filtres : filtres de cas et filtres sur les lignes de la table imbriquée.  
  
 La condition sur la table de cas restreint les clients à ceux dont le revenu se situe entre 30000 et 40000. La condition sur la table imbriquée restreint les clients à ceux qui n'ont pas acheté d'élément particulier.  
  
 La condition de filtre complète créée dans cet exemple se présente comme suit :  
  
```  
[Income] > '30000'   
AND  [Income] < '40000'   
AND EXISTS (SELECT * FROM [<nested table name>]   
WHERE [Model] <> 'Water Bottle' )   
```  
  
### <a name="to-create-a-case-filter-on-a-mining-model"></a>Pour créer un filtre de cas sur un modèle d'exploration de données  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dans l'Explorateur de solutions, cliquez sur la structure d'exploration de données qui contient le modèle d'exploration de données à filtrer.  
  
2.  Cliquez sur l'onglet **Modèles d'exploration de données** .  
  
3.  Sélectionnez le modèle et cliquez avec le bouton droit pour ouvrir le menu contextuel.  
  
     - ou -  
  
     Sélectionnez le modèle. Puis, dans le menu **Modèle d'exploration de données** , sélectionnez **Définir le filtre de modèle**.  
  
4.  Dans la boîte de dialogue **Filtre de modèle** , cliquez sur la ligne supérieure dans la grille, dans la zone de texte **Colonne de la structure d'exploration de données** .  
  
5.  Si la source de données contient une table plate unique, la liste déroulante affiche uniquement les noms des colonnes dans cette table.  
  
     Si la structure d'exploration de données contient plusieurs tables, la liste affiche les noms des tables sources. Les noms de colonne n'apparaissent pas jusqu'à ce qu'une table ait été sélectionnée.  
  
     Si la structure d'exploration de données contient une table de cas et une table imbriquée, la liste déroulante affiche des colonnes de la table de cas et le nom de la table imbriquée.  
  
6.  Sélectionnez une colonne dans la liste déroulante.  
  
     L'icône située à gauche de la zone de texte change pour indiquer que l'élément sélectionné est une table ou une colonne.  
  
7.  Cliquez sur la zone de texte **Opérateur** et sélectionnez un opérateur dans la liste. Les opérateurs valides changent selon le type de données de la colonne que vous avez sélectionnée.  
  
8.  Cliquez sur la zone de texte **Valeur** et tapez une valeur dans la zone.  
  
     Par exemple, sélectionnez `Income` que la colonne, sélectionnez le plus grand que l’opérateur (>) et tapez `30000`.  
  
9. Cliquez sur la ligne suivante dans la grille.  
  
     La condition de filtre que vous avez créée est ajoutée automatiquement à la zone de texte Expression. Par exemple : `[Income] > '30000'`  
  
10. Cliquez sur la zone de texte **AND/OR** dans la ligne suivante de la grille pour ajouter une condition.  
  
     Par exemple, pour créer une condition BETWEEN, sélectionnez `AND` dans la liste déroulante d’opérandes logiques.  
  
11. Sélectionnez un opérateur et tapez une valeur comme décrit dans les étapes 7 et 8.  
  
     Par exemple, sélectionnez `Income` que la colonne à nouveau, sélectionnez l’opérateur inférieur à (<), puis tapez `40000`.  
  
12. Cliquez sur la ligne suivante dans la grille.  
  
13. La condition de filtre dans la zone de texte Expression est automatiquement mise à jour pour inclure la nouvelle condition. L'expression complétée se présente comme suit : `[Income] > '30000'AND [Income] < '40000'`  
  
### <a name="to-add-a-filter-on-the-nested-table-in-a-mining-model"></a>Pour ajouter un filtre sur la table imbriquée dans un modèle d'exploration de données  
  
1.  Dans le  **\<nom > filtre de modèle** boîte de dialogue, cliquez sur une ligne vide dans la grille sous **colonne de Structure d’exploration de données**.  
  
2.  Sélectionnez le nom de la table imbriquée dans la liste déroulante.  
  
     L'icône située à gauche de la zone de texte change pour indiquer que l'élément sélectionné est le nom d'une table.  
  
3.  Cliquez sur la zone de texte **Opérateur** et sélectionnez **Contient** ou **Ne contient pas**.  
  
     Ce sont les seules conditions disponibles pour la table imbriquée dans la boîte de dialogue **Filtre de modèle** , car vous restreignez la table de cas uniquement aux cas qui contiennent une certaine valeur dans la table imbriquée. Vous allez définir la valeur pour la condition sur la table imbriquée lors de l'étape suivante.  
  
4.  Cliquez sur la zone **Valeur** , puis sur le bouton **(…)** pour générer une expression.  
  
     Le  **\<nom > filtre** boîte de dialogue s’ouvre. Cette boîte de dialogue peut définir des conditions uniquement sur la table actuelle, qui est la table imbriquée dans ce cas.  
  
5.  Cliquez sur la zone **Colonne de la structure d'exploration de données** et sélectionnez un nom de colonne dans les listes déroulantes des colonnes de la table imbriquée.  
  
6.  Cliquez sur **Opérateur** et sélectionnez un opérateur dans la liste d'opérateurs valides pour la colonne.  
  
7.  Cliquez sur **Valeur** et tapez une valeur.  
  
     Par exemple, pour **colonne de Structure d’exploration de données,** sélectionnez `Model`. Pour **opérateur**, sélectionnez `<>`, puis tapez la valeur `Water Bottle`. Cette condition crée l'expression de filtre suivante :  
  
```  
EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] <> 'Water Bottle' )   
```  
  
> [!NOTE]  
>  Puisque le nombre d'attributs de table imbriquée est potentiellement illimité, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne fournit pas de liste de valeurs possibles à sélectionner. Vous devez taper la valeur exacte. En outre, vous ne pouvez pas utiliser d'opérateur LIKE dans une table imbriquée.  
  
1.  Ajouter d’autres conditions en fonction des besoins, combinez des conditions en sélectionnant `AND` ou `OR` dans le **et/ou** située à gauche de la **Conditions** grille. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
2.  Dans la boîte de dialogue **Filtre de modèle** , examinez les conditions que vous avez créées en utilisant la boîte de dialogue **Filtre** . Les conditions pour la table imbriquée sont ajoutées aux conditions pour la table de cas, tandis que le jeu complet de conditions de filtre est affiché dans la zone de texte **Expression** .  
  
3.  Cliquez éventuellement sur **Modifier la requête** pour modifier manuellement l'expression de filtre.  
  
    > [!NOTE]  
    >  Si vous modifiez manuellement quelque partie que ce soit d'une expression de filtre, la grille est alors désactivée et vous devez utiliser l'expression de filtre en mode édition de texte uniquement. Pour restaurer le mode de modification de grille, vous devez effacer l'expression de filtre et recommencer.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Filtres pour les modèles d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-models-analysis-services-data-mining.md)   
 [Tâches du modèle d’exploration de données et procédures](mining-model-tasks-and-how-tos.md)   
 [Supprimer un filtre d’un modèle d’exploration de données](delete-a-filter-from-a-mining-model.md)  
  
  
