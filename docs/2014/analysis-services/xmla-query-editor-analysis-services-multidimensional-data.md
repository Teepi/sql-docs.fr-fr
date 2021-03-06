---
title: Éditeur de requête XMLA (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.editor.xmla.f1
helpviewer_keywords:
- XMLA Query Editor
- Query Editor [XMLA]
ms.assetid: 14623019-7839-4038-9d12-2f8953d2ec04
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 221ea55990b98a9723928f52cd5432f13760cc91
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211429"
---
# <a name="xmla-query-editor-analysis-services---multidimensional-data"></a>Éditeur de requête XMLA (Analysis Services - Données multidimensionnelles)
  Utilisez l'Éditeur de requête XMLA pour créer et exécuter des instructions et des scripts écrits en langage XMLA.  
  
## <a name="features"></a>Fonctionnalités  
  
-   Tapez les scripts dans le volet d'éditeur de requête de l'Éditeur de requête XMLA.  
  
-   Pour exécuter les scripts, appuyez sur **F5**, ou cliquez sur **Exécuter** dans la barre d'outils ou dans le menu **Requête** , cliquez sur **Exécuter**. Si une partie du code est sélectionnée, seule cette partie du code est exécutée. En revanche, si aucun code n'est sélectionné, le contenu entier de l'Éditeur de requête XMLA est exécuté.  
  
-   Affichage des métadonnées des cubes et des autres objets contenus dans une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans le volet des métadonnées.  
  
-   Pour obtenir de l'aide sur la syntaxe XMLA, sélectionnez un mot clé dans l'Éditeur de requête XMLA, puis cliquez sur **F1**.  
  
-   Pour obtenir une aide dynamique sur la syntaxe XMLA, dans le menu **?** (Aide), cliquez sur **Aide dynamique** pour ouvrir le composant correspondant. Avec l'Aide dynamique, les rubriques d'aide apparaissent dans la fenêtre **Aide dynamique** lorsque vous tapez des mots clés dans l'Éditeur de requête.  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>Barre d'outils Éditeurs SQL Server Analysis Services  
 Lorsque l'Éditeur de requête XMLA est ouvert, la barre d'outils **Éditeurs SQL Server Analysis Services** s'affiche avec les boutons ci-après.  
  
|Terme|Définition|  
|----------|----------------|  
|**Se connecter**|Ouvre la boîte de dialogue **Se connecter au serveur** pour établir une connexion à une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Déconnecter**|Déconnecte l'Éditeur de requête XMLA d'une instance d' [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .|  
|**Modifier la connexion**|Ouvre la boîte de dialogue **Se connecter au serveur** pour établir une connexion à une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] différente.|  
|**Nouvelle requête avec la connexion actuelle**|Ouvre une nouvelle fenêtre d'Éditeur de requête XMLA, avec les informations de connexion issues de la fenêtre active.|  
|**Bases de données disponibles**|Se connecte à une base de données différente [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur la même instance.|  
|**Exécuter**|Exécute le code sélectionné. Si aucun code n'est sélectionné, cette option exécute le code entier dans l'Éditeur de requête XMLA.|  
|**Analyser**|Contrôle la syntaxe du code sélectionné. Si aucun code n'est sélectionné, cette option vérifie la syntaxe de toute la fenêtre de l'Éditeur de requête XMLA.|  
|**Annuler l'exécution de la requête**|Envoie une demande d'annulation au serveur. Certaines requêtes ne peuvent pas être annulées immédiatement et doivent attendre une condition d'annulation appropriée. Une fois les requêtes annulées, un certain délai peut exister au cours de l'annulation des transactions.|  
  
## <a name="xmla-query-editor-window"></a>Fenêtre Éditeur de requête XMLA  
 Les options suivantes sont disponibles dans l'Éditeur de requête XMLA :  
  
|Terme|Définition|  
|----------|----------------|  
|**Fenêtre Éditeur de requête**|Tapez les instructions et les scripts XMLA à exécuter par l'Éditeur de requête XMLA.<br /><br /> Le menu contextuel de l'éditeur de requête contient les options suivantes :<br /><br /> **Couper**: copie la sélection actuelle dans le Presse-papiers et supprime la sélection de la fenêtre d’éditeur de requête.<br />**Copier**: Copie la sélection actuelle dans le Presse-papiers.<br />**Coller**: colle le contenu du Presse-papiers à la sélection actuelle.<br />**Se connecter**: ouvre la boîte de dialogue **Se connecter au serveur** pour établir une connexion à une instance [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .<br />**Déconnecter**: déconnecte l’éditeur de requête en cours d’un [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.<br />**Déconnecter toutes les requêtes**: déconnecte tous les éditeurs de requête ouverts.<br />**Modifier la connexion**: ouvre le **se connecter au serveur** boîte de dialogue pour établir une connexion à un autre [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.<br />**Ouvrir le serveur dans l’Explorateur d’objets**: ouvre le [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance à laquelle l’éditeur de requête actuel est connecté dans **Explorateur d’objets**.<br />**Exécutez**: exécute le code sélectionné, ou si aucun code n’est sélectionné, exécute le code entier dans l’éditeur de requête actuel.<br />**Fenêtre Propriétés**: affiche la **propriétés** fenêtre dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour la fenêtre de requête active.<br />**Options de requête**: affiche la **Options de requête** boîte de dialogue.|  
|**Fenêtre des résultats**|Affiche les résultats d'une instruction ou d'un script XMLA sous forme de texte.|  
|**Fenêtre de messages**|Affiche des informations sur l'exécution d'une instruction ou d'un script XMLA. Cette fenêtre, par exemple, contient les erreurs détectées lors de l'exécution ou le nombre de cellules extraites après l'exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de requête MDX &#40;Analysis Services - données multidimensionnelles&#41;](mdx-query-editor-analysis-services-multidimensional-data.md)   
 [Éditeur de requête DMX &#40;Analysis Services - Exploration de données&#41;](dmx-query-editor-analysis-services-data-mining.md)   
 [Les éditeurs de texte et de requête &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)   
 [Raccourcis clavier dans SQL Server Management Studio](../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
  
  
