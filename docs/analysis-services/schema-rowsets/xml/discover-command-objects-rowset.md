---
title: Ensemble de lignes DISCOVER_COMMAND_OBJECTS | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_COMMAND_OBJECTS rowset
ms.assetid: 325114ee-3a50-4504-9782-dbf7c1a44778
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cae36b0ff5492555137952c2ad9b19f609c53948
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="discovercommandobjects-rowset"></a>Ensemble de lignes DISCOVER_COMMAND_OBJECTS
  Fournit des informations sur l'activité et l'utilisation des ressources des objets actuellement utilisés par la commande référencée.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_COMMAND_OBJECTS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Restriction| Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**SESSION_SPID**|**DBTYPE_I4**|Oui|ID de session.|  
|**ID DE SESSION**|**DBTYPE_WSTR**|Oui|Identificateur unique de session, tel qu'un GUID.|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||Numéro de séquence de la commande.|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**|Oui|Chemin d'accès au parent de l'objet actuel.|  
|**OBJECT_ID**|**DBTYPE_WSTR**|Oui|ID de l'objet tel que défini lors de sa création.|  
|**OBJECT_VERSION**|**DBTYPE_I4**||Numéro de version des métadonnées de l'objet ; ce nombre change chaque fois que l'objet est modifié.|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||Numéro de lignage des données contenues dans l'objet. Ce nombre est incrémenté chaque fois que l'objet est traité.|  
|**OBJECT_CPU_TIME_MS**|**DBTYPE_I8**||Temps processeur, en millisecondes, utilisé par l'objet depuis le début de la commande.|  
|**OBJECT_READ_KB**|**DBTYPE_I8**||Valeur cumulée, en kilo-octets, des lectures de données par l'objet depuis le début de la commande.|  
|**OBJECT_READS**|**DBTYPE_I8**||Nombre cumulé d'opérations de lecture par l'objet depuis le début de la commande.|  
|**OBJECT_WRITE_KB**|**DBTYPE_I8**||Valeur cumulée, en kilo-octets, des écritures de données par l'objet depuis le début de la commande.|  
|**OBJECT_WRITES**|**DBTYPE_I8**||Nombre cumulé d'opérations d'écriture par l'objet depuis le début de la commande.|  
|**OBJECT_ROWS_RETURNED**|**DBTYPE_I8**||Nombre de lignes retournées par l'objet à l'appelant depuis le début de la commande.|  
|**OBJECT_ROWS_SCANNED**|**DBTYPE_I8**||Nombre de lignes analysées par l'objet depuis le début de la commande.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
> [!IMPORTANT]  
>  L'ensemble de lignes de schéma DISCOVER_COMMAND_OBJECTS ne signale pas l'activité par le biais de requêtes DMV.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd35-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|CommandObjects|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  