---
title: Configurer une base de données miroir chiffrée | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- database master key [SQL Server], database mirroring
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
caps.latest.revision: 24
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4b8ac0e68b60e44dcb18e342418dffa10365e17e
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35312128"
---
# <a name="set-up-an-encrypted-mirror-database"></a>Configurer une base de données miroir chiffrée
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Pour activer le déchiffrement automatique de la clé principale d'une base de données miroir, vous devez fournir le mot de passe utilisé pour chiffrer la clé principale à l'instance de serveur miroir. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures incluent des mécanismes de transfert du mot de passe. Utilisez **sp_control_dbmasterkey_password** pour créer des informations d’identification destinées à la clé principale de la base de données avant de démarrer la mise en miroir de celle-ci. Vous devez répéter cette procédure pour chaque base de données qui sera mise en miroir. Pour plus d’informations, consultez [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md).  
  
> [!CAUTION]  
>  N’activez pas le déchiffrement avec basculement d’une base de données qui doit rester inaccessible à l’administrateur système ( **sa** ) et à d’autres principaux de serveur hautement privilégiés. Vous pouvez configurer une base de données de sorte que la hiérarchie de ses clés ne puisse pas être déchiffrée par la clé principale du service. Cette option est prise en charge comme défense renforcée des bases de données contenant des informations qui ne doivent pas être accessibles à l’administrateur système ( **sa** ) ou à d’autres principaux de serveur hautement privilégiés. L’activation du déchiffrement avec basculement de cette base de données supprime cette défense renforcée, en permettant à l’administrateur système ( **sa** ) et à d’autres principaux de serveur hautement privilégiés de déchiffrer la base de données.  
  
## <a name="see-also"></a> Voir aussi  
 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Configuration de la mise en miroir d’une base de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)  
  
  
