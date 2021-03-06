---
title: Paramètres (Type de mappage) du projet (MySQLToSQL) | Documents Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 136fdf6d-657f-447b-af41-49bbc6e0e93e
caps.latest.revision: 13
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9bf1d1c219b8673345d5f2074fe8885b5c58223f
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34776765"
---
# <a name="project-settings-type-mapping-mysqltosql"></a>Paramètres (Type de mappage) du projet (MySQLToSQL)
Les paramètres de mappage de Type de projet vous permettent de définir des mappages de type par défaut pour le projet SSMA.  

Mappage de type est disponible dans les boîtes de dialogue Paramètres du projet et les paramètres de projet par défaut :  
  
-   Utilisez la boîte de dialogue Paramètres du projet pour définir les options de configuration pour le projet actuel. Pour accéder aux paramètres de mappage de type, dans le menu Outils, sélectionnez les paramètres du projet, puis cliquez sur le mappage de Type dans le volet gauche.  
  
-   Utilisez la boîte de dialogue Paramètres du projet par défaut pour définir les options de configuration pour tous les projets. Pour accéder au mappage des types de paramètres, dans le menu Outils, sélectionnez Paramètres par défaut d’un projet, type de projet de migration select pour lequel les paramètres sont requis pour être affichés / a été remplacée par **Version cible de la Migration** liste déroulante et puis cliquez sur le mappage de Type dans le volet gauche.  
  
## <a name="options"></a>Options  
  
##### <a name="source-type"></a>Type de source  
Il est le type de données MySQL, qui doit être mappée vers le type de données de base de données cible.  
  
##### <a name="target-type"></a>Type de cible  
Type de la base de données cible pour le type de données MySQL spécifié.  
  
##### <a name="add"></a>Ajouter  
Cliquez pour ajouter un type de données à la liste de mappage.  
  
##### <a name="edit"></a>Modifier  
Cliquez pour modifier le type de données sélectionné dans la liste de mappage.  
  
##### <a name="remove"></a>Supprimer  
Cliquez pour supprimer le mappage de type de données sélectionnées à partir de la liste de mappage.  
  
##### <a name="reset-to-default"></a>Rétablir les valeurs par défaut  
Cliquez pour réinitialiser la liste de mappage de type pour les valeurs par défaut SSMA.  
  
## <a name="type-mappings"></a>Mappages de types  
Le tableau suivant présente le mappage par défaut entre les types de données source et cible  
  
|||  
|-|-|  
|**Type de données MySQL**|**Type de données SQL Server**|  
|BIGINT|BIGINT|  
|bigint [*.. 255]|BIGINT|  
|binary|binaire [1]|  
|binaire [valeur 0.. 1]|binaire [1]|  
|binaire [2..255]|binaire [*]|  
|bit|binaire [1]|  
|bits [0..8]|binaire [1]|  
|bits [17..24]|binaire [3]|  
|bits [25..32]|binaire [4]|  
|bits [33..40]|binaire [5]|  
|bits [41..48]|binaire [6]|  
|bits [49..56]|binaire [7]|  
|bits [57..64]|binaire [8]|  
|bits [9..16]|binaire [2]|  
|objet BLOB|varbinary(max)|  
|objet BLOB de [valeur 0.. 1]|varbinary [1]|  
|objet BLOB [2..8000]|varbinary [*]|  
|objet BLOB [8001.. *]|varbinary(max)|  
|bool|bit|  
|boolean|bit|  
|char|NCHAR [1]|  
|octets de char|binaire [1]|  
|octets de char [valeur 0.. 1]|binaire [1]|  
|octets de char [2..255]|binaire [*]|  
|Char [valeur 0.. 1]|NCHAR [1]|  
|Char [2..255]|NCHAR [*]|  
|caractère|NCHAR [1]|  
|caractère variable la [valeur 0.. 1]|nvarchar [1]|  
|caractère variable [2..255]|NVARCHAR|  
|caractère [valeur 0.. 1]|NCHAR [1]|  
|caractère [2..255]|NCHAR [*]|  
|Date|Date|  
|DATETIME|datetime2[0]|  
|dec|Décimal|  
|DEC [*.. 65]|Decimal [*] [0]|  
|DEC [*.. 65][\*.. 30]|Decimal [*] [\*]|  
|Décimal|Décimal|  
|Decimal [*.. 65]|Decimal [*] [0]|  
|Decimal [*.. 65][\*.. 30]|Decimal [*] [\*]|  
|double|float [53]|  
|double précision|float [53]|  
|double précision [*.. 255][\*.. 30]|numérique [*] [\*]|  
|double [*.. 255][\*.. 30]|numérique [*] [\*]|  
|fixe|NUMERIC|  
|fixe [*.. 65][\*.. 30]|numérique [*] [\*]|  
|FLOAT|float [24]|  
|float [*.. 255][\*.. 30]|numérique [*] [\*]|  
|float [*.. 53]|float [53]|  
|INT|INT|  
|int [*.. 255]|INT|  
|entier|INT|  
|entier [*.. 255]|INT|  
|longblob|varbinary(max)|  
|LONGTEXT|nvarchar(max)|  
|mediumblob|varbinary(max)|  
|mediumint|INT|  
|mediumint [*.. 255]|INT|  
|mediumtext|nvarchar(max)|  
|national char|NCHAR [1]|  
|national char [valeur 0.. 1]|NCHAR [1]|  
|national char [2..255]|NCHAR [*]|  
|caractères nationaux|NCHAR [1]|  
|variable de caractères nationaux|nvarchar [1]|  
|caractères nationaux faisant varier la [valeur 0.. 1]|nvarchar [1]|  
|caractères nationaux varying [2..4000]|nvarchar [*]|  
|variable de caractères nationaux [4001.. *]|nvarchar(max)|  
|caractères nationaux [valeur 0.. 1]|NCHAR [1]|  
|caractères nationaux [2..255]|NCHAR [*]|  
|national varchar|nvarchar [1]|  
|varchar national [valeur 0.. 1]|nvarchar [1]|  
|national varchar [2..4000]|nvarchar [*]|  
|national varchar [4001.. *]|nvarchar(max)|  
|NCHAR|NCHAR [1]|  
|NCHAR varchar|nvarchar [1]|  
|NCHAR, varchar [valeur 0.. 1]|nvarchar [1]|  
|NCHAR, varchar [2..4000]|nvarchar [*]|  
|NCHAR varchar [4001.. *]|nvarchar(max)|  
|NCHAR [valeur 0.. 1]|NCHAR [1]|  
|NCHAR [2..255]|NCHAR [*]|  
|NUMERIC|NUMERIC|  
|numérique [*.. 65]|numérique [*] [0]|  
|numérique [*.. 65][\*.. 30]|numérique [*] [\*]|  
|NVARCHAR|nvarchar [1]|  
|nvarchar [valeur 0.. 1]|nvarchar [1]|  
|nvarchar [2..4000]|nvarchar [*]|  
|nvarchar [4001.. *]|nvarchar(max)|  
|REAL|float [53]|  
|Real [*.. 255][\*.. 30]|numérique [*] [\*]|  
|Série|BIGINT|  
|SMALLINT|SMALLINT|  
|smallint [*.. 255]|SMALLINT|  
|texte|nvarchar(max)|  
|texte de [valeur 0.. 1]|nvarchar [1]|  
|texte [2..4000]|nvarchar [*]|  
|texte [4001.. *]|nvarchar(max)|  
|time|time|  
|TIMESTAMP|DATETIME|  
|tinyblob|varbinary [255]|  
|TINYINT|SMALLINT|  
|tinyint [*.. 255]|SMALLINT|  
|tinytext|nvarchar [255]|  
|bigint non signé|BIGINT|  
|bigint non signé [*.. 255]|BIGINT|  
|dec non signé|Décimal|  
|non signé dec [*.. 65]|Decimal [*] [0]|  
|non signé dec [*.. 65][\*.. 30]|Decimal [*] [\*]|  
|décimal non signé|Décimal|  
|décimal non signé [*.. 65]|Decimal [*] [0]|  
|décimal non signé [*.. 65][\*.. 30]|Decimal [*] [\*]|  
|double non signé|float [53]|  
|non signée double précision|float [53]|  
|non signé double précision [*.. 255][\*.. 30]|numérique [*] [\*]|  
|non signé double [*.. 255][\*.. 30]|numérique [*] [\*]|  
|non signé fixe|NUMERIC|  
|non signé fixe [*.. 65][\*.. 30]|numérique [*] [\*]|  
|float non signé|float [24]|  
|non signé float [*.. 255][\*.. 30]|numérique [*] [\*]|  
|non signé float [*.. 53]|float [53]|  
|nombre entier non signé|BIGINT|  
|entier [*.. 255]|BIGINT|  
|entier non signé|BIGINT|  
|entier non signé [*.. 255]|BIGINT|  
|mediumint non signé|INT|  
|non signé mediumint [*.. 255]|INT|  
|numérique non signé|NUMERIC|  
|non signé numérique [*.. 65]|numérique [*] [0]|  
|non signé numérique [*.. 65][\*.. 30]|numérique [*] [\*]|  
|non signé réel|float [53]|  
|non signé réel [*.. 255[[\*.. 30]|numérique [*] [\*]|  
|smallint non signé|INT|  
|smallint non signé [*.. 255]|INT|  
|tinyint non signé|TINYINT|  
|tinyint non signée [*.. 255]|TINYINT|  
|varbinary [valeur 0.. 1]|varbinary [1]|  
|varbinary [2..8000]|varbinary [*]|  
|varbinary [8001.. *]|varbinary(max)|  
|varchar [valeur 0.. 1]|nvarchar [1]|  
|varchar [2..4000]|nvarchar [*]|  
|varchar [4001.. *]|nvarchar(max)|  
|year|SMALLINT|  
|année [2..2]|SMALLINT|  
|année [4..4]|SMALLINT|  
  
##### <a name="add"></a>Ajouter  
Cliquez pour ajouter un type de données à la liste de mappage.  
  
##### <a name="edit"></a>Modifier  
Cliquez pour modifier un type de données dans la liste de mappage.  
  
##### <a name="remove"></a>Supprimer  
Cliquez pour supprimer le mappage de type de données sélectionnées à partir de la liste de mappage.  
  
##### <a name="reset-to-default"></a>Rétablir les valeurs par défaut  
Cliquez pour réinitialiser tous les mappages de type de données pour les valeurs par défaut SSMA.  
  
