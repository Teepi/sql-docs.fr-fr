---
title: Utilisation des fichiers bibliothèques et d’en-tête OLE DB Driver pour SQL Server | Microsoft Docs
description: Utilisation des fichiers bibliothèques et d’en-tête OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- header files [OLE DB Driver for SQL Server]
- MSOLEDBSQL, header files
- OLE DB, header files
- library files [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, header files
- data access [OLE DB Driver for SQL Server], header files
- data access [OLE DB Driver for SQL Server], library files
- OLE DB Driver for SQL Server, library files
- MSOLEDBSQL, library files
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 847d25310542a6eb10f929a04ee4e5e066bbb38e
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108701"
---
# <a name="using-the-ole-db-driver-for-sql-server-header-and-library-files"></a>Utilisation des fichiers bibliothèques et d’en-tête OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour l’en-tête de SQL Server et les fichiers de bibliothèque sont installés lorsque le pilote OLE DB pour l’option de kit de développement logiciel de SQL Server est sélectionné au cours du processus d’installation. Lors du développement d'une application, il importe de copier et d'installer tous les fichiers requis pour le développement sur votre environnement de développement. Pour plus d’informations sur l’installation et la redistribution du pilote OLE DB pour SQL Server, consultez [installation OLE DB Driver pour SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md).  
  
 Le pilote OLE DB pour l’en-tête de SQL Server et les fichiers de bibliothèque sont installés à l’emplacement suivant :  
  
 *%Program Files%* \Microsoft SQL Server\Client SDK\OLEDB\181\SDK  
  
 Le pilote OLE DB pour le fichier d’en-tête SQL Server (msoledbsql.h) peut être utilisé pour ajouter le pilote OLE DB pour la fonctionnalité d’accès de données de SQL Server à vos applications personnalisées. Le fichier d’en-tête OLE DB Driver pour SQL Server contient l’ensemble des définitions, attributs, propriétés et interfaces nécessaires pour tirer parti des nouvelles fonctionnalités introduites dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Outre le pilote OLE DB pour le fichier d’en-tête SQL Server, il existe également un fichier de bibliothèque msoledbsql.lib qui est la bibliothèque d’exportation pour [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) fonctionnalité.  
  
 Le fichier d’en-tête OLE DB Driver pour SQL Server offre une compatibilité descendante avec le fichier d’en-tête sqloledb.h utilisé avec MDAC (Microsoft Data Access Components), mais ne contient pas les CLSID pour SQLOLEDB (le fournisseur OLE DB pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] inclus avec MDAC) ni les symboles pour la fonctionnalité XML (non prise en charge par OLE DB Driver pour SQL Server).    
  
 Les applications OLE DB qui utilisent le pilote OLE DB pour SQL Server doivent uniquement référencer msoledbsql.h. Si une application utilise MDAC (SQLOLEDB) et OLE DB Driver pour SQL Server, elle peut faire référence à sqloledb.h et msoledbsql.h, mais la référence à sqloledb.h doit être placée en premier.  
  
## <a name="using-the-ole-db-driver-for-sql-server-header-file"></a>À l’aide de OLE DB Driver pour SQL Server-fichier d’en-tête  
 Pour utiliser le pilote OLE DB pour le fichier d’en-tête SQL Server, vous devez utiliser un **incluent** instruction au sein de votre code de programmation C/C++. Les sections suivantes décrivent comment effectuer cette applications OLE DB.  
  
> [!NOTE]  
>  Le pilote OLE DB pour les fichiers de bibliothèque et d’en-tête SQL Server peut uniquement être compilé à l’aide de Visual Studio C++ 2012 ou version ultérieure.  
  
### <a name="ole-db"></a>OLE DB  
 Pour utiliser le pilote OLE DB pour le fichier d’en-tête SQL Server dans une application OLE DB, à l’aide de lignes de code de programmation suivantes :  
  
```    
include "msoledbsql.h";  
```  
  
> [!NOTE]  
>  Si l’application possède un **incluent** instruction pour sqloledb.h, le **incluent** instruction pour msoledbsql.h doit venir après elle.  
  
 Lorsque vous créez une connexion à une source de données via OLE DB Driver pour SQL Server, utilisez « MSOLEDBSQL » comme chaîne de nom du fournisseur.  

  
## <a name="component-names-and-properties-by-version"></a>Noms des composants et propriétés par version  

|Propriété|OLE DB Driver pour SQL Server|MDAC|  
|--------|----------------------------|----|   
|PROGID pour OLE DB|MSOLEDBSQL|SQLOLEDB|  
|Nom du fichier d'en-tête OLE DB|msoledbsql.h|Sqloledb.h|  
|DLL du fournisseur OLE DB|msoledbsql.dll|Sqloledb.dll| 
  
  
## <a name="static-linking-and-bcp-functions"></a>Liaison statique et fonctions BCP  
 Lorsqu'une application utilise des fonctions BCP, il est important pour l'application de spécifier dans la chaîne de connexion le pilote de la même version fourni avec le fichier d'en-tête et la bibliothèque utilisés pour compiler l'application.  
  
 Pour plus d’informations, consultez exécution [effectuant des opérations de copie en bloc](../../oledb/features/performing-bulk-copy-operations.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
