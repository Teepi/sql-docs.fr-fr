---
title: Bibliothèques de connectivité et frameworks | Documents Microsoft
description: Le tableau ci-dessous répertorie les bibliothèques de connectivité ou les pilotes que les applications clientes peuvent utiliser à partir d'une variété de langues pour se connecter et utiliser Microsoft SQL Server fonctionnant sur site ou dans le cloud, sous Linux, Windows ou Docker, ainsi qu'Azure SQL Database et Azure SQL Data Warehouse.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.openlocfilehash: 37b6714a11adc9a64b796830183ecc02101a4823
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396541"
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>Les bibliothèques de connectivité et des infrastructures pour Microsoft SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Consultez nos [Tutoriels de Démarrage](http://aka.ms/sqldev) pour démarrer rapidement avec des langages de programmation tels que C#, Java, Node. js, PHP et Python et de construire une application en utilisant SQL Server sur Linux ou Windows ou Docker sur MacOS.

Le tableau ci-dessous répertorie les bibliothèques de connectivité ou *pilotes* que les applications clientes peuvent utiliser à partir d’une variété de langages pour se connecter et utiliser Microsoft SQL Server en local ou dans le cloud, sous Linux, Windows ou Docker ainsi qu'avec SQL Azure Database et Azure SQL Data Warehouse. 

| Langue | Plateforme | Ressources supplémentaires | Télécharger | Découvrir |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Microsoft ADO.NET pour SQL Server](http://msdn.microsoft.com/library/mt657768.aspx) | [Télécharger](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [Bien démarrer](https://www.microsoft.com/en-us/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows, Linux, macOS | [Microsoft JDBC Driver pour SQL Server](http://msdn.microsoft.com/library/mt484311.aspx) | [Télécharger](http://go.microsoft.com/fwlink/?LinkId=245496) |  [Bien démarrer](https://www.microsoft.com/en-us/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows, Linux, macOS| [Pilote PHP SQL pour SQL Server](../connect/php/microsoft-php-driver-for-sql-server.md) | Système d'exploitation : <br/> \* [Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \* [Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \* [macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [Bien démarrer](https://www.microsoft.com/en-us/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows, Linux, macOS | [Node.js Driver for SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [Bien démarrer](https://www.microsoft.com/en-us/sql-server/developer-get-started/node/ubuntu)
| Python | Windows, Linux, macOS | [Pilote Python SQL](../connect/python/python-driver-for-sql-server.md) <br/> \* [pyodbc](http://msdn.microsoft.com/library/mt763257.aspx) |  [Bien démarrer](https://www.microsoft.com/en-us/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows, Linux, macOS | [Pilote Ruby pour SQL Server](../connect/ruby/ruby-driver-for-sql-server.md) | [Bien démarrer](https://www.microsoft.com/en-us/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows, Linux, macOS | [Pilote Microsoft ODBC pour SQL Server](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) | [Télécharger](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) |  

Le tableau ci-dessous énumère quelques exemples de frameworks ORM (Object Relational Mapping) et de frameworks web que les applications clientes peuvent utiliser avec Microsoft SQL Server fonctionnant sur site ou dans le cloud, sous Linux, Windows ou Docker et aussi avec Azure SQL Database et Azure SQL Data Warehouse. 

| Langue | Plateforme | ORM(s) |
| :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Entity Framework](https://docs.microsoft.com/ef)<br>[Entity Framework Core](https://docs.microsoft.com/ef/core/index) |
| Java | Windows, Linux, macOS |[Mise en veille prolongée ORM](http://hibernate.org/orm)|
| PHP | Windows, Linux | [Laravel (parlant)](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows, Linux, macOS | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | Windows, Linux, macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows, Linux, macOS | [Ruby on Rails](http://rubyonrails.org/) |

## <a name="related-links"></a>Liens connexes
- [Pilotes SQL Server](http://msdn.microsoft.com/library/mt654049.aspx) pour la connexion à partir d’applications clientes
