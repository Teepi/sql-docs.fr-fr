---
title: Méthode GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
api_name:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
caps.latest.revision: 25
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 42898aba8f621688ba229fcf01d367b4da1a4f71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149030"
---
# <a name="generatedatabasecreationscript-method-wmi-msreportserverconfigurationsetting"></a>Méthode GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting)
  Génère un script SQL qui peut être utilisé pour créer une base de données du serveur de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Databasename*  
 Chaîne contenant le nom de la base de données du serveur de rapports à créer.  
  
 *Lcid*  
 Valeur utilisée pour la localisation des noms de rôles.  
  
 *IsSharePointMode*  
 Indique s'il convient de créer la base de données en mode natif ou mode SharePoint.  
  
> [!IMPORTANT]  
>  À compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], *IsSharePointMode* = `True` n’est pas pris en charge, car en mode SharePoint, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est un SharePoint service partagé et n’est pas contrôlé par le fournisseur WMI. Vous devez toujours définir ce paramètre `False`.  
  
 *Script*  
 [out] Chaîne contenant le script SQL généré.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Cette méthode génère un script SQL qui crée des bases de données du serveur de rapports pour la version du serveur de rapports actuellement connecté.  
  
 La valeur fournie dans le paramètre *DatabaseName* doit être conforme aux conventions d’affectation des noms de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 La méthode ne vérifie pas l'existence de la base de données lors de la génération du script.  
  
 Cette méthode ne vérifie pas l'existence de la base de données du serveur de rapports lors de la génération du script.  
  
 Le script généré prend en charge [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
