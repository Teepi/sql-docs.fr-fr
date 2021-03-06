---
title: Création d’un Assembly | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
caps.latest.revision: 26
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a7dcaae61cdfa6466f8f7194b4f93977ec2e7d97
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37353342"
---
# <a name="creating-an-assembly"></a>Création d'un assembly
  Les objets de base de données managés, tels que les procédures stockées ou les déclencheurs, sont successivement compilés et déployés dans des unités appelées « assemblys ». Les assemblys DLL managés doivent être enregistrés dans [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] avant de pouvoir utiliser la fonctionnalité fournie par l’assembly. Pour enregistrer un assembly dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , utilisez l'instruction CREATE ASSEMBLY. Cette rubrique explique comment enregistrer un assembly dans une base de données à l'aide de l'instruction CREATE ASSEMBLY, puis comment spécifier les paramètres de sécurité de l'assembly.  
  
## <a name="the-create-assembly-statement"></a>Instruction CREATE ASSEMBLY  
 L'instruction CREATE ASSEMBLY permet de créer un assembly dans une base de données. Par exemple :  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 La clause FROM spécifie le nom du chemin d'accès de l'assembly à créer. Ce chemin d'accès peut être soit un chemin UNC (Universal Naming Convention), soit le chemin d'accès d'un fichier physique stocké localement sur l'ordinateur.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n'autorise pas l'inscription de différentes versions d'un assembly avec le même nom, la même culture et la même clé publique.  
  
 Il est possible de créer des assemblys qui référencent d'autres assemblys. Lorsqu’un assembly est créé dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] crée également les assemblys référencés par l’assembly de niveau racine, si les assemblys référencés ne sont pas déjà créées dans la base de données.  
  
 Les utilisateurs ou les rôles d'utilisateurs de base de données se voient accorder des autorisations pour créer, et de ce fait acquérir, des assemblys dans une base de données. Pour être en mesure de créer des assemblys, l'utilisateur ou le rôle d'utilisateur de base de données doit bénéficier de l'autorisation CREATE ASSEMBLY.  
  
 Un assembly peut parvenir à référencer d'autres assemblys uniquement si :  
  
-   l'assembly appelé ou référencé est possédé par le même utilisateur ou rôle ;  
  
-   l'assembly appelé ou référencé a été créé dans la même base de données.  
  
## <a name="specifying-security-when-creating-assemblies"></a>Définition de la sécurité lors de la création d'assemblys  
 Lorsque vous créez un assembly dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vous pouvez spécifier un des trois niveaux différents de sécurité dans lesquels votre code peut être exécuté : `SAFE`, `EXTERNAL_ACCESS` ou `UNSAFE`. Au moment de l'exécution de l'instruction `CREATE ASSEMBLY`, l'assembly de code est soumis à certains contrôles qui peuvent entraîner l'échec de l'enregistrement de l'assembly sur le serveur. Pour plus d'informations, consultez l'exemple d'emprunt d'identité sur [CodePlex](http://msftengprodsamples.codeplex.com/).  
  
 `SAFE` est le jeu d'autorisations par défaut et fonctionne pour la majorité des scénarios. Pour spécifier un niveau de sécurité donné, vous devez modifier la syntaxe de l'instruction CREATE ASSEMBLY comme suit :  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 Il est également possible de créer un assembly à l'aide du jeu d'autorisations `SAFE` par simple omission de la troisième ligne de code ci-dessus :  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Lorsque le code dans un assembly s'exécute sous le jeu d'autorisations `SAFE`, tout calcul ou accès aux données sur le serveur ne peut avoir lieu que par l'entremise du fournisseur managé in-process.  
  
### <a name="creating-externalaccess-and-unsafe-assemblies"></a>Création d'assemblys EXTERNAL_ACCESS et UNSAFE  
 `EXTERNAL_ACCESS` propose des scénarios dans lesquels le code doit accéder à des ressources externes au serveur, tel que des fichiers, le réseau, le Registre et des variables d'environnement. Lorsque le serveur accède à une ressource externe, il emprunte l'identité du contexte de sécurité de l'utilisateur appelant le code managé.  
  
 L'autorisation de code `UNSAFE` convient dans des situations où la sécurité d'un assembly ne peut être vérifiée ou exige un accès supplémentaire à des ressources restreintes, telles que l'API Win32 [!INCLUDE[msCoName](../../../includes/msconame-md.md)].  
  
 Pour la création d'un assembly `EXTERNAL_ACCESS` ou `UNSAFE` dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'une des deux conditions suivantes doit être remplie :  
  
1.  L'assembly est signé avec un nom fort ou porte une signature Authenticode avec certificat. Ce nom fort (ou certificat) est créé dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en tant que clé asymétrique (ou certificat) et dispose d'une connexion correspondante avec l'autorisation `EXTERNAL ACCESS ASSEMBLY` (pour les assemblys à accès externe) ou l'autorisation `UNSAFE ASSEMBLY` (pour les assemblys non sécurisés).  
  
2.  Le propriétaire de la base de données (DBO) a `EXTERNAL ACCESS ASSEMBLY` (pour `EXTERNAL ACCESS` assemblys) ou `UNSAFE ASSEMBLY` (pour `UNSAFE` assemblys) autorisation et la base de données a la [TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) défini sur `ON`.  
  
 Les deux conditions mentionnées ci-dessus sont également vérifiées au moment du chargement de l'assembly (exécution incluse). Une des conditions doit au minimum être satisfaite pour le chargement de l'assembly.  
  
 Nous vous recommandons le [TRUSTWORTHY Database Property](../../security/trustworthy-database-property.md) sur une base de données ne pas définir `ON` uniquement pour exécuter le common language runtime (CLR) de code dans le processus serveur. Il est préférable, à la place, de créer une clé asymétrique à partir du fichier d'assembly dans la base de données master. Une connexion mappée à cette clé asymétrique doit ensuite être créée. Cette connexion doit disposer de l'autorisation `EXTERNAL ACCESS ASSEMBLY` ou `UNSAFE ASSEMBLY`.  
  
 Ce qui suit [!INCLUDE[tsql](../../../includes/tsql-md.md)] instructions avant d’exécuter l’instruction CREATE ASSEMBLY.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  Vous devez créer une connexion à associer à la clé asymétrique. Cette connexion permet uniquement d'accorder des autorisations ; elle ne doit pas être associée à un utilisateur ni utilisée dans l'application.  
  
 Pour créer un assembly `EXTERNAL ACCESS`, la personne chargée de le créer doit posséder l'autorisation `EXTERNAL ACCESS`. Elle est spécifiée au moment de créer l'assembly :  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 Ce qui suit [!INCLUDE[tsql](../../../includes/tsql-md.md)] instructions avant d’exécuter l’instruction CREATE ASSEMBLY.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 Pour préciser qu'un assembly est chargé avec l'autorisation `UNSAFE`, vous devez spécifier l'autorisation `UNSAFE` définie lors du chargement de l'assembly sur le serveur :  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 Pour obtenir des informations détaillées sur les autorisations pour chacun de ces paramètres, consultez [CLR Integration Security](../security/clr-integration-security.md).  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des assemblys d’intégration du CLR](managing-clr-integration-assemblies.md)   
 [Modification d’un Assembly](altering-an-assembly.md)   
 [Suppression d’un Assembly](dropping-an-assembly.md)   
 [Sécurité d’accès du Code CLR Integration](../security/clr-integration-code-access-security.md)   
 [Propriété de base de données TRUSTWORTHY](../../security/trustworthy-database-property.md)   
 [Autorisation d’appelants partiellement approuvés](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
  
  
