---
title: Se connecter à un abonnement Microsoft Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cca5a270-643f-4677-8802-98464f19f82a
caps.latest.revision: 4
author: dagiro
ms.author: v-dagir
manager: craigg
ms.openlocfilehash: 35a9b5426c071e089036dbe0aaaadc1783f11c24
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983731"
---
# <a name="connect-to-a-microsoft-azure-subscription"></a>Se connecter à un abonnement Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Utilisez **Se connecter à un abonnement Microsoft Azure** pour inscrire un conteneur d’objets blob Azure auprès de votre instance de SQL Server.  La boîte de dialogue crée une signature d’accès partagé et une stratégie d’accès stockée sur un conteneur d’objets blob Azure, puis crée des informations d’identification SQL Server.  Cette boîte de dialogue s’affiche quand vous utilisez la tâche de sauvegarde ou de restauration à partir de SQL Server Management Studio et que l’opération implique une unité URL.

## <a name="limitation"></a>Limitation
**Se connecter à un abonnement Microsoft** ne fonctionne qu’avec un compte de stockage Azure créé par le biais du modèle de déploiement de gestion des services (classique).  Pour plus d’informations sur les modèles de déploiement Azure, consultez [Déploiement Azure Resource Manager et déploiement classique](https://azure.microsoft.com/documentation/articles/resource-manager-deployment-model/).

## <a name="options"></a>Options
**Connexion**     
Connectez-vous avec le compte Azure approprié.

**Sélectionner l’abonnement à utiliser**      
Sélectionnez l’abonnement souhaité dans la liste déroulante.

**Sélectionnez un compte de stockage**  
Sélectionnez le compte de stockage souhaité dans la liste déroulante.

**Sélectionner un conteneur d’objets blob**   
Sélectionnez le conteneur d’objets blob souhaité dans la liste déroulante.

**Expiration de la stratégie d’accès partagé**   
La stratégie d’accès partagé expire à la date indiquée.  La date d’expiration par défaut est une année à partir de la création.  Modifiez-la comme vous le souhaitez.

**Signature d’accès partagé générée**   
La zone de texte enrichi affiche la signature d’accès partagé générée.

**Créer des informations d’identification**   
Ce bouton génère une stratégie d’accès stockée et une signature d’accès partagé, puis crée des informations d’identification SQL Server.
