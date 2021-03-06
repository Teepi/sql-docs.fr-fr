---
title: 'Étape 1 : Copie du package de la leçon 1 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7f1616c2-2b4e-4010-be50-27d7b897403a
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 97da2e6f299541173246dae96af1055c7df44810
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166740"
---
# <a name="step-1-copying-the-lesson-1-package"></a>Étape 1 : Copie du package de la leçon 1
  Dans cette tâche, vous allez créer une copie du package Lesson 1.dtsx que vous avez créé à la leçon 1. Si vous n’avez pas terminé la leçon 1, vous pouvez ajouter au projet le package final de la leçon 1 inclus avec le didacticiel, puis le copier à la place. Vous allez utiliser cette nouvelle copie tout au long de la leçon 2.  
  
### <a name="to-create-the-lesson-2-package"></a>Pour créer le package de la leçon 2  
  
1.  Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools n’est pas encore ouvert, dans le menu **Démarrer**, pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server 2012**et cliquez sur **SQL Server Data Tools**.  
  
2.  Dans le menu **Fichier** , cliquez sur **Ouvrir**, sur **Projet/Solution**, sur le dossier **Didacticiel SSIS** , sur **Ouvrir**, puis double-cliquez sur **SSIS Tutorial.sln**.  
  
3.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Lesson 1.dtsx**et choisissez **Copier**.  
  
4.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Packages SSIS**et choisissez **Coller**.  
  
     Par défaut, le package copié est nommé Lesson 2.dtsx.  
  
5.  Dans l’Explorateur de solutions, double-cliquez sur **Lesson 2.dtsx** pour ouvrir le package.  
  
6.  Cliquez n’importe où dans l’arrière-plan de l’aire de conception **Flux de contrôle** , puis cliquez sur **Propriétés**.  
  
7.  Dans la fenêtre Propriétés, mettez à jour le `Name` propriété `Lesson 2`.  
  
8.  Cliquez sur la zone pour le **ID** propriété, cliquez sur la flèche déroulante, puis  **\<générer un nouvel ID >**.  
  
### <a name="to-add-the-completed-lesson-1-package"></a>Pour ajouter le package final de la leçon 1  
  
1.  Ouvrez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools et ouvrez le projet Didacticiel SSIS.  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Packages SSIS**, puis cliquez sur **Ajouter le package existant**.  
  
3.  Dans la boîte de dialogue **Ajouter une copie des packages existants** , sous **Emplacement du package**, sélectionnez **Système de fichiers**.  
  
4.  Cliquez sur le bouton Parcourir **(...)** , accédez à **Lesson 1.dtsx** sur votre ordinateur, puis cliquez sur **Ouvrir**.  
  
     Pour télécharger tous les packages de leçons de ce didacticiel, procédez comme suit.  
  
    1.  Accédez à [Exemples de produits Integration Services](http://go.microsoft.com/fwlink/?LinkId=275027)  
  
    2.  Cliquez sur l'onglet **DOWNLOADS** (Téléchargements).  
  
    3.  Cliquez sur le fichier SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Copiez et collez le package de la leçon 1 comme décrit aux étapes 3 à 8 de la procédure précédente.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 2 : Ajout et configuration du conteneur de boucles Foreach](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
  
