---
title: GetPermissions, méthode (ADOX) | Documents Microsoft
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
- _User25::GetPermissions
- _Group25::raw_GetPermissions
- _Group25::GetPermissions
- _User25::raw_GetPermissions
helpviewer_keywords:
- GetPermissions method [ADOX]
ms.assetid: df201c1f-c76a-465d-98f0-83b7fc36e6e3
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 55a5d4f9096d5a75855d4b612a202afd034b11da
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35286038"
---
# <a name="getpermissions-method-adox"></a>GetPermissions, méthode (ADOX)
Retourne les autorisations pour un [groupe](../../../ado/reference/adox-api/group-object-adox.md) ou [utilisateur](../../../ado/reference/adox-api/user-object-adox.md) sur un objet ou un conteneur d’objets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ReturnValue=GroupOrUser.GetPermissions(Name, ObjectType    [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **Long** valeur qui spécifie un masque de bits contenant les autorisations que le groupe ou l’utilisateur dispose sur l’objet. Cette valeur peut être une ou plusieurs de la [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) constantes.  
  
#### <a name="parameters"></a>Paramètres  
 *Nom*  
 A **Variant** valeur qui spécifie le nom de l’objet pour lequel définir des autorisations. Définissez *nom* à une valeur null si vous souhaitez obtenir les autorisations pour le conteneur d’objets.  
  
 *ObjectType*  
 A **Long** valeur qui peut être une de le [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) constantes, qui spécifie le type de l’objet pour lequel obtenir les autorisations.  
  
 *ObjectTypeId*  
 Facultatif. A **Variant** valeur qui spécifie le GUID d’un type d’objet fournisseur non défini par la spécification OLE DB. Ce paramètre est obligatoire si *ObjectType* a la valeur **adPermObjProviderSpecific**; sinon, il n’est pas utilisé.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Group, objet (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[User, objet (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [GetPermissions et SetPermissions, méthodes-exemple (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Nom, propriété (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)   
 [SetPermissions, méthode (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
