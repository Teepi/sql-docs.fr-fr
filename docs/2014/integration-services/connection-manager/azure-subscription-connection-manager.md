---
title: Gestionnaire de connexions d’abonnement Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpsubscrconn.f1
- sql11.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1fa0589e7ac68f3662929c6316cdd0ddf427911d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306109"
---
# <a name="azure-subscription-connection-manager"></a>Gestionnaire de connexions d’abonnement Azure
  Le Gestionnaire de connexions Azure HDInsight permet à un package SSIS pour vous connecter à un abonnement Azure en utilisant les valeurs que vous spécifiez pour les propriétés : ID d’abonnement Azure et certificat de gestion.  
  
1.  Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS** ci-dessus, sélectionnez **Abonnement Azure**, puis cliquez sur **Ajouter**.  Vous devez voir s’afficher la boîte de dialogue **Éditeur du gestionnaire de connexions d’abonnement Azure** .  
  
     ![SSIS-AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "AzureSubscriptionManager de SSIS")  
  
2.  Entrez votre ID d’abonnement Azure, qui identifie de façon unique un abonnement Azure, pour l’ **ID d’abonnement Azure**.  Cette valeur est indiquée sur le [portail de gestion Azure](https://manage.windowsazure.com) , à la page **Paramètres** :  
  
     ![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")  
  
3.  Choisissez **Emplacement du magasin de certificats de gestion** et **Nom du magasin de certificats de gestion** dans les listes déroulantes.  
  
4.  Entrez l’ **empreinte numérique du certificat de gestion** ou cliquez sur **Parcourir** pour choisir un certificat dans le magasin sélectionné. Le certificat doit être téléchargé en tant que certificat de gestion pour l’abonnement. Pour ce faire, cliquez sur **Télécharger** dans la page suivante du portail Azure (voir cet [article MSDN](https://msdn.microsoft.com/library/azure/gg551722.aspx) pour plus de détails).  
  
     ![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")  
  
5.  Cliquez sur **Tester la connexion** pour tester la connexion.  
  
6.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
  
