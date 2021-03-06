---
title: Créer une Dimension de temps en générant une Table temporelle | Microsoft Docs
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
- time dimensions [Analysis Services]
- dimensions [Analysis Services], time
- time periods [Analysis Services]
- range-based time dimensions [Analysis Services]
- server time dimensions [Analysis Services]
- calendars [Analysis Services]
- table-based time dimensions [Analysis Services]
ms.assetid: 58303326-1361-4c0e-9f3d-642ce69c4f6a
caps.latest.revision: 41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9cb6230863b9e898f50ab30c6fc4288998024e5c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180936"
---
# <a name="create-a-time-dimension-by-generating-a-time-table"></a>Create a Time Dimension by Generating a Time Table
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez utiliser l'Assistant Dimension dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour créer une dimension de temps lorsque aucune table de temps n'est disponible dans la base de données source. Pour ce faire, sélectionnez l'une des options suivantes dans la page **Sélectionner la méthode de création** :  
  
-   **Générer une table de temps dans la source de données** Sélectionnez cette option lorsque vous disposez de l'autorisation de créer des objets dans la source de données sous-jacente. L'Assistant génère ensuite une table de temps et stocke cette table dans la source de données. L'Assistant crée ensuite la dimension de temps à partir de cette table de temps.  
  
-   **Générer une table de temps sur le serveur** Sélectionnez cette option lorsque vous ne disposez pas de l'autorisation de créer des objets dans la source de données sous-jacente. L'Assistant génère et stocke ensuite une table sur le serveur au lieu de le faire dans la source de données. (La dimension créée à partir d'une table de temps sur le serveur est appelée *dimension de temps du serveur*.) L'Assistant crée ensuite la dimension de temps du serveur à partir de cette table.  
  
 Lorsque vous créez une dimension de temps du serveur, vous spécifiez les périodes, ainsi que les dates de début et de fin de la dimension. L'Assistant utilise les périodes spécifiées pour créer les attributs de temps. Lorsque vous traitez la dimension, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] génère et stocke les données requises pour prendre en charge les dates et les périodes spécifiées. L'Assistant utilise les attributs créés pour une dimension de temps afin de recommander les hiérarchies de la dimension. Les hiérarchies font apparaître les relations entre les différentes périodes et tiennent compte des différents calendriers. Par exemple, dans une hiérarchie de calendrier standard, un niveau Semaines apparaît sous un niveau Années, mais pas sous un niveau Mois, car les années se divisent en nombre égal de semaines, mais pas les mois. En revanche, dans une hiérarchie de calendrier de fabrication ou de rapports, les mois se divisent en nombre égal de semaines, de sorte qu'un niveau Semaines apparaît sous un niveau Mois.  
  
## <a name="define-time-periods"></a>Définition de périodes  
 Utilisez la page **Définir des périodes** de l'Assistant pour spécifier les plages de dates que vous voulez inclure dans la dimension. Par exemple, vous pouvez sélectionner une plage qui débute le 1er janvier de l'année la plus ancienne dans vos données et se termine un ou deux ans après l'année en cours (pour autoriser les futures transactions). Les transactions qui sont en dehors de la plage de ne pas apparaître ou apparaissent comme étant inconnus membres dans la dimension, selon le `UnknownMemberVisible` paramètre de propriété pour la dimension. Vous pouvez également modifier le premier jour de la semaine utilisé par vos données (le jour par défaut est le dimanche).  
  
 Sélectionnez les périodes de temps  à utiliser lorsque l'Assistant crée les hiérarchies qui s'appliquent à vos données, telles que Années, Semestres, Trimestres, Quadrimestres, Mois, Décades, Semaines ou Date. Vous devez toujours sélectionner au moins la période Date. L'attribut Date étant l'attribut clé de la dimension, cette dernière ne peut pas fonctionner sans lui.  
  
 À côté de **Langue pour les noms des membres de temps**, sélectionnez la langue à utiliser pour étiqueter les membres de la dimension.  
  
 Une fois que vous avez créé une dimension de temps qui repose sur une plage de dates, vous pouvez utiliser le Concepteur de dimensions pour ajouter ou supprimer les attributs de temps. L'attribut Date étant l'attribut clé de la dimension, vous ne pouvez pas le supprimer de la dimension. Pour masquer l’attribut Date aux utilisateurs, vous pouvez modifier le `AttributeHierarchyVisible` propriété sur l’attribut `False`.  
  
## <a name="select-calendars"></a>Sélection de calendriers  
 Le calendrier standard de 12 mois (grégorien), qui débute le 1er janvier et se termine le 31 décembre, est toujours inclus lorsque vous créez une dimension de temps. Dans la page **Sélectionner des calendriers** de l'Assistant, vous pouvez spécifier des calendriers supplémentaires sur lesquels reposeront les hiérarchies de la dimension. Pour obtenir une description des types de calendrier, consultez [Créer une dimension de type Date](database-dimensions-create-a-date-type-dimension.md).  
  
 Selon les périodes que vous sélectionnez dans la page **Définir des périodes** de l'Assistant, les sélections de calendrier déterminent les attributs qui sont créés dans la dimension. Par exemple, si vous sélectionnez les périodes **Année** et **Trimestre** dans la page **Définir des périodes** de l’Assistant et **Calendrier fiscal** dans la page **Sélectionner des calendriers** , les attributs FiscalYear, FiscalQuarter et FiscalQuarterOfYear sont créés pour le calendrier fiscal.  
  
 L’Assistant crée également des hiérarchies spécifiques aux calendriers qui se composent des attributs créés pour le calendrier. Pour chaque calendrier, chaque niveau de chaque hiérarchie est reporté dans le niveau immédiatement supérieur. Par exemple, dans le calendrier standard de 12 mois, l'Assistant crée une hiérarchie d'Années et de Semaines ou d'Années et de Mois. Toutefois, les mois d'un calendrier standard ne contenant pas un nombre égal de semaines, il n'y a pas de hiérarchie d'Années, de Mois et de Semaines. À l'inverse, les mois d'un calendrier de fabrication ou de rapports contenant un nombre égal de semaines, les semaines dans ce calendrier sont regroupées dans les mois.  
  
## <a name="completing-the-dimension-wizard"></a>Fin de l'Assistant Dimension  
 Dans la page **Fin de l'Assistant** , vérifiez les attributs et les hiérarchies créés par l'Assistant, puis attribuez un nom à la dimension de temps. Cliquez sur **Terminer** pour terminer l'Assistant et créer la dimension. Une fois la dimension terminée, vous pouvez la modifier à l'aide du Concepteur de dimensions.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](data-source-views-in-multidimensional-models.md)   
 [Créer une Dimension de type Date](database-dimensions-create-a-date-type-dimension.md)   
 [Propriétés de Dimension de base de données](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties.md)   
 [Relations de dimension](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Créer une Dimension à l’aide d’une Table existante](create-a-dimension-by-using-an-existing-table.md)   
 [Créer une dimension en générant une table non temporelle dans la source de données](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)  
  
  
