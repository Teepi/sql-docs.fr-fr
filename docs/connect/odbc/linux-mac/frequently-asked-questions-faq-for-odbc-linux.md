---
title: Questions fréquentes (FAQ) pour ODBC Linux et macOS | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17d25f6084e136736dbc4c8a8ff3cb019ce4692e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37991371"
---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>Questions fréquentes (FAQ) pour ODBC Linux et macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Voici les réponses aux questions sur ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur Linux et macOS.
  
## <a name="frequently-asked-questions"></a>Forum Aux Questions (FAQ)

**Comment les applications ODBC existantes sur Linux ou macOS fonctionnent-elles avec le pilote ?**  
Vous devriez pouvoir compiler et exécuter les applications ODBC que vous avez compilées et exécutées sur Linux ou macOS à l’aide d’autres pilotes. 
  
**Quelles sont les fonctionnalités de [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] prises en charge par cette version du pilote ?**

Le pilote ODBC sur Linux et macOS prend en charge toutes les fonctionnalités de serveur dans [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] à l’exception de la base de données locale. Pour plus d’informations sur les fonctionnalités de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] prises en charge, consultez [Instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
**Le pilote prend-il en charge l’authentification Kerberos ?**  
Oui. Si vous avez une installation existante de l’environnement Kerberos, vous pourrez vous connecter aux serveurs à l’aide de la `Trusted_Connection=Yes` option de chaîne de connexion ou de la source de données. Pour plus d’informations, consultez [Utilisation de l’authentification intégrée](../../../connect/odbc/linux-mac/using-integrated-authentication.md).  
  
**Quel encodage Unicode une application doit-elle utiliser ?**  
UTF-8 pour les données SQL_CHAR et UTF-16 pour les données SQL_WCHAR.  

**Existe-t-il des exemples ODBC que je peux télécharger et exécuter avec le pilote pour le tester ou l’évaluer ?**

Pour obtenir un exemple, consultez la page [Use Existing MSDN C++ ODBC Samples for the ODBC Driver on Linux](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) . Cela concerne également le pilote ODBC de macOS. 

**Est le pilote ODBC sur Linux ou macOS en open source ?**

Non, les pilotes ODBC sur Linux et macOS ne sont pas un produit open source.  

## <a name="see-also"></a> Voir aussi
[Installation de Microsoft ODBC Driver for SQL Server sur Linux et macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
