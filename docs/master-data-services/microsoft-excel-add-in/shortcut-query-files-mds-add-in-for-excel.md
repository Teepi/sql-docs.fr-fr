---
title: Fichiers de requête de raccourci (Complément MDS pour Excel) | Microsoft Docs
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1ba0219a-6c40-41fa-aff9-8c8f41ef3220
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 14c18d4ff3690c07d324f6f98fae51fbba270d3e
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2018
ms.locfileid: "35335193"
---
# <a name="shortcut-query-files-mds-add-in-for-excel"></a>Fichiers de requête de raccourci (Complément MDS pour Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans le [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], utilisez les fichiers de requête de raccourci pour rapidement vous connecter et charger les données fréquemment utilisées. Vous pouvez également utiliser ces fichiers lorsque vous souhaitez partager des données MDS avec d'autres utilisateurs. Au lieu d'enregistrer la feuille de calcul et de l'envoyer par courrier électronique, vous pouvez enregistrer un fichier de requête de raccourci et l'envoyer de la même manière. De cette façon, vous êtes sûr que votre destinataire et vous-même êtes connectés au référentiel MDS pour récupérer les données les plus récentes.  
  
 Les fichiers de requête de raccourci sont des fichiers XML qui contiennent des informations sur :  
  
-   la connexion au référentiel MDS ;  
  
-   le modèle, la version, et l'entité ;  
  
-   tous les filtres appliqués lorsque le raccourci a été créé ;  
  
-   l'ordre de gauche à droite des colonnes lorsque le raccourci a été créé.  
  
 Vous pouvez enregistrer ces fichiers dans une liste et les choisir lorsque vous ouvrez le complément. Vous pouvez les exporter sur votre ordinateur ou dans un emplacement partagé, ou vous pouvez les envoyer à d'autres utilisateurs.  
  
 Pour ouvrir des fichiers de requête de raccourci, vous pouvez les importer ou bien double-cliquer sur leur icône pour les ouvrir automatiquement via l’application QueryOpener.  
  
## <a name="queryopener-application"></a>Application QueryOpener  
 Tous les utilisateurs qui installent [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] installent également une application appelée QueryOpener. Cette application sert à ouvrir des fichiers de requête de raccourci dans [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]. Si vous double-cliquez sur le fichier de requête de raccourci, cette application est automatiquement lancée pour ouvrir le fichier dans le complément.  
  
 Lorsque vous ouvrez un fichier de requête de raccourci avec cette application, vous êtes invité à créer une connexion « sécurisée », indiquant que vous faites confiance au contenu de cet emplacement. (Vous pouvez établir une connexion sécurisée en sélectionnant **Toujours autoriser une connexion à cette adresse** dans la fenêtre d’invite de commandes.) Chaque fois que vous marquez une connexion comme sécurisée, elle est ajouté à la liste. Si vous souhaitez effacer cette liste, ouvrez la boîte de dialogue **Paramètres** , puis dans la section **Serveurs ajoutés à la liste sécurisée** , cliquez sur **Effacer tout**.  
  
 L’emplacement par défaut de l’application est *lecteur*:\Program Files\Microsoft SQL Server\130\Master Data Services\Excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Enregistrez le contenu de la feuille de calcul active en tant que fichier de requête de raccourci.|[Enregistrer un fichier de requête de raccourci &#40;Complément MDS pour Excel#41;](../../master-data-services/microsoft-excel-add-in/save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Envoyez par courrier électronique un fichier de requête de raccourci qui représente le contenu de la feuille de calcul active.|[Envoyer par e-mail un fichier de requête de raccourci &#40;Complément MDS pour Excel#41;](../../master-data-services/microsoft-excel-add-in/email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenu associé  
  
-   [Connexions &#40;Complément MDS pour Excel#41;](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
-   [Complément Master Data Services pour Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
-   [Sécurité &#40;Master Data Services&#41;](../../master-data-services/security-master-data-services.md)  
  
  
