---
title: Recherche de rapports et d’autres éléments (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6a586659-5c2b-453b-8f40-a3a469277b17
caps.latest.revision: 5
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: eafc6aa4bfbd9df7ca6fbc33b2475cc96ebc62f3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198789"
---
# <a name="searching-for-reports-and-other-items-report-builder--and-ssrs"></a>Recherche de rapports et d’autres éléments (Générateur de rapports et SSRS)
  Vous pouvez utiliser le Gestionnaire de rapports pour rechercher sur un serveur de rapports des éléments spécifiques en fonction de leur nom ou de leur description. Vous pouvez rechercher des rapports publiés, des modèles de rapports, des dossiers, des sources de données partagées et des ressources. Il est impossible de rechercher des planifications, des propriétaires, des attributions de rôles, des instantanés d'historique de rapport spécifiques ou des abonnements. La recherche est effectuée dans la base de données du serveur de rapports dans laquelle les éléments sont stockés.  
  
> [!NOTE]  
>  Une recherche effectuée sur un système de fichiers ne permet pas d'afficher un résultat contenant des éléments gérés par un serveur de rapports.  
  
-   Pour rechercher des éléments dans le Gestionnaire de rapports, tapez une chaîne dans la zone de texte **Rechercher** en haut de la page. La recherche débute par le nœud supérieur de l'arborescence des dossiers et se poursuit dans tous les niveaux. Si vous ne disposez pas des autorisations requises pour accéder à un niveau particulier, ce niveau est ignoré. Ceci concerne les dossiers Mes rapports qui appartiennent à d'autres utilisateurs et également ceux des autres dossiers qui ne sont généralement pas disponibles. Seuls les rapports et les éléments que vous êtes autorisé à visualiser sont inclus dans les résultats de la recherche.  
  
-   Pour rechercher un élément en fonction de son nom ou de sa description, spécifiez tout ou partie du texte recherché. La fonction de recherche ne distingue pas les majuscules des minuscules. Vous ne pouvez pas utiliser des opérateurs de recherche comme les symboles plus (+) ou moins (-) pour intégrer ou exclure des critères de recherche.  
  
-   Pour rechercher un texte spécifique dans un rapport, utilisez la barre d'outils située dans la partie supérieure du rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et affichage de rapports dans le Gestionnaire de rapports &#40;Générateur de rapports et SSRS&#41;](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)   
 [Utilisation du dossier Mes rapports &#40;Générateur de rapports et SSRS&#41;](using-my-reports-report-builder-and-ssrs.md)   
 [Recherche, affichage et gestion des rapports &#40;Générateur de rapports et SSRS&#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Ouvrir et fermer un rapport &#40;Gestionnaire de rapports&#41;](../reports/open-and-close-a-report-report-manager.md)  
  
  
