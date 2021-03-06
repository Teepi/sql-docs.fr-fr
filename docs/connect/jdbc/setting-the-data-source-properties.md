---
title: Propriétés de la définition des données Source | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9957a3273f2e33fea59560c4af30ec0315eea92
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39458023"
---
# <a name="setting-the-data-source-properties"></a>Définition des propriétés de la source de données

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Les sources de données représentent le mécanisme recommandé de création de connexions JDBC dans un environnement Java EE (Java Platform, Enterprise Edition). Elles offrent des connexions, des connexions regroupées et des connexions distribuées sans codage effectué de manière irréversible des propriétés de connexion en code Java. Toutes les sources de données du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] peuvent définir ou obtenir la valeur d’une propriété quelconque en utilisant respectivement les méthodes d’accesseur Get et Set appropriées.

Les produits Java EE, tels que les serveurs d'applications et les moteurs servlet/JSP, vous permettent généralement de configurer des sources de données pour l'accès à la base de données. Toute propriété répertoriée dans la rubrique [Définition des propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md) peut être spécifiée à n’importe quel endroit où la configuration vous permet d’entrer une propriété en tant que paire propriété=valeur.

Pour plus d’informations sur les sources de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], consultez la classe [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md). Pour obtenir un exemple montrant comment utiliser la classe SQLServerDataSource pour établir une connexion à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] de base de données, consultez [exemple de Source de données](../../connect/jdbc/data-source-sample.md).

## <a name="see-also"></a> Voir aussi

[Connexion à SQL Server avec le pilote JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
