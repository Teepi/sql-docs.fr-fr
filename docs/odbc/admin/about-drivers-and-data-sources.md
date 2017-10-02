---
title: "Sur les pilotes et les Sources de données | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 79ae9e95ce31df371366e9073cb36f88c5bd9ece
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="about-drivers-and-data-sources"></a>Sur les pilotes et les Sources de données
*Pilotes* sont les composants qui traitent des demandes d’ODBC et retournent des données à l’application. Si nécessaire, pilotes de modifier la requête d’une application dans un formulaire qui est interprété par la source de données. Vous devez utiliser le programme d’installation du pilote pour ajouter ou supprimer un pilote à partir de votre ordinateur.  
  
 *Sources de données* sont les bases de données ou les fichiers accédés par un pilote et sont identifiés par un nom de source de données (DSN). Utilisez l’administrateur de Source de données ODBC pour ajouter, configurer et supprimer des sources de données à partir de votre système. Les types de sources de données qui peuvent être utilisés sont décrits dans le tableau suivant.  
  
|Source de données| Description|  
|-----------------|-----------------|  
|Utilisateur|Sources de données utilisateur sont propres à un ordinateur et peuvent être utilisées uniquement par l’utilisateur actuel. Ils sont inscrits dans la sous-arborescence de Registre HKEY_CURRENT_USER.|  
|Système|Sources de données système sont locales sur un ordinateur plutôt que dédié à un utilisateur. Le système ou n’importe quel utilisateur disposant de privilèges peut utiliser une source de données configurée avec un DSN système. Sources de données système sont enregistrés dans la sous-arborescence de Registre HKEY_LOCAL_MACHINE.|  
|Fichier|DSN de fichier sont des sources de fichier qui peuvent être partagés entre tous les utilisateurs qui ont les mêmes pilotes installés et par conséquent ont accès à la base de données. Ces sources de données ne doivent pas être dédiés à un utilisateur, ni être local sur un ordinateur. Noms de source de données de fichiers ne sont pas identifiées par les entrées de Registre dédié ; au lieu de cela, ils sont identifiés par un nom de fichier avec une extension .dsn.|  
  
 Sources de données utilisateur et système sont désignés collectivement par *machine* des sources de données, car elles sont locales sur un ordinateur.  
  
 Chacune de ces sources de données possède un onglet dans le **administrateur de sources de données ODBC** boîte de dialogue. Pour plus d’informations sur les sources de données disponibles, consultez [Sources de données](../../odbc/reference/data-sources.md).