---
title: Déterminer si le moteur de base de données est installé et démarré | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, determining if installed
- verifying Database Engine installation
- viewing Database Engine installation
- installed Database Engine verification [SQL Server]
ms.assetid: babb02e4-3521-4b75-b5df-e09205594375
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 619fbc9818e627d58a018723475f6f97493df49b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265366"
---
# <a name="determine-whether-the-database-engine-is-installed-and-started"></a>Déterminer si le moteur de base de données est installé et démarré
  Lorsqu'elle est réussie, l'installation du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] installe des fichiers dans le système de fichiers, crée des entrées dans le Registre et installe plusieurs outils. Cette rubrique explique comment déterminer si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est installé et démarré dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
##  <a name="SSMSProcedure"></a> Utilisation du Gestionnaire de configuration SQL Server  
  
#### <a name="how-to-view-and-start-the-database-engine-by-using-sql-server-configuration-manager"></a>Comment afficher et démarrer le moteur de base de données à l'aide du Gestionnaire de configuration SQL Server  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, pointez sur **Microsoft SQL Server**, pointez sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
     Si ces éléments ne sont pas visibles dans le menu **Démarrer** , cela signifie que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas correctement installé. Exécutez le programme d'installation pour installer le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
2.  Dans le **Gestionnaire de configuration SQL Server**, dans le volet gauche, cliquez sur **Services SQL Server**. Le volet droit répertorie plusieurs services associés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est installé, le service [!INCLUDE[ssDE](../../includes/ssde-md.md)] apparaît en tant que **SQL Server (MSSQLSERVER)** s’il s’agit de l’instance par défaut, ou en tant que **SQL Server (**\<*nom_instance*>**)**, si [!INCLUDE[ssDE](../../includes/ssde-md.md)] est installé en tant qu’instance nommée. Sauf modification du nom de l’instance, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] s’installe en tant qu’instance nommée sous le nom **SQLEXPRESS**. Si l'icône du service est un triangle vert, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est en cours d'exécution. Par contre, si l'icône est un carré rouge, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est arrêté.  
  
3.  Pour démarrer le [!INCLUDE[ssDE](../../includes/ssde-md.md)],dans le volet droit, cliquez avec le bouton droit sur le [!INCLUDE[ssDE](../../includes/ssde-md.md)], puis cliquez sur **Démarrer**.  
  
> [!NOTE]  
>  Au cours de l'installation, l'utilisateur peut choisir l'emplacement où les fichiers programmes et les fichiers de base de données vont être installés. S’il accepte l’emplacement par défaut, les fichiers sont installés dans [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] et C:\Program Files\Microsoft SQL Server\MSSQL.*x*, où *x* est un nombre.  
  
  
