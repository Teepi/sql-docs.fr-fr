---
title: Transactions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0bf9bf1d02c09007bfeed695ec7f01ca34ef1e9b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411528"
---
# <a name="transactions"></a>Transactions
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB fournisseur implémente la prise en charge de la transaction locale. Le consommateur peut utiliser des transactions distribuées ou coordonnées à l'aide de Microsoft Distributed Transaction Coordinator (MS DTC). Pour les consommateurs qui exigent un contrôle des transactions qui s’étend sur plusieurs sessions, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB Native peut joindre des transactions lancées et gérées par MS DTC.  
  
 Par défaut, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client utilise un mode de transaction autocommit, où chaque action discrète dans une session de consommateur comprend une transaction complète sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mode de validation automatique du fournisseur OLE DB Native Client est local, et les transactions validées automatiquement ne couvrent jamais plus d’une session.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **ITransactionLocal** interface, ce qui permet au consommateur d’utiliser explicitement et implicitement démarrer des transactions sur une seule connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ne prend pas en charge les transactions locales imbriquées.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Prise en charge des transactions locales](supporting-local-transactions.md)  
  
-   [Prise en charge des transactions distribuées](supporting-distributed-transactions.md)  
  
-   [Niveaux d’isolation &#40;OLE DB&#41;](isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
