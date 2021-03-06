---
title: Mettre à niveau des packages Integration Services à l’aide de l’Assistant Mise à niveau de packages SSIS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, upgrading
- upgrading Integration Services packages
ms.assetid: 9359275a-48f5-4d1e-8ae7-e797759e3ccf
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cccc4857558d90f25b9b246391a66fdd81d46bdb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37199619"
---
# <a name="upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard"></a>Mettre à niveau des packages Integration Services à l'aide de l'Assistant Mise à niveau de packages SSIS
  Vous pouvez mettre à niveau des packages créés dans des versions antérieures d' [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] vers le format [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilisé par [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit l'Assistant Mise à niveau de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] à cet effet. Étant donné que vous pouvez configurer l'Assistant pour qu'il sauvegarde vos packages d'origine, vous pouvez continuer à les utiliser si vous rencontrez des problèmes de mise à niveau.  
  
 L'Assistant Mise à niveau de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] est installé lors de l'installation de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
> [!NOTE]  
>  L'Assistant Mise à niveau de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] est disponible dans les éditions Standard, Enterprise et Developer de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour plus d’informations sur la mise à niveau des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , consultez [Mettre à niveau des packages Integration Services](upgrade-integration-services-packages.md).  
  
 Le reste de cette rubrique décrit comment exécuter l'Assistant et sauvegarder les packages d'origine.  
  
## <a name="running-the-ssis-package-upgrade-wizard"></a>Exécution de l'Assistant Mise à niveau de packages SSIS  
 Vous pouvez exécuter l'Assistant Mise à niveau de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] à partir de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ou de l'invite de commandes.  
  
#### <a name="to-run-the-wizard-from-sql-server-data-tools"></a>Pour exécuter l'Assistant à partir de l'outils de données SQL Server  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], créez ou ouvrez un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nœud **Packages SSIS** , puis cliquez sur **Mettre à niveau tous les packages** pour mettre à niveau tous les packages sous ce nœud.  
  
    > [!NOTE]  
    >  Lorsque vous ouvrez un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient des packages [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ou [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ouvre automatiquement l'Assistant Mise à niveau de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
#### <a name="to-run-the-wizard-from-sql-server-management-studio"></a>Pour exécuter l'Assistant à partir de SQL Server Management Studio  
  
-   Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], développez le nœud **Packages stockés** , cliquez avec le bouton droit sur le nœud **Système de fichiers** ou **MSDB** , puis cliquez sur **Mettre à niveau les packages**.  
  
#### <a name="to-run-the-wizard-at-the-command-prompt"></a>Pour exécuter l'Assistant à l'invite de commandes  
  
-   À l’invite de commandes, exécutez le fichier SSISUpgrade.exe à partir de la **C:\Program Files\Microsoft SQL Server\120\DTS\Binn** dossier.  
  
## <a name="backing-up-the-original-packages"></a>Sauvegarde des packages d'origine  
 Pour sauvegarder les packages d'origine, les packages d'origine et les package mis à niveau doivent être stockés dans le même dossier du système de fichiers. Selon la façon dont vous exécutez l'Assistant, cet emplacement de stockage peut être sélectionné automatiquement.  
  
-   Lorsque vous exécutez l'Assistant Mise à niveau de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] à partir de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], l'Assistant stocke automatiquement à la fois les packages d'origine et les packages mis à niveau dans le même dossier dans le système de fichiers.  
  
-   Lorsque vous exécutez l'Assistant Mise à niveau de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] à partir de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de l'invite de commandes, vous pouvez spécifier différents emplacements de stockage pour les packages d'origine et les packages mis à niveau. Pour sauvegarder les packages d'origine, n'oubliez pas de spécifier que les packages d'origine et les packages mis à niveau sont stockés dans le même dossier du système de fichiers. Si vous spécifiez d'autres options de stockage, l'Assistant ne sera pas en mesure de sauvegarder les packages d'origine.  
  
 Lorsqu'il sauvegarde les packages d'origine, l'Assistant stocke une copie des packages d'origine dans un dossier **SSISBackupFolder** . Il crée le dossier **SSISBackupFolder** en tant que sous-dossier du dossier qui contient les packages d'origine et les packages mis à niveau.  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-management-studio-or-at-the-command-prompt"></a>Pour sauvegarder les packages d'origine dans SQL Server Management Studio ou à l'invite de commandes  
  
1.  Enregistrez les packages d'origine à un emplacement du système de fichiers.  
  
    > [!NOTE]  
    >  L'option de sauvegarde de l'Assistant fonctionne uniquement avec les packages stockés dans le système de fichiers.  
  
2.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou à l'invite de commandes, exécutez l'Assistant Mise à niveau de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
3.  Dans la page **Sélectionner l'emplacement source** de l'Assistant, définissez la propriété **Source du package** à **Système de fichiers**.  
  
4.  Dans la page **Sélectionner l’emplacement de destination** de l’Assistant, sélectionnez **Enregistrer à l’emplacement source** pour enregistrer les packages mis à niveau au même emplacement que les packages d’origine.  
  
    > [!NOTE]  
    >  L'option de sauvegarde de l'Assistant n'est disponible que lorsque les packages mis à niveau sont stockés dans le même dossier que les packages d'origine.  
  
5.  Dans la page **Sélectionner les options de gestion des packages** de l'Assistant, sélectionnez l'option **Sauvegarder les packages d'origine** .  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-data-tools"></a>Pour sauvegarder les packages d'origine dans les outils de données SQL Server  
  
1.  Enregistrez les packages d'origine à un emplacement du système de fichiers.  
  
2.  Dans la page **Sélectionner les options de gestion des packages** de l'Assistant, sélectionnez l'option **Sauvegarder les packages d'origine** .  
  
    > [!WARNING]  
    >  Le **sauvegarder les packages d’origine** option ne s’affiche pas lorsque vous ouvrez un [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] ou [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] projet [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ce qui lance automatiquement l’Assistant.  
  
3.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], exécutez l'Assistant Mise à niveau de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
  
