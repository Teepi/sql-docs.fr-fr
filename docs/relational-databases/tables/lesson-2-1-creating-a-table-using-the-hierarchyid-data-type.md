---
title: "Création d’une table à l’aide du type de données hierarchyid | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- HierarchyID
ms.assetid: 0d1f361f-336c-4571-99d1-f4813b2d9fc4
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d3671dcea0c0825ba2624bc84a13ee9e2073a25f
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-2-1---creating-a-table-using-the-hierarchyid-data-type"></a>Leçon 2-1 : Création d’une table à l’aide du type de données hierarchyid
L'exemple suivant crée une table nommée EmployeeOrg qui inclut des données sur les employés ainsi que leur hiérarchie de création de rapports. Cet exemple crée la table dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , mais cela est facultatif. Pour que l'exemple reste simple, cette table ne comporte que cinq colonnes :  
  
-   OrgNode est une colonne **hierarchyid** qui stocke la relation hiérarchique.  
  
-   OrgLevel est une colonne calculée en fonction de la colonne OrgNode qui stocke chaque niveau de nœuds dans la hiérarchie. Elle sera utilisée pour un index à largeur prioritaire.  
  
-   EmployeeID contient le numéro d'identification d'employé qui est habituellement utilisé pour les applications telles que les salaires. Dans le nouveau développement d'applications, les applications peuvent utiliser la colonne OrgNode ; cette colonne EmployeeID séparée n'est donc pas nécessaire.  
  
-   EmpName contient le nom de l'employé.  
  
-   Titre contient le titre de l'employé.  
  
### <a name="to-create-the-employeeorg-table"></a>Pour créer la table EmployeeOrg  
  
1.  Dans une fenêtre de l'Éditeur de requête, exécutez le code suivant pour créer la table `EmployeeOrg` . Lorsque la colonne `OrgNode` est définie comme clé primaire avec un index cluster, un index à profondeur prioritaire est créé :  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    CREATE TABLE HumanResources.EmployeeOrg  
    (  
       OrgNode hierarchyid PRIMARY KEY CLUSTERED,  
       OrgLevel AS OrgNode.GetLevel(),  
       EmployeeID int UNIQUE NOT NULL,  
       EmpName varchar(20) NOT NULL,  
       Title varchar(20) NULL  
    ) ;  
    GO  
    ```  
  
2.  Exécutez le code suivant pour créer un index composite sur les colonnes `OrgLevel` et `OrgNode` afin de prendre en charge des recherches à largeur prioritaire efficaces :  
  
    ```  
    CREATE UNIQUE INDEX EmployeeOrgNc1   
    ON HumanResources.EmployeeOrg(OrgLevel, OrgNode) ;  
    GO  
    ```  
  
La table est maintenant prête à recevoir les données. La tâche suivante remplira la table à l'aide de méthodes hiérarchiques.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
[Remplissage d'une table hiérarchique utilisant des méthodes hiérarchiques](../../relational-databases/tables/lesson-2-2-populating-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
  
