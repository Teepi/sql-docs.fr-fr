---
title: SetServiceAccount, méthode (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SetServiceAccount Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
caps.latest.revision: 36
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 7186220ae32ceb8faa3fd5bdd906712d844d88e1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317939"
---
# <a name="setserviceaccount-method-sqlservice-class"></a>Méthode SetServiceAccount (classe SqlService)
  Tente de modifier le nom d'utilisateur et le mot de passe sous lesquels l'instance du service s'exécute.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
object  
.SetServiceAccount(  
ServiceStartName , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a>Éléments  
 *object*  
 Objet de [classe SqlService](sqlservice-class.md) qui représente le service.  
  
#### <a name="parameters"></a>Paramètres  
 *ServiceStartName*  
 Valeur de chaîne qui spécifie le nom de compte sous lequel le service s'exécute. En fonction du type de service, le nom de compte peut se présenter sous la forme DomainName\Username. Lorsqu'il s'exécute, le processus du service sera connecté à l'aide de l'une des deux formes suivantes :  
  
-   si le compte appartient au domaine intégré, \Username peut être spécifié ;  
  
-   Si NULL est spécifié, le service s’être connecté en tant que le **LocalSystem** compte.  
  
 Pour les pilotes du noyau ou au niveau du système, *StartName* contient le nom d’objet de pilote, \FileSystem\Rdr ou \Driver\Xns, que le système d’e/s utilise pour charger le pilote de périphérique. Si la valeur NULL est spécifiée, le pilote s'exécute avec un nom d'objet par défaut créé par le système d'E/S en fonction du nom du service, par exemple DWDOM\Admin.  
  
 *ServiceStartPassword*  
 Valeur de chaîne qui spécifie le mot de passe pour le nom du compte dans le *StartName* paramètre. Spécifiez NULL si vous ne modifiez pas le mot de passe. Spécifiez une chaîne vide si le service ne possède pas de mot de passe.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur `uint32` égale à 0 si le service a été correctement modifié ou égale à 1 si la demande n'est pas prise en charge. Tout autre nombre indique une erreur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrage et arrêt des Services](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
