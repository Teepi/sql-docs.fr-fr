---
title: Éditeur de gestionnaire de connexions de fichiers | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileconnectionmanager.f1
helpviewer_keywords:
- File Connection Manager Editor
ms.assetid: 051c48e5-3d86-49af-b554-ff62e3de3622
caps.latest.revision: 22
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0691e6d8b6bebec04d2126bba0caa8b14ed3cdd1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311939"
---
# <a name="file-connection-manager-editor"></a>Éditeur du gestionnaire de connexions de fichiers
  Utilisez la boîte de dialogue **Éditeur du gestionnaire de connexions de fichiers** pour spécifier les propriétés à utiliser pour se connecter à un fichier ou à un dossier.  
  
> [!NOTE]  
>  Vous pouvez définir la propriété ConnectionString du gestionnaire de connexions de fichiers en spécifiant une expression dans la fenêtre Propriétés de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Toutefois, pour éviter une erreur de validation quand vous utilisez une expression pour spécifier le fichier ou dossier, dans **l’Éditeur du gestionnaire de connexions de fichiers**, pour **Fichier/Dossier**, ajoutez un chemin du fichier ou du dossier.  
  
 Pour en savoir plus sur le gestionnaire de connexions de fichiers, consultez [File Connection Manager](connection-manager/file-connection-manager.md).  
  
## <a name="options"></a>Options  
 **Type d'utilisation**  
 Indiquez si le **Gestionnaire de connexions de fichiers** se connecte à un fichier ou dossier existant ou s’il crée un nouveau fichier ou dossier.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Créer un fichier|Crée un nouveau fichier au moment de l'exécution.|  
|Fichier existant|Utilise un fichier existant.|  
|Créer un dossier|Crée un nouveau dossier au moment de l'exécution.|  
|Dossier existant|Utilise un dossier existant.|  
  
 **Fichier / Dossier**  
 Si **Fichier**, spécifiez le fichier à utiliser.  
  
 Si **Dossier**, spécifiez le dossier à utiliser.  
  
 **Parcourir**  
 Sélectionnez le fichier ou le dossier à l’aide de la boîte de dialogue **Sélectionner un fichier** ou **Rechercher un dossier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
