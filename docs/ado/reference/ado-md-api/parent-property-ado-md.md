---
title: Parent, propriété (ADO MD) | Documents Microsoft
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
- Parent
- Member::Parent
helpviewer_keywords:
- Parent property [ADO MD]
ms.assetid: 32c278c1-d8e1-4bb7-9ecd-2fbfdffee34b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d07d330aaa7497679524caab2a8a9543d64370be
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284640"
---
# <a name="parent-property-ado-md"></a>Parent, propriété (ADO MD)
Indique le membre qui est le parent d’actuel [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) dans une hiérarchie.  
  
## <a name="return-values"></a>Valeurs de retour  
 Retourne un [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md) de l’objet et est en lecture seule.  
  
## <a name="remarks"></a>Notes  
 Un membre qui est au niveau supérieur d’une hiérarchie (racine) a aucun parent. Cette propriété est prise en charge uniquement sur **membre** objets appartenant à un [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md) objet. Une erreur se produit lorsque cette propriété est référencée à partir de **membre** objets appartenant à un [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md) objet.  
  
## <a name="applies-to"></a>S'applique à  
 [Member, objet (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Children, propriété (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)
