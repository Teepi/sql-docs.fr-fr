---
title: Exemple de données volumineuses de lecture | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6c986144-3854-4352-8331-e79eccbefc28
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a2dc9e6e5ce3baa3bdaa878c37bb47a77d02a54
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39451527"
---
# <a name="reading-large-data-sample"></a>Exemple de lecture de données volumineuses

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Cet exemple d’application du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] montre comment récupérer une valeur d’une grande colonne unique auprès d’une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], avec la méthode [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md).

Le fichier de code pour cet exemple est nommé ReadLargeData.java et se trouve à l’emplacement suivant :

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Spécifications

Pour exécuter cet exemple d’application, l’accès à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] est nécessaire. Définissez également le classpath de façon à inclure le fichier jar mssql-jdbc. Pour plus d’informations sur la façon de définir l’instruction classpath, consultez [à l’aide du pilote JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] fournit les fichiers bibliothèques de classes mssql-jdbc à utiliser en fonction des paramètres JRE (Java Runtime Environment) choisis. Pour plus d’informations sur le fichier JAR à choisir, consultez [configuration système requise pour le pilote JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a> Exemple

Dans l’exemple suivant, le code établit une connexion à la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Il crée ensuite des exemples de données et met à jour la table Production.Document en utilisant une requête paramétrable.

De plus, il montre comment obtenir le mode de mise en mémoire tampon adaptatif avec la méthode [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md). Notez qu'à partir de la version 2.0 du pilote JDBC, la propriété de connexion responseBuffering a la valeur « adaptive » par défaut.

Ensuite, en utilisant une instruction SQL avec l’objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), il exécute les instructions SQL et place les données qu’il retourne dans un objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).

Enfin, l’exemple de code boucle dans les lignes de données du jeu de résultats, et utilise la méthode [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md) pour accéder à certaines données.

[!code[JDBC#UsingAdaptiveBuffering1](../../../connect/jdbc/codesnippet/Java/reading-large-data-sample_1.java)]

## <a name="see-also"></a> Voir aussi

[Utilisation de données volumineuses](../../../connect/jdbc/code-samples/working-with-large-data.md)
