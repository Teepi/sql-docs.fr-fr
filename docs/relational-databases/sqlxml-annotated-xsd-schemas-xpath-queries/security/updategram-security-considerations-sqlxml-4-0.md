---
title: Considérations de sécurité de mise à jour (SQLXML 4.0) | Microsoft Docs
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
- SQLXML, updategrams
- security [SQLXML], updategrams
- updategrams [SQLXML], security
ms.assetid: 00dc6cf4-a2e8-4cca-bdd6-d5122102a82d
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: d4efd0a03a5b7d7aa4b230a1b6c6d862fc20a372
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39533079"
---
# <a name="updategram-security-considerations-sqlxml-40"></a>Considérations de sécurité relatives au code de mise à jour (updategram) (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Vous trouverez ci-après des instructions de sécurité relatives à l'utilisation des codes de mise à jour :  
  
-   Évitez d'utiliser le mappage par défaut lorsque vous utilisez des codes de mise à jour pour mettre à jour des données. Lorsque vous utilisez le mappage par défaut, un nom d'élément dans un code de mise à jour mappe à un nom de table et un nom d'attribut mappe à une colonne. Cela expose les informations de colonnes et de tables dans la base de données, ce qui constitue un problème de sécurité potentiel. Au lieu de cela, si vous spécifiez un schéma de mappage séparé qui mappe les éléments et attributs dans un code de mise à jour aux tables et colonnes de base de données, vos noms d'attributs et d'éléments de code de mise à jour peuvent être arbitraires et le schéma effectue un mappage nécessaire de ces noms aux tables et colonnes de base de données. Ainsi, les informations sur la base de données ne sont pas exposées dans un code de mise à jour.  
  
-   N'autorisez pas les utilisateurs à créer et exécuter leurs codes de mise à jour. Il est recommandé de faire en sorte que les codes de mise à jour résident en tant que modèles sur un serveur, plutôt que les créer de manière dynamique dans des applications de type ASP, ce qui pourraient exposer les données de la base de données. Le fait d'autoriser les utilisateurs à accéder uniquement aux données par le biais des codes de mise à jour fournis en tant que modèles peut éliminer ce risque.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de codes de mise à jour pour modifier des données dans SQLXML 4.0](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
  
  
