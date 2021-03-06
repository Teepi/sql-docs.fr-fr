---
title: Conversions effectuées à partir du Client au serveur | Microsoft Docs
description: Conversions effectuées de client à serveur
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB], client to server
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d4b68de60f6d1ffa345018478b5abc70ecf2839b
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39109821"
---
# <a name="conversions-performed-from-client-to-server"></a>Conversions de client à serveur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cet article décrit les conversions de date/heure effectuées entre une application cliente écrite avec OLE DB Driver pour SQL Server et [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (ou version ultérieure).  
  
## <a name="conversions"></a>Conversions  
 Cette rubrique décrit les conversions effectuées sur le client. Si le client spécifie la précision en fractions de seconde pour un paramètre qui diffère de celui défini sur le serveur, la conversion peut provoquer un échec dans les cas où le serveur autoriserait le succès de l'opération. En particulier, le client traite toute troncation des fractions de seconde comme une erreur, alors que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] arrondit les valeurs d’heure à la seconde entière la plus proche.  
  
 Si ICommandWithParameters::SetParameterInfo n’est pas appelée, les liaisons DBTYPE_DBTIMESTAMP sont converties comme s’ils étaient **datetime2**.  
  
|Vers -><br /><br /> From|DBDATE (date)|DBTIME (time)|DBTIME2 (time)|DBTIMESTAMP (smalldatetime)|DBTIMESTAMP (datetime)|DBTIMESTAMP (datetime2)|DBTIMESTAMPOFFSET (datetimeoffset)|STR|WSTR|SQLVARIANT<br /><br /> (sql_variant)|  
|----------------------|---------------------|---------------------|----------------------|-----------------------------------|------------------------------|-------------------------------|------------------------------------------|---------|----------|-------------------------------------|  
|DATE|1, 2|1, 3, 4|4, 12|1, 12|1, 12|1, 12|1, 5, 12|1, 12|1, 12|1, 12<br /><br /> datetime2(0)|  
|DBDATE|1|-|-|1, 6|1, 6|1, 6|1, 5, 6|1, 10|1, 10|1<br /><br /> Date|  
|DBTIME|-|1|1|1, 7|1, 7|1, 7|1, 5, 7|1, 10|1, 10|1<br /><br /> Time(0)|  
|DBTIME2|-|1, 3|1|1, 7, 10, 14|1, 7, 10, 15|1, 7, 10|1, 5, 7, 10|1, 10, 11|1, 10, 11|1<br /><br /> Time(7)|  
|DBTIMESTAMP|1, 2|1, 3, 4|1, 4, 10|1, 10, 14|1, 10, 15|1, 10|1, 5, 10|1, 10,11|1, 10, 11|1, 10<br /><br /> datetime2(7)|  
|DBTIMESTAMPOFFSET|1, 2, 8|1, 3, 4, 8|1, 4, 8, 10|1, 8, 10, 14|1, 8, 10, 15|1, 8, 10|1, 10|1, 10, 11|1, 10, 11|1, 10<br /><br /> datetimeoffset(7)|  
|FILETIME|1, 2|1, 3, 4|1, 4, 13|1, 13|1, 13|1, 13|1, 5, 13|1, 13|1, 10|1, 13<br /><br /> datetime2(3)|  
|BYTES|-|-|-|-|-|-|-|Néant|Néant|Néant|  
|VARIANT|1|1|1|1, 10|1, 10|1, 10|1, 10|Néant|Néant|1, 10|  
|SSVARIANT|1, 16|1, 16|1, 16|1, 10, 16|1, 10, 16|1, 10, 16|1, 10, 16|Néant|Néant|1, 16|  
|BSTR|1, 9|1, 9|1, 9, 10|1, 9, 10|1, 9, 10|1, 9, 10|1, 9, 10|Néant|Néant|Néant|  
|STR|1, 9|1, 9|1, 9, 10|1, 9, 10|1, 9, 10|1, 9, 10|1, 9, 10|Néant|Néant|Néant|  
|WSTR|1, 9|1, 9|1, 9, 10|1, 9, 10|1, 9, 10|1, 9, 10|1, 9, 10|Néant|Néant|Néant|  
  
## <a name="key-to-symbols"></a>Liste des symboles  
  
|Symbole|Signification|  
|------------|-------------|  
|-|Aucune conversion n'est prise en charge. Si la liaison est validée lorsque IAccessor::CreateAccessor est appelée, DBBINDSTATUS_UPSUPPORTEDCONVERSION est retourné dans *rgStatus*. Lorsque la validation pour l'accesseur est différée, DBSTATUS_E_BADACCESSOR est défini.|  
|Néant|Non applicable.|  
|1|Si les données fournies ne sont pas valides, DBSTATUS_E_CANTCONVERTVALUE est défini. Comme les données d'entrée sont validées avant que les conversions ne soient appliquées, même quand un composant est ignoré par une conversion suivante, il doit demeurer valide pour que la conversion réussisse.|  
|2|Les champs time (heure) sont ignorés.|  
|3|Les fractions de seconde doivent être égales à zéro ou DBSTATUS_E_DATAOVERFLOW est défini.|  
|4|Le composant date est ignoré.|  
|5|Le composant timezone est défini avec le paramètre timezone du client.|  
|6|L'heure est définie avec la valeur zéro.|  
|7|La date est définie avec la date en cours.|  
|8|L'heure est convertie en heure UTC. Si une erreur se produit pendant cette conversion, DBSTATUS_E_CANTCONVERTVALUE est défini.|  
|9|La chaîne est analysée comme littéral ISO et convertie dans le type cible. En cas d'échec, la chaîne est analysée comme littéral de date OLE (qui possède aussi des composants heure) et convertie d'une date OLE (DBTYPE_DATE) en type cible.<br /><br /> Si le type cible est DBTIMESTAMP, **smalldatetime**, **datetime**ou **datetime2**, la chaîne doit se conformer à la syntaxe pour la date, l'heure ou les littéraux **datetime2** , ou à la syntaxe reconnue par OLE. Si la chaîne est un littéral date, tous les composants heure sont définis avec la valeur zéro. Si la chaîne est un littéral heure, la date est définie avec la date en cours.<br /><br /> Pour tous les autres types cibles, la chaîne doit se conformer à la syntaxe des littéraux du type cible.|  
|10|S'il se produit une troncation des fractions de seconde avec perte de données, DBSTATUS_E_DATAOVERFLOW est défini. Pour les conversions de chaîne, le contrôle du dépassement de capacité n'est possible que lorsque la chaîne est conforme à la syntaxe ISO. Si la chaîne est un littéral date OLE, les fractions de seconde sont arrondies.<br /><br /> Pour la conversion de DBTIMESTAMP (datetime) en smalldatetime, le pilote OLE DB pour SQL Server tronque sans rien indiquer la valeur des secondes, au lieu de générer l’erreur DBSTATUS_E_DATAOVERFLOW.|  
|11|Le nombre de chiffres des fractions de seconde (l’échelle) est déterminé à partir de la taille de la colonne de destination, conformément au tableau ci-dessous. Pour les tailles de colonne supérieures à la plage du tableau, une échelle de 9 est nécessaire. Cette conversion accepte jusqu'à neuf chiffres de fractions de seconde, valeur maximale autorisée par OLE DB.<br /><br /> Cependant, si le type source est DBTIMESTAMP et que les fractions de seconde sont nulles, aucun chiffre de fraction de seconde ou virgule décimale n'est généré. Ce comportement garantit la compatibilité descendante pour les applications développées à l'aide de fournisseurs OLE DB plus anciens.<br /><br /> Une taille de colonne de ~0 implique une taille illimitée dans OLE DB (9 chiffres, à moins que la règle de 3 chiffres pour DBTIMESTAMP ne s'applique).|  
|12|La sémantique des conversions antérieures à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] pour DBTYPE_DATE est conservée. Les fractions de seconde sont tronquées à une longueur nulle.|  
|13|La sémantique des conversions antérieure à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] pour DBTYPE_FILETIME est conservée. Si vous utilisez l’API Windows FileTimeToSystemTime, la précision en fractions de seconde est limitée à 1 milliseconde.|  
|14|La sémantique des conversions antérieure à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] pour **smalldatetime** est conservée. Les secondes sont définies avec la valeur 0.|  
|15|La sémantique des conversions antérieure à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] pour **datetime** est conservée. Les secondes sont arrondies au 300ème de seconde le plus proche.|  
|16|Le comportement de conversion d'une valeur (d'un type donné) incorporée à un struct client SSVARIANT est identique à celui des mêmes valeur et type non incorporés à un struct client SSVARIANT.|  
  
||||  
|-|-|-|  
|Type|Longueur (en caractères)|Échelle|  
|DBTIME2|8, 10..18|0, 1..9|  
|DBTIMESTAMP|19, 21..29|0, 1..9|  
|DBTIMESTAMPOFFSET|26, 28..36|0, 1..9|  
  
## <a name="see-also"></a> Voir aussi  
 [Liaisons et conversions &#40;OLE DB&#41;](../../oledb/ole-db-date-time/conversions-ole-db.md)  
  
  
