---
title: MSSQLSERVER_33028 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b2820abe304ce16234029caa16164285f6f66f9b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415319"
---
# <a name="mssqlserver33028"></a>MSSQLSERVER_33028
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|33028|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SEC_CRYPTOPROV_CANTOPENSESSION|  
|Texte du message|Impossible d'ouvrir la session pour %S_MSG '%.*ls'. Code d'erreur du fournisseur : %d.|  
  
## <a name="explanation"></a>Explication  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’a pas pu ouvrir le fournisseur de services de chiffrement répertorié dans le message d’erreur. Le fournisseur de services de chiffrement a fourni le code d'erreur répertorié. Il peut s'avérer nécessaire de contacter votre fournisseur de services de chiffrement pour plus d'informations sur l'erreur.  
  
|Code d'erreur|Description|  
|----------------|-----------------|  
|0|Réussite. Aucune erreur.|  
| 1|Échec. Une erreur non spécifiée ou inattendue s'est produite. Aucune information supplémentaire n'est disponible.|  
|2|Mémoire tampon insuffisante. Impossible d'allouer de l'espace au fournisseur de services de chiffrement.|  
|3|Non pris en charge. Le fournisseur de services de chiffrement n'est pas pris en charge par cette version. Sélectionnez-en un autre.|  
|4|Introuvable. Le fournisseur de services de chiffrement spécifié est absent ou vous n'avez pas l'autorisation d'accéder aux fichiers.|  
|5|Échec d'autorisation. Peut provenir de l'indication d'un mot de passe ou nom d'utilisateur incorrect lors de la création des informations d'identification. Peut être généré si les informations d'identification n'existent pas.|  
|6|Argument non valide. Un argument non valide a été transmis au fournisseur de services de chiffrement.|  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Corrigez l'erreur ou contactez le fournisseur de services de chiffrement pour plus d'informations.  
  
  
