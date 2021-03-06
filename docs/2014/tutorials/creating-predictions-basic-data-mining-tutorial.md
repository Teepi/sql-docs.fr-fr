---
title: Création de prédictions (didacticiel d’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8410ed2-bb98-4d51-a9eb-b239be1201c2
caps.latest.revision: 42
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 64045eb4a87794e3d4b870ddb3ede28e48af2ce2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267965"
---
# <a name="creating-predictions-basic-data-mining-tutorial"></a>Création de prédictions (Didacticiel sur l'exploration de données de base)
  Une fois que vous avez testé la précision de vos modèles d’exploration de données et décidé que vous êtes satisfait des résultats, vous pouvez ensuite générer des prédictions à l’aide du Générateur de requêtes de prédiction sur le **prévision de modèle d’exploration de données** onglet dans l’exploration de données Concepteur.  
  
 Le Générateur de requêtes de prédiction a trois vues. Avec le **conception** et **requête** vues, vous pouvez générer et examiner votre requête. Vous pouvez ensuite exécuter la requête et afficher les résultats dans le **résultat** vue.  
  
 Toutes les requêtes de prédictions utilisent DMX, qui est l'abréviation du langage Data Mining Extensions (DMX). DMX a une syntaxe similaire à celle de T-SQL mais est utilisée pour des requêtes sur des objets d'exploration de données. Bien que la syntaxe DMX n’est pas complexe, à l’aide d’un générateur de requêtes comme celle-ci, ou celui de la [SQL Server Data Mining Add-Ins pour Office](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md), facilite la sélection des entrées et créer des expressions, donc nous vous recommandons vivement que vous allez principes de base.  
  
## <a name="creating-the-query"></a>Création de la requête  
 La première étape dans la création d'une requête de prédiction consiste à sélectionner un modèle d'exploration de données et une table d'entrée.  
  
#### <a name="to-select-a-model-and-input-table"></a>Pour sélectionner un modèle et une table d'entrée  
  
1.  Sur le **prévision de modèle d’exploration de données** onglet du Concepteur d’exploration de données, dans le **Mining Model** , cliquez sur **sélectionner un modèle**.  
  
2.  Dans le **sélectionner un modèle d’exploration de données** boîte de dialogue zone, parcourez l’arborescence pour le **publipostage ciblé** structure, développez la structure, sélectionnez `TM_Decision_Tree`, puis cliquez sur **OK**.  
  
3.  Dans le **sélectionner une ou plusieurs tables d’entrée** , cliquez sur **sélectionner la Table de cas**.  
  
4.  Dans le **sélectionner une Table** boîte de dialogue le **Source de données** , sélectionnez la vue de source de données [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].  
  
5.  Dans **nom de la Table/vue**, sélectionnez le **ProspectiveBuyer (dbo)** table, puis cliquez sur **OK**.  
  
     Le `ProspectiveBuyer` table est très similaire à la **vTargetMail** table de cas.  
  
## <a name="mapping-the-columns"></a>Mappage des colonnes  
 Une fois la table d'entrée sélectionnée, le Générateur de requêtes de prédiction crée un mappage par défaut entre le modèle d'exploration de données et la table d'entrée en fonction des noms des colonnes. Au moins une colonne de la structure doit correspondre à une colonne dans les données externes.  
  
> [!IMPORTANT]  
>  Les données que vous utilisez pour déterminer la précision des modèles doivent contenir une colonne qui peut être mappée à la colonne prédictible. Si une telle colonne n'existe pas, vous pouvez en créer une avec des valeurs vides, mais elle doit avoir le même type de données que la colonne prédictible.  
  
#### <a name="to-map-the-inputs-to-the-model"></a>Pour mapper les entrées au modèle  
  
1.  Avec le bouton droit des lignes qui connectent les **modèle d’exploration de données** fenêtre pour le **sélectionner plusieurs tables d’entrée** , puis sélectionnez **modifier les connexions**.  
  
     Vous remarquez que toutes les colonnes ne sont pas mappées. Nous allons ajouter des mappages pour plusieurs **colonnes de Table**. Nous allons également générer une nouvelle colonne de date de naissance sur la colonne de date actuelle, afin que les colonnes correspondent mieux.  
  
2.  Sous **colonne de Table**, cliquez sur le `Bike Buyer` de la cellule et sélectionnez ProspectiveBuyer.Unknown dans la liste déroulante.  
  
     Cette action mappe la colonne prédictible, [Bike Buyer], à une colonne de la table d'entrée.  
  
3.  Cliquez sur **OK**.  
  
4.  Dans **l’Explorateur de solutions**, avec le bouton droit le **publipostage ciblé** vue de source de données et sélectionnez **Concepteur de vues**.  
  
5.  Cliquez sur la table ProspectiveBuyer, puis sélectionnez **nouveau calcul nommé**.  
  
6.  Dans le **créer un calcul nommé** boîte de dialogue pour **nom de colonne**, type `calcAge`.  
  
7.  Pour **Description**, type **calcule l’âge en fonction de la date de naissance**.  
  
8.  Dans le **Expression** , tapez `DATEDIFF(YYYY,[BirthDate],getdate())` puis cliquez sur **OK**.  
  
     Étant donné que la table d’entrée n’a aucun **âge** colonne correspondant à celle du modèle, vous pouvez utiliser cette expression pour calculer l’âge du client à partir de la colonne de date de naissance dans la table d’entrée. Dans la mesure où **âge** a été identifiée comme les plus influents colonne pour prédire l’achat de vélo, il doit exister dans les deux le modèle et dans la table d’entrée.  
  
9. Dans le Concepteur d’exploration de données, sélectionnez le **prévision de modèle d’exploration de données** onglet et ouvrez à nouveau le **modifier les connexions** fenêtre.  
  
10. Sous **colonne de Table**, cliquez sur le **âge** de la cellule et sélectionnez ProspectiveBuyer.calcAge à partir de la liste déroulante.  
  
    > [!WARNING]  
    >  Si vous ne voyez pas la colonne dans la liste, vous devrez peut-être actualiser la définition de la vue de source de données chargée dans le concepteur. Pour ce faire, à partir de la **fichier** menu, sélectionnez **Enregistrer tout**, puis fermez et rouvrez le projet dans le concepteur.  
  
11. Cliquez sur **OK**.  
  
## <a name="designing-the-prediction-query"></a>Conception de la requête de prédiction  
  
1.  Le premier bouton de la barre d’outils de la **prévision de modèle d’exploration de données** onglet est la **commutateur pour concevoir afficher / basculer vers l’affichage des résultats / basculer vers l’affichage de la requête** bouton. Cliquez sur la flèche bas sur ce bouton, puis sélectionnez **conception**.  
  
2.  Dans la grille sur la **prévision de modèle d’exploration de données** , cliquez sur la cellule dans la première ligne vide dans le **Source** colonne, puis sélectionnez **fonction de prédiction**.  
  
3.  Dans le **fonction de prédiction** de ligne, dans le **champ** colonne, sélectionnez `PredictProbability`.  
  
     Dans le **Alias** colonne de la même ligne, type **probabilité des résultats**.  
  
4.  À partir de la **Mining Model** fenêtre ci-dessus, sélectionnez et faites glisser [Bike Buyer] dans le **critères/Argument** cellule.  
  
     Lorsque vous relâchez, [TM_Decision_Tree]. [Bike Buyer] s’affiche dans le **critères/Argument** cellule.  
  
     Ceci permet de spécifier la colonne cible pour la fonction `PredictProbability`. Pour plus d’informations sur les fonctions, consultez [Data Mining Extensions &#40;DMX&#41; référence des fonctions](/sql/dmx/data-mining-extensions-dmx-function-reference).  
  
5.  Cliquez sur la ligne vide suivante dans le **Source** colonne, puis sélectionnez un modèle d’exploration de données TM_Decision_Tree **.**  
  
6.  Dans le `TM_Decision_Tree` de ligne, dans le **champ** colonne, sélectionnez `Bike Buyer`.  
  
7.  Dans le `TM_Decision_Tree` de ligne, dans le **critères/Argument** colonne, tapez `=1`.  
  
8.  Cliquez sur la ligne vide suivante dans le **Source** colonne, puis sélectionnez **table ProspectiveBuyer**.  
  
9. Dans le `ProspectiveBuyer` de ligne, dans le **champ** colonne, sélectionnez **ProspectiveBuyerKey**.  
  
     Un identificateur unique est ainsi ajouté à la requête de prédiction, lequel vous permet d'identifier les personnes susceptibles ou non d'acheter un vélo.  
  
10. Ajoutez cinq lignes en plus à la grille. Pour chaque ligne, sélectionnez **table ProspectiveBuyer** en tant que le **Source** , puis ajoutez les colonnes suivantes dans le **champ** cellules :  
  
    -   calcAge  
  
    -   LastName  
  
    -   FirstName  
  
    -   AddressLine1  
  
    -   AddressLine2  
  
 Enfin, exécutez la requête et consultez les résultats.  
  
 Le **Générateur de requêtes de prédiction** inclut également ces commandes :  
  
-   **Afficher** case à cocher  
  
     Vous permet de supprimer des clauses de la requête sans devoir les supprimer du concepteur. Ceci s'avère utile lorsque vous travaillez avec des requêtes complexes et souhaitez conserver la syntaxe sans devoir copier et coller le DMX dans la fenêtre.  
  
-   **Grouper**  
  
     Insère une parenthèse ouvrante (gauche) au début de la ligne sélectionnée, ou insère une parenthèse fermante (droite) à la fin de la ligne active.  
  
-   **ET/OU**  
  
     Insère l'opérateur `AND` ou l'opérateur `OR` immédiatement après la fonction ou la colonne active.  
  
#### <a name="to-run-the-query-and-view-results"></a>Pour exécuter la requête et afficher les résultats  
  
1.  Dans le **prévision de modèle d’exploration de données** onglet, sélectionnez le **résultat** bouton.  
  
2.  Après l'exécution de la requête et l'affichage des résultats, vous pouvez examiner les résultats.  
  
     Le **prévision de modèle d’exploration de données** onglet affiche des informations de contact pour les clients potentiels susceptibles d’acheter des vélos. Le **probabilité des résultats** colonne indique la probabilité de la prédiction correcte. Ces résultats peuvent vous aider à déterminer les clients potentiels à cibler pour le publipostage.  
  
3.  À ce stade, vous pouvez enregistrer les résultats. Vous avez le choix entre trois options.  
  
    -   Cliquez sur une ligne de données dans les résultats, puis sélectionnez **copie** pour enregistrer uniquement cette valeur (et l’en-tête de colonne) dans le Presse-papiers.  
  
    -   Avec le bouton droit n’importe quelle ligne dans les résultats, puis sélectionnez **copier tout** pour copier le jeu de résultats entier, y compris les en-têtes de colonne, dans le Presse-papiers.  
  
    -   Cliquez sur **enregistrer le résultat de la requête** pour enregistrer les résultats directement à une base de données comme suit :  
  
        1.  Dans le **enregistrer le résultat de requête Data Mining** boîte de dialogue, sélectionnez une source de données, ou définir une nouvelle source de données.  
  
        2.  Tapez le nom de la table dans laquelle seront enregistrés les résultats de la requête.  
  
        3.  Utilisez l’option **ajouter à la vue DSV**, pour créer la table et l’ajouter à une vue de source de données existante. Cela est utile si vous voulez conserver toutes les tables associées pour un modèle, telles que les données de formation, les données source de prédiction et les résultats de la requête, dans la même vue de source de données.  
  
        4.  Utilisez l’option **remplacer si existe**, mettre à jour une table existante avec les derniers résultats.  
  
             Vous devez utiliser l'option permettant de remplacer la table si vous avez ajouté des colonnes à la requête de prédiction, modifié les noms des types de données des colonnes dans la requête de prédiction ou si vous avez exécuté des instructions ALTER sur la table de destination.  
  
             En outre, si plusieurs colonnes portent le même nom (par exemple, le nom de colonne par défaut **Expression**) vous devez créer un alias pour les colonnes avec des noms dupliqués, ou une erreur est générée lorsque le concepteur tente d’enregistrer les résultats dans SQL Serveur. En effet, SQL Server n'autorise pas plusieurs colonnes à porter le même nom.  
  
             Pour plus d’informations, consultez [enregistrer les boîte de dialogue données d’exploration de données requête résultat &#40;vue prévision de modèle d’exploration de données&#41;](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md).  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Utilisation de l’extraction sur les données de Structure &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une requête de prédiction à l’aide du Générateur de requêtes de prédiction](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
