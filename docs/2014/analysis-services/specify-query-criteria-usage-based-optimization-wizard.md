---
title: Spécifier des critères de requête (Assistant Optimisation de l’utilisation) | Microsoft Docs
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
- sql12.asvs.usagebasedoptimizationwizard.specifyquerycriteria.f1
ms.assetid: 3193adc2-af9f-4234-a4cc-dea0c280a724
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 46a0877a1f51964287f9a01f00adeae23d2dcfd1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176426"
---
# <a name="specify-query-criteria-usage-based-optimization-wizard"></a>Spécifier les critères de requêtes (Assistant Optimisation de l'utilisation)
  Utilisez la page **Spécifier les critères de requêtes** pour choisir unes ou plusieurs options de filtre afin d'identifier des requêtes à optimiser.  
  
> [!NOTE]  
>  Cette page est désactivée si [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] n'est pas connecté au journal des requêtes.  
  
## <a name="options"></a>Options  
 **Statistiques des journaux de requête**  
 Affiche des informations sur les requêtes stockées dans le journal pour les partitions sélectionnées. Les éléments suivants s'affichent :  
  
|Terme|Définition|  
|----------|----------------|  
|**Nombre total de requêtes**|Affiche le nombre total de requêtes stockées dans le journal pour les partitions sélectionnées.|  
|**Requêtes distinctes**|Affiche le nombre de requêtes distinctes stockées dans le journal pour les partitions sélectionnées.|  
|**Utilisateurs distincts**|Affiche le nombre total d'utilisateurs distincts associés aux requêtes stockées dans le journal pour les partitions sélectionnées.|  
|**Temps de réponse moyen**|Affiche le temps de réponse moyen pour les requêtes stockées dans le journal pour les partitions sélectionnées.|  
  
 **Date de début**  
 Filtre les requêtes du journal en fonction de la date et de l'heure de début. Choisissez ou tapez une date dans la liste déroulante.  
  
> [!NOTE]  
>  Si vous ne sélectionnez pas **Date de fin** , toutes les requêtes du journal portant une date et une heure égales ou ultérieures à celles spécifiées sont prises en compte.  
  
 **Date de fin**  
 Filtre les requêtes du journal en fonction de la date et de l'heure de fin. Choisissez ou tapez une date dans la liste déroulante.  
  
> [!NOTE]  
>  Si vous ne sélectionnez pas **Date de début** , toutes les requêtes du journal portant une date et une heure égales ou antérieures à celles spécifiées sont prises en compte.  
  
 **Utilisateurs**  
 Filtre les requêtes du journal en fonction d'un jeu d'utilisateurs. Cliquez sur le bouton (**...**) pour afficher la boîte de dialogue **Sélection de l’utilisateur** et choisir des utilisateurs sur la base desquels les requêtes doivent être filtrées. Pour plus d’informations sur la boîte de dialogue **Sélection de l’utilisateur**, consultez [Boîte de dialogue Sélection de l’utilisateur &#40;Analysis Services – Données multidimensionnelles&#41;](user-selection-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Requêtes les plus fréquentes**  
 Filtre les requêtes du journal en fonction du pourcentage supérieur de requêtes distinctes exécutées le plus fréquemment pour les partitions sélectionnées. Choisissez ou tapez un pourcentage dans la zone de texte.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 de l’Assistant Optimisation de l’utilisation](usage-based-optimization-wizard-f1-help.md)   
 [Assistants Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
