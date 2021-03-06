---
title: À l’aide des Extensions Visual C++ | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ [ADO], using VC++ extensions
- ADO, Visual C++
ms.assetid: ff759185-df41-4507-8d12-0921894ffbd9
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 805abefbd6f934781b86060e98c73ab6ee8fd3c0
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982801"
---
# <a name="visual-c-extensions"></a>Extensions Visual C++
## <a name="the-iadorecordbinding-interface"></a>L’Interface IADORecordBinding
 Les Extensions Microsoft Visual C++ pour ADO associent, ou la liaison, les champs d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet à des variables C/C++. Chaque fois que la ligne actuelle de la limite **Recordset** change, tous les champs liés dans le **Recordset** sont copiés dans les variables C/C++. Si nécessaire, les données copiées sont converties au type de données déclaré de la variable C/C++.

 Le **BindToRecordset** méthode de la **IADORecordBinding** interface lie les champs à des variables C/C++. Le **AddNew** méthode ajoute une nouvelle ligne à la limite **Recordset**. Le **mise à jour** méthode renseigne les champs de nouvelles lignes de la **Recordset**, ou met à jour des champs dans les lignes existantes, avec la valeur des variables C/C++.

 Le **IADORecordBinding** interface est implémentée par le **Recordset** objet. Vous ne codez pas l’implémentation vous-même.

## <a name="binding-entries"></a>Entrées de liaison
 Les Extensions Visual C++ pour ADO mappent les champs d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet à des variables C/C++. La définition d’un mappage entre un champ et une variable est appelé un *liaison d’entrée*. Les macros fournissent des entrées de liaison pour les données numériques, de longueur fixe et de longueur variable. Les entrées de liaison et les variables C/C++ sont déclarées dans une classe dérivée de la classe d’Extensions Visual C++, **CADORecordBinding**. Le **CADORecordBinding** classe est définie en interne par les macros d’entrée de liaison.

 ADO mappe en interne les paramètres de ces macros à OLE DB **DBBINDING** structurer et crée un OLE DB **accesseur** objet pour gérer le déplacement et la conversion des données entre les champs et les variables. OLE DB définit les données comme composé de trois parties : un *tampon* où les données sont stockées ; un *état* qui indique si un champ a été stocké dans la mémoire tampon, ou comment la variable doit être restaurée à le champ ; et le *longueur* des données. (Consultez [l’obtention et définition des données (OLE DB)](http://msdn.microsoft.com/4369708b-c9fb-4d48-a321-bf949b41a369)dans la référence du programmeur OLE DB, pour plus d’informations.)

## <a name="header-file"></a>Fichier d’en-tête
 Inclure le fichier suivant dans votre application afin d’utiliser les Extensions Visual C++ pour ADO :

```
#include <icrsint.h>
```

## <a name="binding-recordset-fields"></a>Liaison des champs du Recordset

#### <a name="to-bind-recordset-fields-to-cc-variables"></a>Pour lier les champs du Recordset à des Variables C/C++

1.  Créer une classe dérivée de la **CADORecordBinding** classe.

2.  Spécifiez les entrées de liaison et les variables C/C++ correspondantes dans la classe dérivée. Les entrées de liaison entre **BEGIN_ADO_BINDING** et **END_ADO_BINDING** macros. N’interrompez pas les macros avec des virgules ou des points-virgules. Les délimiteurs appropriés sont automatiquement spécifiés par chaque macro.

     Spécifiez une entrée de liaison pour chaque champ à mapper à une variable C/C++. Utilisez un membre approprié de la **ADO_FIXED_LENGTH_ENTRY**, **ADO_NUMERIC_ENTRY**, ou **ADO_VARIABLE_LENGTH_ENTRY** famille de macros.

3.  Dans votre application, créez une instance de la classe dérivée de **CADORecordBinding**. Obtenir le **IADORecordBinding** de l’interface à partir de la **Recordset**. Appelez ensuite la **BindToRecordset** méthode à laquelle lier le **Recordset** champs aux variables C/C++.

 Pour plus d’informations, consultez le [exemple d’Extensions Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md).

## <a name="interface-methods"></a>Méthodes d'interface
 Le **IADORecordBinding** interface a trois méthodes : **BindToRecordset**, **AddNew**, et **mise à jour**. Le seul argument de chaque méthode est un pointeur vers une instance de la classe dérivée de **CADORecordBinding**. Par conséquent, le **AddNew** et **mise à jour** méthodes ne peuvent pas spécifier les paramètres de du même nom de la méthode ADO.

## <a name="syntax"></a>Syntaxe
 Le **BindToRecordset** méthode associe le **Recordset** champs avec des variables C/C++.

```
BindToRecordset(CADORecordBinding *binding)
```

 Le **AddNew** méthode appelle éponyme, ADO [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) (méthode), pour ajouter une nouvelle ligne à la **Recordset**.

```
AddNew(CADORecordBinding *binding)
```

 Le **mettre à jour** méthode appelle éponyme, ADO [mettre à jour](../../../ado/reference/ado-api/update-method.md) (méthode), pour mettre à jour le **Recordset**.

```
Update(CADORecordBinding *binding)
```

## <a name="binding-entry-macros"></a>Macros d’entrées de liaison
 Macros d’entrées de liaison définissent l’association entre un **Recordset** champ et une variable. Une macro de début et de fin délimitant le jeu d’entrées de liaison.

 Familles de macros sont fournies pour les données de longueur fixe, tel que **adDate** ou **adBoolean**; numérique des données, tel que **adTinyInt**, **sont également**, ou **adDouble**; et les données de longueur variable, tel que **adChar**, **adVarChar** ou **adVarBinary**. Tous les types numériques, à l’exception de **adVarNumeric**, sont également des types de longueur fixe. Chaque famille a différents jeux de paramètres afin que vous pouvez exclure les informations de liaison qui ne présente aucun intérêt.

 Pour plus d’informations, consultez [annexe a : Types de données](http://msdn.microsoft.com/e3a0533a-2196-4eb0-a31e-92fe9556ada6), de référence du programmeur OLE DB.

### <a name="begin-binding-entries"></a>Commencer les entrées de liaison
 **BEGIN_ADO_BINDING**(*classe*)

### <a name="fixed-length-data"></a>Données de longueur fixe
 **ADO_FIXED_LENGTH_ENTRY**(*Ordinal, type de données, mémoire tampon, état, modifier*)

 **ADO_FIXED_LENGTH_ENTRY2**(*Ordinal, type de données, mémoire tampon, modifier*)

### <a name="numeric-data"></a>Données numériques
 **ADO_NUMERIC_ENTRY**(*Ordinal, type de données, mémoire tampon, précision, échelle, état, modifier*)

 **ADO_NUMERIC_ENTRY2**(*Ordinal, type de données, mémoire tampon, précision, échelle, modifier*)

### <a name="variable-length-data"></a>Données de longueur variable
 **ADO_VARIABLE_LENGTH_ENTRY**(*Ordinal, type de données, mémoire tampon, taille, état, longueur, modifier*)

 **ADO_VARIABLE_LENGTH_ENTRY2**(*Ordinal, type de données, mémoire tampon, taille, état, modifier*)

 **ADO_VARIABLE_LENGTH_ENTRY3**(*Ordinal, type de données, mémoire tampon, taille, longueur, modifier*)

 **ADO_VARIABLE_LENGTH_ENTRY4**(*Ordinal, type de données, mémoire tampon, la taille, modifier*)

### <a name="end-binding-entries"></a>Fin d’entrées de liaison
 **END_ADO_BINDING**()

|Paramètre|Description|
|---------------|-----------------|
|*Classe*|Classe dans lequel les entrées de liaison et les variables de C/C++ sont définies.|
|*Ordinal*|Nombre ordinal, à partir d’un, de la **Recordset** champ correspondant à la variable C/C++.|
|*Type de données*|Type de données ADO équivalent de la variable C/C++ (consultez [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) pour obtenir la liste des types de données valides). La valeur de la **Recordset** champ sera converti en ce type de données si nécessaire.|
|*Mémoire tampon*|Nom de la variable C/C++ dans lequel le **Recordset** champ est stocké.|
|*Taille*|Taille maximale en octets de *tampon*. Si *tampon* contiendra une chaîne de longueur variable, prévoyez de l’espace pour un zéro de fin.|
|*État*|Nom d’une variable qui indique si le contenu de *tampon* sont valides et si la conversion du champ à *DataType* a réussi.<br /><br /> Les deux valeurs plus importantes de cette variable sont **adFldOK**, ce qui signifie que la conversion a réussi ; et **adFldNull**, ce qui signifie que la valeur du champ serait un VARIANT de type VT_NULL et pas simplement vide.<br /><br /> Les valeurs possibles pour *état* sont répertoriées dans le tableau suivant, « Valeurs d’état ».|
|*Modifier*|Indicateur booléen ; Si la valeur est TRUE, indique à ADO est autorisé à mettre à jour le correspondantes **Recordset** champ avec la valeur contenue dans *tampon*.<br /><br /> Définissez la valeur booléenne *modifier* paramètre TRUE pour permettre à ADO mettre à jour le champ lié, et FALSE si vous souhaitez examiner le champ sans le modifier.|
|*Précision*|Nombre de chiffres qui peuvent être représentés dans une variable numérique.|
|*Échelle*|Nombre de décimales dans une variable numérique.|
|*Longueur*|Nom d’une variable de quatre octets qui contient la longueur réelle des données dans *tampon*.|

## <a name="status-values"></a>Valeurs d'état
 La valeur de la *état* variable indique si un champ a été correctement copié dans une variable.

 Lors de la définition de données, *état* peut être défini sur **adFldNull** pour indiquer le **Recordset** champ doit être défini avec la valeur null.

|Constante|Valeur|Description|
|--------------|-----------|-----------------|
|**adFldOK**|0|Une valeur de champ non null a été retournée.|
|**adFldBadAccessor**| 1|Liaison n’était pas valide.|
|**adFldCantConvertValue**|2|Valeur n’a pas pu être convertie pour des raisons autres que l’authentification incompatibilité ou données de dépassement.|
|**adFldNull**|3|Lors de l’obtention d’un champ, indique une valeur null a été retournée.<br /><br /> Lorsque vous définissez un champ, indique le champ doit être défini sur **NULL** lorsque le champ ne peut pas encoder **NULL** lui-même (par exemple, un tableau de caractères ou un nombre entier).|
|**adFldTruncated**|4|Données de longueur variable ou des chiffres numériques ont été tronquées.|
|**adFldSignMismatch**|5|Valeur est signée et le type de données de variable n’est pas signé.|
|**adFldDataOverFlow**|6|Valeur est supérieure à pourraient être stockées dans le type de données de variable.|
|**adFldCantCreate**|7|Type de colonne inconnu et champ déjà ouvert.|
|**adFldUnavailable**|8|Valeur du champ n’a pas pu être déterminée, par exemple, sur un nouveau champ non assigné sans valeur par défaut.|
|**adFldPermissionDenied**|9|Lors de la mise à jour, aucune autorisation pour écrire des données.|
|**adFldIntegrityViolation**|10|Lors de la mise à jour, la valeur du champ enfreint l’intégrité de la colonne.|
|**adFldSchemaViolation**|11|Lors de la mise à jour, la valeur du champ violerait schéma de colonne.|
|**adFldBadStatus**|12|Lors de la mise à jour, paramètre d’état non valide.|
|**adFldDefault**|13|Lors de la mise à jour, la valeur par défaut a été utilisée.|

## <a name="see-also"></a>Voir aussi
 [Exemple d’Extensions Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md) [en-tête d’Extensions Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)
