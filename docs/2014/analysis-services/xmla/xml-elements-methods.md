---
title: Méthodes (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#
helpviewer_keywords:
- methods [XML for Analysis]
- XML for Analysis, methods
- XMLA, methods
ms.assetid: c6768dd4-ca06-4a85-93b7-5fd5700886ad
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1baf254e9965153394a3a7b1367ced21c009a7f4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171420"
---
# <a name="methods-xmla"></a>Méthodes (XMLA)
  Le protocole XML for Analysis (XMLA) utilise deux méthodes, `Discover` et `Execute`, pour offrir un moyen standard pour les applications d’accéder aux informations sur une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Ces méthodes étant appelées à l'aide du protocole SOAP (Simple Object Access Protocol), elles acceptent des entrées et affichent les sorties au format XML. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] implémente les deux méthodes conformément à la spécification XML for Analysis 1.1.  
  
## <a name="in-this-section"></a>Dans cette section  
 Les rubriques suivantes décrivent les méthodes XMLA mises en œuvre par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Méthode|Description|  
|------------|-----------------|  
|[Méthode Discover &#40;XMLA&#41;](xml-elements-methods-discover.md)|Récupère des informations (notamment la liste des bases de données disponibles) ou des détails concernant un objet spécifique à partir d'une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Les données récupérées à l'aide de la méthode `Discover` dépendent des valeurs des paramètres qui lui sont transmis.|  
|[Exécuter la méthode &#40;XMLA&#41;](xml-elements-methods-execute.md)|Transmet des commandes XMLA à une instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Ceci inclut des demandes qui impliquent un transfert de données (par exemple, la récupération ou la mise à jour de données sur le serveur).|  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Types de données XML &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Éléments XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)  
  
  
