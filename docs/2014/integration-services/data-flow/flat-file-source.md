---
title: Source de fichier plat | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Flat File
- text file reading [Integration Services]
- flat files
- Flat File source
ms.assetid: 4a64f7f3-f25d-4db0-93b3-a29496030e58
caps.latest.revision: 50
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 040069e373761d6d3ad78ea26bea5f8e538c33ae
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229359"
---
# <a name="flat-file-source"></a>Source de fichier plat
  La source de fichier plat lit des données figurant dans un fichier texte. Le fichier texte peut être d'un format délimité, à largeur fixe ou mixte.  
  
-   Le format délimité utilise des séparateurs de colonnes et de lignes pour définir les colonnes et les lignes.  
  
-   Le format de largeur fixe utilise la largeur pour définir les colonnes et les lignes. Ce format comprend également un caractère qui permet de remplir les champs dans la limite de leur largeur maximale.  
  
-   Le format non justifié à droite utilise la largeur pour définir toutes les colonnes, à l'exception de la dernière colonne, qui est délimitée par le séparateur de lignes.  
  
 Vous pouvez configurer la source de fichier plat comme suit :  
  
-   Ajoutez une colonne à la sortie de transformation qui contient le nom du fichier texte dont la source de fichier plat extrait les données.  
  
-   Spécifiez si la source de fichier plat interprète les chaînes nulles dans les colonnes en tant que valeurs NULL.  
  
    > [!NOTE]  
    >  Le gestionnaire de connexions de fichiers plats utilisé par la source de fichier plat doit être configuré de manière à utiliser un format délimité, afin qu'il puisse interpréter les chaînes de longueur nulle en tant que valeurs NULL. Si le gestionnaire de connexions utilise le format à largeur fixe ou non justifié à droite, les données composées d'espaces ne peuvent pas être interprétées comme des valeurs NULL.  
  
 Les colonnes de sortie dans la sortie de la source de fichier plat comportent la propriété FastParse. FastParse indique si la colonne utilise les routines d’analyse de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui sont rapides, mais ne tiennent pas compte des paramètres régionaux, ou les routines d’analyse standard qui tiennent compte des paramètres régionaux. Pour plus d'informations, consultez [Fast Parse](../fast-parse.md) et [Standard Parse](../standard-parse.md).  
  
 Les colonnes de sortie incluent également la propriété UseBinaryFormat. Cette propriété vous permet d'implémenter la prise en charge de données binaires, par exemple des données au format décimal compressé, dans des fichiers. Par défaut, UseBinaryFormat la valeur est définie `false`. Si vous souhaitez utiliser un format binaire, la valeur UseBinaryFormat `true` et le type de données sur la colonne de sortie `DT_BYTES`. De cette manière, la source de fichier plat ignore la conversion des données et passe les données telles quelles à la colonne de sortie. Vous pouvez ensuite utiliser une transformation, telle que la conversion de données ou de colonne dérivée pour convertir les données `DT_BYTES` en un type de données différent, ou vous pouvez écrire un script personnalisé dans une transformation de script pour interpréter les données. Vous pouvez également écrire un composant de flux de données personnalisé pour interpréter les données. Pour plus d’informations sur les données de types que vous pouvez effectuer un cast `DT_BYTES` pour voir [Cast &#40;SSIS Expression&#41;](../expressions/cast-ssis-expression.md).  
  
 Cette source utilise un gestionnaire de connexions de fichiers plats pour accéder au fichier texte. À l'aide des propriétés du gestionnaire de connexions de fichiers plats, vous pouvez indiquer des informations relatives au fichier et à chacune de ses colonnes, ainsi que définir la façon dont la source du fichier plat doit gérer les données figurant dans le fichier texte. Par exemple, vous pouvez spécifier les caractères qui séparent les colonnes et les lignes du fichier, ainsi que le type de données et la longueur de chaque colonne. Pour plus d'informations, consultez [Flat File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 Cette source comporte une sortie et une sortie d'erreur.  
  
## <a name="configuration-of-the-flat-file-source"></a>Configuration de la source de fichier plat  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de source de fichier plat**, cliquez sur l’une des rubriques suivantes :  
  
-   [Flat File Source Editor &#40;Page Gestionnaire de connexions&#41;](../flat-file-source-editor-connection-manager-page.md)  
  
-   [Flat File Source Editor &#40;Page colonnes&#41;](../flat-file-source-editor-columns-page.md)  
  
-   [Flat File Source Editor &#40;Page sortie d’erreur&#41;](../flat-file-source-editor-error-output-page.md)  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../common-properties.md)  
  
-   [Propriétés personnalisées des fichiers plats](flat-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Pour plus d’informations sur la définition des propriétés d’un composant de flux de données, consultez [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Destination de fichier plat](flat-file-destination.md)   
 [Flux de données](data-flow.md)  
  
  