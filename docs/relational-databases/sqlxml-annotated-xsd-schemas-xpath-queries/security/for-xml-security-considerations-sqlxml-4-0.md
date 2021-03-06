---
title: POUR des considérations de sécurité XML (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- client-side XML formatting
- FOR XML clause, security
- server-side XML formatting
- AUTO mode
- security [SQLXML], FOR XML
ms.assetid: facba279-df93-475b-ad43-0043dc5bae03
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: b514e8cd796f0a351d368c7948bda5c035e77dc5
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561455"
---
# <a name="for-xml-security-considerations-sqlxml-40"></a>Considérations relatives à la sécurité de FOR XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Le mode AUTO de FOR XML génère une hiérarchie XML dans laquelle les noms d'éléments sont mappés aux noms de tables et les noms d'attributs sont mappés aux noms de colonnes. Les informations de colonne et de table de la base de données sont de ce fait exposées. Vous pouvez masquer les informations de la base de données lorsque vous utilisez le mode AUTO (mise en forme côté serveur) en spécifiant des alias de table et de colonne dans la requête. Ces alias sont retournés dans le document XML résultant comme noms d'éléments et noms d'attributs.  
  
 Par exemple, la requête suivante spécifie le mode AUTO. La mise en forme XML est par conséquent réalisée sur le serveur :  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 Dans le document XML résultant, les alias sont utilisés pour les noms d'éléments et les noms d'attributs :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <C F="Nancy" L="Fuller" />   
  <CE F="Andrew" L="Peacock" />   
  <C F="Janet" L="Leverling" />   
  ...  
</root>  
```  
  
 Lorsque vous utilisez le mode NESTED (mise en forme côté client), les alias sont retournés uniquement pour les attributs figurant dans le document XML résultant. Les noms des tables de base sont toujours retournés comme noms d'éléments. Par exemple, la requête suivante spécifie le mode NESTED.  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 Dans le document XML résultant, les noms des tables de base sont retournés comme noms d'éléments et les alias de tables ne sont pas utilisés :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Person.Contact F="Nancy" L="Fuller" />   
  <Person.Contact F="Andrew" L="Peacock" />   
  <Person.Contact F="Janet" L="Leverling" />   
       ...  
</root>  
```  
  
  
