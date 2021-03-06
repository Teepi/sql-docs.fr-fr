---
title: Créer une hiérarchie explicite (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 29d75b956b6d9be23bd17e3df705724d3876d583
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219489"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a>Créer une hiérarchie explicite (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez une hiérarchie explicite lorsque vous avez besoin d'une hiérarchie déséquilibrée dans laquelle les membres peuvent exister à tous les niveaux. Les hiérarchies explicites contiennent des membres d'une entité unique.  
  
 Après avoir créé une hiérarchie explicite, vous pouvez lui ajouter des membres dans la zone fonctionnelle **Explorateur** .  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   L'entité doit être activée pour les hiérarchies et collections explicites. Pour plus d’informations, consultez [activer une entité pour les hiérarchies et Collections explicites &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).  
  
### <a name="to-create-an-explicit-hierarchy"></a>Pour créer une hiérarchie explicite  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Entités**.  
  
3.  Dans la page **Maintenance de l'entité** , dans la liste **Modèle** , sélectionnez un modèle.  
  
4.  Sélectionnez la ligne de l'entité pour laquelle vous souhaitez créer une hiérarchie explicite.  
  
5.  Cliquez sur **Modifier l'entité sélectionnée**.  
  
6.  Sur le **modifier l’entité** page, dans le **hiérarchies explicites** volet, cliquez sur **ajouter une hiérarchie explicite**.  
  
7.  Sur le **ajouter une hiérarchie explicite** page, dans le **nom de la hiérarchie explicite** zone, tapez un nom pour la hiérarchie.  
  
8.  Décochez éventuellement la case **Hiérarchie obligatoire** pour créer la hiérarchie comme une hiérarchie non obligatoire. Pour plus d’informations sur les types de hiérarchies, consultez [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).  
  
9. Cliquez sur **enregistrer la hiérarchie**.  
  
10. Sur le **modifier l’entité** , cliquez sur **enregistrer l’entité**.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   [Créer un membre consolidé &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [Déplacer des membres dans une hiérarchie &#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchies explicites &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [Hiérarchies dérivées avec des niveaux supérieurs d’une hiérarchie dérivée&#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Modifier le nom d’une hiérarchie explicite &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  
