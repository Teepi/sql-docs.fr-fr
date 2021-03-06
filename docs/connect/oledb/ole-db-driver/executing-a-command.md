---
title: Exécution d’une commande | Microsoft Docs
description: Exécution d’une commande
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- commands [OLE DB Driver for SQL Server]
- OLE DB, executing commands
- sessions [OLE DB Driver for SQL Server]
- OLE DB extensions for XML
- OLE DB Driver for SQL Server, command execution
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 86ce7ef5abcc3a365428c015603b9e9779c22190
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39105966"
---
# <a name="executing-a-command"></a>Exécution d'une commande
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Une fois la connexion à une source de données est établie, le consommateur appelle la **IDBCreateSession::CreateSession** méthode pour créer une session. La session agit en guise de commande, d'ensemble de lignes ou de fabrique de transactions.  
  
 Pour utiliser directement des tables individuelles ou des index, le consommateur demande l’interface **IOpenRowset**. La méthode **IOpenRowset::OpenRowset** ouvre et retourne un ensemble de lignes qui inclut toutes les lignes d’une même table de base ou d’un même index.  
  
 Pour exécuter une commande (par exemple SELECT \* FROM Authors), le consommateur demande l’interface **IDBCreateCommand**. Le consommateur peut exécuter le **IDBCreateCommand::CreateCommand** méthode pour créer un objet de commande et de demande pour le **ICommandText** interface. Le **ICommandText::SetCommandText** méthode est utilisée pour spécifier la commande qui doit être exécuté.  
  
 La commande **Execute** est utilisée pour exécuter la commande. La commande peut être un nom de procédure ou une instruction SQL. Toutes les commandes ne génèrent pas un objet de jeu de résultats (ensemble de lignes). Les commandes, telles que SELECT * FROM Authors, produisent un jeu de résultats.  
  
## <a name="see-also"></a> Voir aussi  
 [Création d’une application OLE DB Driver pour SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)  
  
  
