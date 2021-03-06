---
title: Parse (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Parse
- Parse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Parse [Database Engine]
ms.assetid: b37e28b6-6e2e-470a-945b-ce5252da743a
caps.latest.revision: 17
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 00464f88444957c52d4671e143c6e3b425770ed6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052935"
---
# <a name="parse-database-engine"></a>Parse (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Parse convertit la représentation de chaîne canonique d’un **hierarchyid** en valeur **hierarchyid**. Parse est appelée implicitement quand une conversion d’un type chaîne en **hierarchyid** se produit. Agit comme l’opposé de [ToString](../../t-sql/data-types/tostring-database-engine.md). Parse() est une méthode statique.
  
## <a name="syntax"></a>Syntaxe  
  
```sql
-- Transact-SQL syntax  
hierarchyid::Parse ( input )  
-- This is functionally equivalent to the following syntax   
-- which implicitly calls Parse():  
CAST ( input AS hierarchyid )  
```  
  
```sql
-- CLR syntax  
static SqlHierarchyId Parse ( SqlString input )   
```  
  
## <a name="arguments"></a>Arguments  
*input*  
[!INCLUDE[tsql](../../includes/tsql-md.md)] : valeur du type de données character converti.
  
CLR : valeur de chaîne évaluée.
  
## <a name="return-types"></a>Types de retour  
**Type de retour SQL Server : hierarchyid**
  
**Type de retour CLR : SqlHierarchyId**
  
## <a name="remarks"></a>Notes   
Si Parse reçoit une valeur qui n’est pas une représentation de chaîne valide d’un **hierarchyid**, une exception est levée. Par exemple, si les types de données **char** contiennent des espaces de fin, une exception est levée.
  
## <a name="examples"></a>Exemples  
  
### <a name="a-converting-transact-sql-values-without-a-table"></a>A. Conversion de valeurs Transact-SQL sans table  
L’exemple de code suivant utilise `ToString` pour convertir une valeur **hierarchyid** en une chaîne et `Parse` pour convertir une valeur de chaîne en **hierarchyid**.
  
```sql
DECLARE @StringValue AS nvarchar(4000), @hierarchyidValue AS hierarchyid  
SET @StringValue = '/1/1/3/'  
SET @hierarchyidValue = 0x5ADE  
  
SELECT hierarchyid::Parse(@StringValue) AS hierarchyidRepresentation,  
@hierarchyidValue.ToString() AS StringRepresentation ;
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
hierarchyidRepresentation    StringRepresentation
-------------------------    -----------------------
0x5ADE                       /1/1/3/
```
  
### <a name="b-clr-example"></a>B. Exemple CLR  
L’extrait de code suivant appelle la méthode Parse() :
  
```sql
string input = “/1/2/”;  
SqlHierarchyId.Parse(input);  
```  
  
## <a name="see-also"></a>Voir aussi
[Référence de méthodes de type de données hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
