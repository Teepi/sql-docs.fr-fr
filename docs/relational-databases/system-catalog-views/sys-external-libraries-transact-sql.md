---
title: Sys.external_libraries (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_libraries catalog view
author: jeannt
ms.author: jeannt
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 3f6d833488982da777d0f146d55f0a67fa945de5
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39553259"
---
# <a name="sysexternallibraries-transact-sql"></a>Sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


Prend en charge la gestion des bibliothèques de package liés aux runtimes externes comme R ou Python.

## <a name="sysexternallibraries"></a>sys.external_libraries

Le sys.external_libraries de vue de catalogue répertorie une ligne pour chaque bibliothèque externe qui a été téléchargé dans la base de données.

|Nom de colonne |Type de données | Description|
|------|------|------|
|external_library_id |INT | ID de l’objet de bibliothèque externe. |
|NAME |sysname |Nom de la bibliothèque externe. Est unique au sein de la base de données par le propriétaire.|
|principal_id |INT |ID du principal qui possède cette bibliothèque externe. |
|langue | sysname | Nom de la langue ou le runtime qui prend en charge de la bibliothèque externe. Les valeurs valides sont « R ». Runtimes supplémentaires peuvent être ajoutées dans les futures.|
|portée |INT |0 pour une étendue publique ; 1 pour l’étendue privée |  
|scope_desc |varchar(7) |Indique si le package est public ou privé|


## <a name="see-also"></a>Voir aussi  
[sys.external_library_files](sys-external-library-files-transact-sql.md)  
[CRÉER UNE BIBLIOTHÈQUE EXTERNE](../../t-sql/statements/create-external-library-transact-sql.md)  
[Gestion des packages pour SQL Server R Services](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
