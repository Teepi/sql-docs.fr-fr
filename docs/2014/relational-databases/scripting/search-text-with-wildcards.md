---
title: Rechercher du texte avec des caractères génériques | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.wildcards
- vswildcardsbuilder
helpviewer_keywords:
- searches [SQL Server Management Studio], wildcards
- Query Editor [SQL Server Management Studio], wildcard searches
- wildcard options [SQL Server Management Studio]
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32a088a9f868c1063d8d6650b759b855d1192ac2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172370"
---
# <a name="search-text-with-wildcards"></a>Rechercher du texte avec des caractères génériques
  Les expressions ci-après peuvent remplacer des caractères ou des chiffres dans le champ **Rechercher** de la boîte de dialogue [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Find and Replace** dialog box.  
  
#### <a name="to-search-using-wildcards"></a>Pour effectuer une recherche avec des caractères génériques  
  
1.  Pour pouvoir utiliser des caractères génériques dans le champ **Rechercher** pendant des opérations Recherche rapide, **Rechercher dans les fichiers**, **Remplacement rapide**ou **Remplacer dans les fichiers** , sélectionnez l’option **Utiliser** sous **Options de recherche** , puis choisissez **Caractères génériques**.  
  
2.  Le bouton triangulaire **Générateur d'expressions** situé en regard du champ **Rechercher** devient alors disponible. Cliquez sur ce bouton pour afficher la liste des caractères génériques disponibles. Quand vous choisissez un élément dans le **Générateur d’expressions**, il est inséré dans la chaîne **Rechercher** .  
  
 Le tableau ci-dessous décrit les caractères génériques disponibles dans le **Générateur d’expressions**.  
  
|Expression|Syntaxe|Description|  
|----------------|------------|-----------------|  
|Tout caractère unique|?|Représente n'importe quel caractère unique.|  
|Tout chiffre|#|Représente n'importe quel chiffre unique. Par exemple, 7# représente les nombres incluant 7 suivi d'un autre nombre, tels que 71, mais pas 17.|  
|Caractères hors jeu|[! ]|Représente tout caractère ne figurant pas dans le jeu spécifié.|  
|Un ou plusieurs caractères|*|Représente n'importe quel caractère. Par exemple, nou* représente tout texte incluant « nou », tel que nouveaufichier.txt.|  
|Jeu de caractères|[ ]|Représente tout caractère du jeu de caractères spécifié.|  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et remplacement](search-and-replace.md)   
 [Rechercher du texte avec des expressions régulières](search-text-with-regular-expressions.md)  
  
  
