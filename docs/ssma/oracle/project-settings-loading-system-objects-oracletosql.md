---
title: Paramètres (chargement d’objets système) du projet (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9418cb34-d869-4d24-95b3-6cb9db949bb0
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: af52d18e2978f8645bce689481f68121a164c160
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40392972"
---
# <a name="project-settingsloading-system-objects-oracletosql"></a>Paramètres du projet (Chargement d’objets système) (OracleToSQL)
La page de chargement des objets de système de la **paramètres du projet** boîte de dialogue vous permet de spécifier les objets de système Oracle SSMA convertit et les charge dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Le volet du chargement des objets système n’est disponible dans le **paramètres du projet** et **par défaut des paramètres de projet** boîtes de dialogue :  
  
-   Pour spécifier les paramètres pour tous les projets SSMA, sur le **outils** menu, sélectionnez **par défaut des paramètres de projet**, sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affichées ou modifiées à partir de **Version cible de migration** déroulante cliquez **général** en bas du volet gauche, puis cliquez sur **le chargement des objets système**.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, sélectionnez **paramètres du projet**, cliquez sur **général** en bas du volet gauche, puis cliquez sur **Du chargement des objets système**.  
  
## <a name="default-settings"></a>Paramètres par défaut  
Conversion d’objets système consomme des ressources système et prend du temps. Pour améliorer les performances, SSMA sélectionne uniquement les objets système plus fréquemment utilisées, comme indiqué dans la liste suivante :  
  
-   SYS.DBMS_OUTPUT  
  
-   SYS.DBMS_PIPE  
  
-   SYS.DBMS_UTILITY  
  
-   SYS. STANDARD  
  
-   SYS. UTL_FILE  
  
-   SYS.DBMS_LOB  
  
-   SYS.DBMS_SQL  
  
-   SYS.DBMS_SESSION  
  
Si vos objets Oracle font référence aux objets système supplémentaires, vous devez sélectionner ces objets. Si vous ne sélectionnez pas les objets système qui sont référencés par vos objets de base de données Oracle, SSMA signale les erreurs de conversion. Si vous recevez des erreurs de conversion dus à l’absence d’objets système, sélectionnez les objets manquants dans cette boîte de dialogue. Vous pouvez ensuite répéter la conversion en fonction des besoins.  
  
