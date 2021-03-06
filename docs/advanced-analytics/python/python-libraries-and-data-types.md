---
title: Python bibliothèques et types de données dans SQL Server Machine Learning | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7b977d079589dbb4c54d5c31fec644d9f984dd61
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "40434849"
---
# <a name="python-libraries-and-data-types"></a>Bibliothèques et types de données Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article décrit les bibliothèques Python qui sont inclus avec SQL Server Machine Learning Services (en base de données) et les installations (autonome).

Cet article répertorie également les types de données non pris en charge, et répertorie les types de données qui peut être effectuée implicitement lorsque les données sont transmises entre Python et SQL Server.

## <a name="python-version"></a>Version de Python

Distribution de SQL Server 2017 Anaconda 4.2 et en Python 3.6.

Un sous-ensemble des fonctionnalités de RevoScaleR (rxLinMod, rxLogit, rxPredict, rxDTrees, rxBTrees, peut-être quelques autres) est fourni à l’aide des API Python, à l’aide d’un nouveau package Python **revoscalepy**. Vous pouvez utiliser ce package fonctionne avec les données à l’aide des trames de données Pandas, les fichiers XDF ou les requêtes de données SQL.

Pour plus d’informations, consultez [revoscalepy What ' s ?](what-is-revoscalepy.md).

## <a name="python-and-sql-data-types"></a>Python et les Types de données SQL

Python prend en charge un nombre limité de types de données par rapport à SQL Server.

Par conséquent, lorsque vous utilisez des données à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans les scripts Python, des données peuvent être converties implicitement en un type de données compatible. Toutefois, souvent une conversion exacte ne peut pas être effectuée automatiquement, et une erreur est retournée.

Ce tableau répertorie les conversions implicites qui sont fournies. Autres types de données ne sont pas pris en charge.

|SQLtype|Type de Python|
|-|-|
|**bigint**|`numeric`|
|**binaire**|`raw`|
|**bit**|`bool`|
|**char**|`str`|
|**float**|`float64`|
|**Int**|`int32`|
|**nchar**|`str`|
|**nvarchar**|`str`|
|**nvarchar(max)**|`str`|
|**real**|`float32`|
|**smallint**|`int16`|
|**tinyint**|`uint8`|
|**varbinary**|`bytes`|
|**varbinary(max)**|`bytes`|
|**varchar(n)**|`str`|
|**varchar(max)**|`str`|



