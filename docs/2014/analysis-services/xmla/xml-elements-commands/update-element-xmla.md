---
title: Mettre à jour, élément (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Update Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Update
- microsoft.xml.analysis.update
- http://schemas.microsoft.com/analysisservices/2003/engine#Update
helpviewer_keywords:
- Update command [XMLA]
ms.assetid: 324dcc16-865d-4d0a-b393-2b06c18ac807
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 75dda4a163ce6551246e11aa9eba6b57fcd9fb25
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283955"
---
# <a name="update-element-xmla"></a>Élément Update (XMLA)
  Met à jour les membres d'attribut d'une dimension.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Update>  
      <Object>...</Object>  
      <MoveWithDescendants>...</MoveWithDescendants>  
      <Attributes>...</Attributes>  
      <Where>...</Where>  
   </Update>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Commandee](../xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[Attributs](../xml-elements-properties/attributes-element-xmla.md), [MoveWithDescendants](../xml-elements-properties/movewithdescendants-element-xmla.md), [objet](../xml-elements-properties/object-element-dimension-xmla.md), [où](../xml-elements-properties/where-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 La commande `Update` déplace des membres d'attribut au sein d'une dimension activée en écriture.  
  
 Pour plus d’informations sur la mise à jour des membres, consultez [insertion, mise à jour et suppression de membres &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément DROP &#40;XMLA&#41;](drop-element-xmla.md)   
 [Insérer un élément &#40;XMLA&#41;](insert-element-xmla.md)   
 [Commandes &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
