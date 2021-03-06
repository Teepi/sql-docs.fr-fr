---
title: Considérations relatives à l’installation de SQL Server à l’aide de SysPrep | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e1792eeb-2874-4653-b20e-3063f4eb4e5d
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 140fac99176fc41f5e3967c158c7929fe9554989
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180416"
---
# <a name="considerations-for-installing-sql-server-using-sysprep"></a>Considérations relatives à l'installation de SQL Server à l'aide de SysPrep
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep vous permet de préparer une instance autonome de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur et de terminer la configuration ultérieurement. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep implique un processus en deux étapes pour arriver à une instance autonome configurée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces étapes sont les suivantes :  
  
-   [Préparer l'image](#BKMK_PrepareImage)  
  
     Cette étape arrête la procédure d'installation après l'installation des fichiers binaires du produit, sans configurer les informations spécifiques à l'ordinateur, au réseau ou au compte pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] préparée.  
  
-   [Finaliser l'image](#BKMK_CompleteImage)  
  
     Cette étape vous permet de finaliser la configuration d'une instance préparée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pendant cette étape, vous pouvez fournir les informations spécifiques à l'ordinateur, au réseau et au compte.  
  
 Pour plus d’informations sur l’installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de SysPrep, consultez [installer SQL Server 2014 à l’aide de SysPrep](install-sql-server-using-sysprep.md).  
  
## <a name="common-uses-for-includessnoversionincludesssnoversion-mdmd-sysprep"></a>Utilisations courantes pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep  
 Vous pouvez utiliser la fonctionnalité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep de chacune des manières suivantes :  
  
-   À l'aide de l'étape Préparer l'image, vous pouvez préparer une ou plusieurs instances non configurées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le même ordinateur. Vous pouvez configurer ces instances préparées à l'aide de l'étape de finalisation d'image sur le même ordinateur.  
  
-   Vous pouvez capturer le fichier de configuration de l'installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l'instance préparée et l'utiliser pour préparer des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supplémentaires non configurées sur plusieurs ordinateurs pour une configuration ultérieure.  
  
-   En association avec l'outil de préparation système Windows (connu sous le nom de Windows SysPrep), vous pouvez créer une image du système d'exploitation comprenant les instances préparées non configurées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur l'ordinateur source. Vous pouvez déployer ensuite l'image de système d'exploitation sur plusieurs ordinateurs. Une fois que vous avez terminé la configuration du système d'exploitation, vous pouvez configurer les instances préparées à l'aide de l'étape Finaliser l'image du programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     L'outil Windows SysPrep sert à préparer des images de système d'exploitation Windows. Il sert à capturer une image personnalisée du système d'exploitation pour le déploiement au sein d'une organisation. Pour plus d'informations sur SysPrep et ses utilisations, consultez l'article intitulé [Qu'est-ce que SysPrep ?](http://go.microsoft.com/fwlink/?LinkId=143546).  
  
## <a name="installation-media-considerations"></a>Considérations relatives au support d'installation  
 Si vous utilisez une version complète de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tenez compte des éléments suivants :  
  
-   Éditions non Express de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    -   L'étape Préparer l'image utilise l'édition d'évaluation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour installer les binaires de produit. Lorsque l'instance est finalisée, l'édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dépend de l'ID de produit fourni pendant l'étape de finalisation d'image.  
  
    -   Si vous fournissez un ID de produit d'édition d'évaluation, la période d'évaluation est configurée de façon à expirer 180 jours après la finalisation de l'instance préparée.  
  
-   Éditions Express de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    -   Pour préparer une instance d'une édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express, utilisez le support d'installation Express.  
  
    -   Vous ne pouvez pas spécifier d'ID de produit pour une instance préparée d'une édition [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.  
  
## <a name="supported-includessnoversionincludesssnoversion-mdmd-installations"></a>Installations de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prises en charge  
 SysPrep dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] prend en charge toutes les fonctionnalités, outils y compris, de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vous pouvez préparer plusieurs instances pour des installations côte à côte de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ou versions antérieures. Les fonctionnalités de ces instances doivent prendre en charge SysPrep.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est installé et finalisé automatiquement à la fin de l'étape de préparation d'image.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Writer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont préparés automatiquement lorsque vous préparez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ils sont finalisés lorsque vous finalisez l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de l'étape Finaliser l'image.  
  
 Pour plus d’informations sur les éditions prises en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Vous pouvez effectuer une mise à niveau d'édition lors de la configuration d'une instance préparée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette option n'est pas prise en charge pour les éditions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.  
  
 Depuis [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep prend en charge les installations de cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir de la ligne de commande.  
  
## <a name="includessnoversionincludesssnoversion-mdmd-sysprep-limitations"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SysPrep  
 La réparation d'une instance préparée n'est pas prise en charge. Si le programme d'installation échoue pendant l'étape Préparer l'image ou Finaliser l'image, vous devez le réexécuter.  
  
##  <a name="BKMK_PrepareImage"></a> Préparer l'image  
 L'étape Préparer l'image installe le produit et les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais ne configure pas l'installation.  
  
 Les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à installer et l'emplacement d'installation pour les fichiers d'installation du produit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent être spécifiés pendant cette étape. Vous pouvez préparer une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] soit par le biais de **Préparation de l’image d’une instance autonome pour le déploiement SysPrep** dans la page **Avancé** du **Centre d’installation** , soit à partir de l’invite de commandes.  
  
-   Vous pouvez préparer plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le même ordinateur et les finaliser ultérieurement.  
  
-   Vous pouvez ajouter ou supprimer des fonctionnalités prises en charge pour les installations SysPrep des instances préparées existantes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Une fois l'instance préparée, un raccourci dans le menu **Démarrer** devient disponible pour finaliser la configuration de l'instance préparée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##  <a name="BKMK_CompleteImage"></a> Finaliser l'image  
 Vous pouvez finaliser les instances préparées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de l'une des méthodes suivantes :  
  
-   Utilisez le raccourci dans le menu Démarrer.  
  
-   Accédez à l’étape **Finalisation d’image d’une instance autonome préparée de SQL Server** dans la page **Avancé** du **Centre d’installation**.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification d'une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)  
  
  
