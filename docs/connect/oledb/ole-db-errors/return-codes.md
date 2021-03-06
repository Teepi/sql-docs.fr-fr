---
title: Codes de retour | Microsoft Docs
description: Codes de retour
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
- OLE DB error handling, return codes
- OLE DB Driver for SQL Server, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: ec559040fceb5116ca83cc4eb295580479224b04
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39107045"
---
# <a name="return-codes"></a>Codes de retour
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Au niveau le plus élémentaire, une fonction membre réussit ou échoue. À un niveau plus précis, une fonction peut réussir, mais son succès peut ne pas être ce que le développeur d'applications prévoyait.  
  
 Pour plus d’informations sur les codes de retour OLE DB, consultez [Codes de retour (OLE DB)](http://go.microsoft.com/fwlink/?LinkId=101631).  
  
 Lorsqu’un pilote OLE DB pour la fonction membre de SQL Server retourne S_OK, la fonction a réussi.  
  
 Quand une fonction membre du pilote OLE DB pour SQL Server ne retourne pas S_OK, les macros OLE/COM FAILED et IS_ERROR de décompactage de HRESULT peuvent déterminer le succès ou l’échec global d’une fonction.  
  
 Si FAILED ou IS_ERROR retourne la valeur TRUE, le consommateur du pilote OLE DB pour SQL Server a l’information selon laquelle l’exécution de la fonction membre a échoué. Lorsque FAILED ou IS_ERROR retourne FALSE et que HRESULT n’est pas égal S_OK, le pilote OLE DB pour SQL Server consommateur est assuré de la fonction a réussi d’une certaine façon. Le consommateur peut extraire des informations détaillées sur ce retour « réussite avec informations » à partir des interfaces d’erreur du pilote OLE DB pour SQL Server. De même, dans le cas où une fonction échoue clairement (la macro FAILED retourne TRUE), les informations d’erreur étendues sont disponibles via les interfaces d’erreur du pilote OLE DB pour SQL Server.  
  
 Pilote OLE DB pour les consommateurs de SQL Server rencontrent généralement le retour HRESULT de DB_S_ERRORSOCCURRED « réussi avec informations ». En général, les fonctions membres qui retournent DB_S_ERRORSOCCURRED définissent un ou plusieurs paramètres qui remettent les valeurs d'état au consommateur. Il est possible que le consommateur ne dispose d’aucune information d’erreur autre que celle retournée dans les paramètres état-valeur : les consommateurs doivent donc implémenter la logique d’application nécessaire pour extraire les valeurs d’état quand elles sont disponibles.  
  
 Le pilote OLE DB pour les fonctions de membre de SQL Server ne renvoient pas le code de réussite S_FALSE. Tous les pilote OLE DB pour les fonctions de membre SQL Server retournent toujours S_OK pour indiquer la réussite.  
  
## <a name="see-also"></a> Voir aussi  
 [Erreurs](../../oledb/ole-db-errors/errors.md)  
  
  
