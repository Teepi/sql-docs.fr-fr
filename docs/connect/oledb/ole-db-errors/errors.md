---
title: Erreurs | Microsoft Docs
description: Erreurs
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 477c89e8d058d2f2971dc295c3bf8e1449c5a3d9
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39105855"
---
# <a name="errors"></a>Erreurs
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Les objets OLE/COM signalent les erreurs via le code de retour HRESULT des fonctions membres objets. Un valeur HRESULT OLE/COM est une structure de bits comprimée. OLE fournit des macros qui déréférencent les membres de la structure.  
  
 OLE/COM spécifie l’interface **IErrorInfo**. L’interface propose des méthodes comme **GetDescription**. Ceci permet aux clients d'extraire des informations détaillées sur les erreurs à partir des serveurs OLE/COM. OLE DB étend **IErrorInfo** pour prendre en charge le retour de plusieurs paquets d’informations d’erreur lors de l’exécution d’une fonction à un seul membre.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut retourner plusieurs erreurs. Une application peut récupérer les erreurs de serveur une par une en appelant [IMultipleResults::GetResult](http://go.microsoft.com/fwlink/?LinkId=129630) en combinaison avec ISQLErrorInfo et IErrorRecords.  
  
 Le pilote OLE DB pour SQL Server expose la valeur **IErrorInfo** améliorée par un enregistrement OLE DB, la valeur **ISQLErrorInfo** personnalisée et les interfaces d’objet erreur [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) spécifiques au fournisseur.  
  
 Pour plus d’informations sur le suivi des erreurs, consultez [Suivi de l’accès aux données](http://go.microsoft.com/fwlink/?LinkId=125805). Pour plus d’informations sur les améliorations apportées au suivi d’erreur ajouté dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], consultez [l’accès à des informations de Diagnostic dans le journal des événements étendus](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Codes de retour](../../oledb/ole-db-errors/return-codes.md)  
  
-   [Informations dans les interfaces d’erreur](../../oledb/ole-db-errors/information-in-error-interfaces.md)  
  
-   [Détails des erreurs SQL Server](../../oledb/ole-db-errors/sql-server-error-detail.md)  
  
-   [Extraction des informations sur les erreurs](../../oledb/ole-db-errors/retrieving-error-information.md)  
  
-   [Résultats des messages SQL Server](../../oledb/ole-db-errors/sql-server-message-results.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Programmation OLE DB Driver pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
