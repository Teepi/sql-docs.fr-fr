---
title: Description, propriété (ADO MD) | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member::Description
- Level::Description
- CubeDef::Description
- Hierarchy::Description
- Description
- Dimension::Description
helpviewer_keywords:
- Description property [ADO MD]
ms.assetid: 6d626d35-0bf3-4f24-9934-ad9c9c91273a
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b073b4719de6554159947502a525d242f37e6707
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284068"
---
# <a name="description-property-ado-md"></a>Description, propriété (ADO MD)
Retourne une description de texte de l’objet actuel.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un **chaîne** et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Pour [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) objets, **Description** s’applique uniquement aux membres de formule et de mesure. **Description** retourne une chaîne vide (« ») pour tous les autres types de membres. Pour plus d’informations sur les différents types de membres, consultez la [Type](../../../ado/reference/ado-md-api/type-property-ado-md.md) propriété.  
  
 Cette propriété est uniquement prise en charge sur **membre** les objets qui appartiennent à un [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) objet. Une erreur se produit lorsque cette propriété est référencée à partir de **membre** objets appartenant à un [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) objet.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[CubeDef, objet (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|[Dimension, objet (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|[Hierarchy, objet (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|  
|[Level, objet (ADO MD)](../../../ado/reference/ado-md-api/level-object-ado-md.md)|[Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)||
