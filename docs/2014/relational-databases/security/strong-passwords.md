---
title: Mots de passe forts | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 58aea76071a92e1ea9638a745d7a8493f9b778ec
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083011"
---
# <a name="strong-passwords"></a>Mots de passe forts
  Les mots de passe peuvent représenter le point le plus faible dans le déploiement de sécurité d'un serveur. Vous devez toujours faire preuve de la plus grande attention lorsque vous choisissez un mot de passe. Un mot de passe fort présente les caractéristiques suivantes :  
  
-   il comprend au moins 8 caractères ;  
  
-   il combine des lettres, des chiffres et des symboles ;  
  
-   il ne se trouve pas dans un dictionnaire ;  
  
-   il ne correspond pas au nom d'une commande ;  
  
-   il ne correspond pas au nom d'une personne ;  
  
-   il ne correspond pas au nom d'un utilisateur ;  
  
-   il ne correspond pas au nom d'un ordinateur ;  
  
-   il est modifié régulièrement ;  
  
-   il est complètement différent des mots de passe précédents.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les mots de passe peuvent compter jusqu’à 128 caractères, comprenant des lettres, des symboles et des chiffres. Étant donné que les noms de connexion, les noms d'utilisateurs, les rôles et les mots de passe sont souvent utilisés dans des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] , certains symboles doivent être placés entre guillemets (") ou crochets ([ ]). Utilisez ces délimiteurs dans les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] lorsque le nom de connexion, le nom d'utilisateur, le rôle ou le mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] présente les caractéristiques suivantes :  
  
-   il contient ou commence par un espace ;  
  
-   Commence par la $ ou \@ caractère.  
  
 Un nom d’accès ou un mot de passe, s’il est utilisé dans une chaîne de connexion OLE DB ou ODBC, ne doit pas contenir les caractères suivants: [] {}() , ; ? * ! \@. Ces caractères servent en effet à initialiser une connexion ou à séparer les valeurs de la chaîne de connexion.  
  
## <a name="related-content"></a>Contenu associé  
 [Stratégie de mot de passe](password-policy.md)  
  
  
