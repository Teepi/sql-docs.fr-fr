---
title: Exception, élément (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d3e542534b85d0f87b689b196001e9a00fe49b15
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036767"
---
# <a name="exception-element-xmla"></a>Élément Exception (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Indique qu’une exception a été retournée à partir d’un [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) ou [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) appel de méthode.  
  
 **Namespace** `http://schemas.microsoft.com/analysisservices/2003/exception`  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<root>  
   ...  
   <Exception />  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques d’éléments  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[racine](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 S'il se produit pendant l'exécution d'un appel de méthode **Discover** ou d'une commande XMLA dans un appel de méthode **Execute** une erreur qui empêche la méthode ou la commande de se terminer, l'élément **root** pour cette méthode ou cette commande contient un élément **Exception** et un élément **Messages** . L'élément **Exception** indique qu'une erreur a fait échouer la méthode ou la commande et l'élément **Messages** contient la liste des messages d'erreur ou d'avertissement relatifs à l'erreur.  
  
## <a name="see-also"></a>Voir aussi
 [Messages élément &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
