---
title: Reporting Services SharePoint et Applications de Service | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 501aa9ee-8c13-458c-bf6f-24e00c82681b
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f612ac92f6741f83a92f29987cea03f662815e9d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37181496"
---
# <a name="reporting-services-sharepoint-service-and-service-applications"></a>Services Reporting Services SharePoint et applications de service
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint repose sur l’architecture de service SharePoint et utilise un service SharePoint et l’autre pour de nombreuses applications de service. Lorsque vous créez une application de service, le service devient disponible et la base de données d'application de service est générée. Vous pouvez créer plusieurs applications de service Reporting Services mais une application de service est suffisante pour la plupart des scénarios de déploiement.  
  
 Cette rubrique fournit les informations suivantes :  
  
-   [Création d'une application de service Reporting Services](#bkmk_createapp)  
  
-   [Modifier les associations de l'application de service avec un groupe de proxy](#bkmk_associations)  
  
-   [Modifier les propriétés d'une application de service](#bkmk_editserviceapplication)  
  
-   [Pour créer une application de service Reporting Services à l'aide de PowerShell](#bkmk_powershell_create_ssrs_serviceapp)  
  
-   [Tâches associées](#bkmk_related)  
  
##  <a name="bkmk_createapp"></a> Création d'une application de service Reporting Services  
 Vous pouvez utiliser l'Administration centrale de SharePoint ou les scripts PowerShell pour créer des applications de service [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Pour plus d’informations sur l’utilisation de l’Administration centrale de SharePoint, consultez la section « Créez une nouvelle application de service Reporting Services » dans [Installer le mode SharePoint de Reporting Services pour SharePoint 2010](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md). Consultez la section PowerShell plus loin dans cette rubrique pour obtenir un exemple de script PowerShell permettant de créer des applications de service.  
  
##  <a name="bkmk_associations"></a> Modifier les associations de l'application de service avec un groupe de proxy  
 La nouvelle page de création d'une application de service contient la section **Association d'application Web**. Cette section vous permet d'associer l'application de service que vous créez. Utilisez la procédure suivante pour modifier l'association et assigner une configuration personnalisée à l'application de service. Le même processus général peut également être utilisé pour ajouter le proxy au groupe par défaut plutôt que modifier l'association à un groupe personnalisé de l'application de service.  
  
1.  Dans l'Administration Centrale de SharePoint, sous Gestion des applications, cliquez sur **Configurer les associations des applications de service**.  
  
2.  Dans la page des Associations de l'application de service, modifiez la vue en **Applications de service**.  
  
3.  Recherchez et cliquez sur le nom de votre nouvelle [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] application de Service. Vous pourriez cliquer également sur la **valeur par défaut** du nom de groupe du proxy de l'application pour ajouter le proxy au groupe par défaut plutôt que compléter les étapes suivantes.  
  
4.  Sélectionnez **Personnalisé** dans la zone de sélection **Modifier le groupe de connexions suivant :**.  
  
5.  Activez la zone pour votre proxy et cliquez sur **OK**.  
  
##  <a name="bkmk_editserviceapplication"></a> Modifier les propriétés d'une application de service  
 Vous pouvez rouvrir la page de propriétés de l'application de service pour modifier les propriétés.  
  
1.  Dans l'Administration Centrale de SharePoint, sous le groupe Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Sélectionnez l'application de service en cliquant sur la colonne de type pour sélectionner la ligne entière. Si vous cliquez sur le nom de l'application, la page des options de gestion du service s'affiche au lieu des propriétés de l'application de service.  
  
3.  Dans le ruban Applications de service, cliquez sur **Propriétés**.  
  
##  <a name="bkmk_powershell_create_ssrs_serviceapp"></a> Pour créer une application de service Reporting Services à l'aide de PowerShell  
 Vous pouvez utiliser PowerShell pour créer l'application de service et le proxy. L'exemple suivant suppose que vous connaissez le pool d'applications qui sera utilisé par l'application de service.  
  
1.  Ajoutez l'objet de pool d'applications de votre nom de pool d'applications à une variable qui est passée dans l'action New.  
  
    ```  
    $appPoolName = get-spserviceapplicationpool “<application pool name>”  
    ```  
  
2.  Créez l'application de service en lui attribuant le nom et le nom de pool d'applications que vous fournissez.  
  
    ```  
    New-SPRSServiceApplication –Name ‘MyServiceApplication’ –ApplicationPool $appPoolName –DatabaseName ‘MyServiceApplicationDatabase’ –DatabaseServer ‘<Server Name>’  
    ```  
  
3.  Obtenez le nouvel objet d'application de service et dirigez l'objet dans le canal du nouvel applet de commande de proxy.  
  
    ```  
    Get-SPRSServiceApplication –name MyServiceApplication | New-SPRSServiceApplicationProxy “MyServiceApplicationProxy”  
    ```  
  
##  <a name="bkmk_related"></a> Tâches associées  
  
|Tâche|Lien|  
|----------|----------|  
|Gérez les paramètres de votre application de service.|[Gérer une application de service SharePoint Reporting Services](../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)|  
|Sauvegardez et restaurez l'application de service et ses composants connexes tels que les clés de chiffrement et le proxy.|[Applications de service SharePoint de sauvegarde et de restauration Reporting Services](../../2014/reporting-services/backup-and-restore-reporting-services-sharepoint-service-applications.md)|  
  
  
