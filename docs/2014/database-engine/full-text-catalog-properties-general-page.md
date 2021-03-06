---
title: Propriétés du catalogue de texte intégral (Page Général) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.general.f1
ms.assetid: d1f66762-2d40-4f24-b635-a417d22ee79a
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: cc0d0c6e287d978b0a10979843a50f40f906872b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169321"
---
# <a name="full-text-catalog-properties-general-page"></a>Propriétés du catalogue de texte intégral (page Général)
  Cette section présente les options et fonctions disponibles dans la page **Général** de la boîte de dialogue **Propriétés du catalogue de texte intégral** .  
  
> [!NOTE]  
>  Pour les bases de données [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] , un catalogue de texte intégral est un concept logique qui fait référence à un groupe d'index de recherche en texte intégral. Le catalogue de texte intégral est un objet virtuel qui n'appartient à aucun groupe de fichiers.  
  
## <a name="options"></a>Options  
  
### <a name="properties"></a>Propriétés  
 **Catalogue par défaut**  
 Indique si le catalogue est le catalogue par défaut de la base de données.  
  
 **État du remplissage**  
 Indique l'état du catalogue. Les valeurs possibles sont :  
  
-   **Inactivité**  
  
-   **Analyse en cours**  
  
-   **Suspendu**  
  
-   **Limitées**  
  
-   **La récupération**  
  
-   **Arrêter**  
  
-   **Remplissage incrémentiel en cours**  
  
-   **Création de l’index**  
  
-   **Le disque est plein — suspendu**  
  
-   **Change tracking**  
  
 **Nombre d’éléments**  
 Affiche le nombre d'éléments de texte intégral contenus dans le catalogue.  
  
 **Taille du catalogue**  
 Affiche la taille en mégaoctets du catalogue de texte intégral.  
  
 **Nom**  
 Nom du catalogue de texte intégral.  
  
 **Respecter les accents**  
 Permet d'afficher ou de modifier si le catalogue respecte ou non les signes diacritiques, par exemple le tilde (**~**), l'accent aigu (**´**) ou le tréma (**¨**). Les valeurs valides sont :  
  
-   **Non**  
  
-   **Oui**  
  
-   Pour plus d'informations sur les signes diacritiques, consultez [diacritique, signe](http://go.microsoft.com/fwlink/?LinkId=154091) (en anglais) dans l'encyclopédie Encarta MSN.  
  
 **Date du dernier remplissage**  
 Affiche la date du dernier remplissage du catalogue.  
  
 **Propriétaire**  
 Propriétaire du catalogue de texte intégral.  
  
 **Nombre de clés uniques**  
 Nombre de mots uniques qui constituent l'index de texte intégral du catalogue.  
  
### <a name="catalog-action"></a>Action du catalogue  
  
|||  
|-|-|  
|**Aucun**|N'exécute aucune opération de type **Optimiser le catalogue**, **Reconstruire le catalogue**ou **Remplir à nouveau le catalogue** .|  
|**Optimiser le catalogue**|Optimise l'utilisation de l'espace du catalogue et améliore les performances des requêtes. Cette option améliore également la précision du classement de la pertinence des résultats de la recherche.<br /><br /> Cette action exécute ALTER FULLTEXT CATALOG *catalog_name* REORGANIZE.|  
|**La reconstruction du catalogue**|Supprime et reconstruit le catalogue de texte intégral. Cette opération doit être exécutée si une propriété fondamentale du catalogue a été modifiée (par exemple, le respect des accents).<br /><br /> Pour que la reconstruction réussisse, le groupe de fichiers dans lequel réside le catalogue de texte intégral doit être en ligne ou accessible en lecture et en écriture. Après la reconstruction, l'index de texte intégral sera rempli à nouveau.<br /><br /> Cette action exécute ALTER FULLTEXT CATALOG *catalog_name* REBUILD.|  
|**Remplir à nouveau le catalogue**|Met à jour le catalogue avec les modifications récemment apportées aux données. Cette option ne requiert aucun temps mort du catalogue.|  
  
## <a name="see-also"></a>Voir aussi  
 [Alimenter des index de recherche en texte intégral](../relational-databases/indexes/indexes.md)  
  
  
