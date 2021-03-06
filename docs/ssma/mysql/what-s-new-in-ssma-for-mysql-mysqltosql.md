---
title: Quelles sont les nouveautés de SSMA pour MySQL (MySQLToSql) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 08/14/2018
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 1451a0b0-6713-4d0c-954f-ea3d8fce1d31
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ad86fed5cfa7eab443ce214cb7cc0965fd7062b8
ms.sourcegitcommit: e2a19dfac1b581237ef694071fbace4768bb6bf4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40393416"
---
# <a name="whats-new-in-ssma-for-mysql-mysqltosql"></a>Nouveautés de SSMA pour MySQL (MySQLToSql)
Cet article répertorie SSMA pour MySQL des modifications dans chaque version. 

## <a name="ssma-v79"></a>SSMA v7.9
La version v7.9 de SSMA pour MySQL contient les modifications suivantes :
- Correctifs ciblés visant qui améliorent la qualité et conversion des mesures.
- Prise en charge partielle pour la migration de types de données spatiales à partir de MySQL vers Azure SQL Database.
- Prend en charge dans la ligne de commande SSMA pour modifier le mappage de Type de données et les préférences du projet.
- Prise en charge pour la migration de données à l’aide de SQL Server Integration Services (SSIS). Après avoir converti le schéma, il est possible de créer un package SSIS à l’aide d’une option de menu contextuel.
- La boîte de dialogue de connexion de base de données SQL Azure dans SSMA a également été modifié pour spécifier le nom complet du serveur. Dans les versions précédentes de SSMA, le préfixe de la base de données SQL Azure devait être mentionnée explicitement à l’intérieur des paramètres des projets.

> [!IMPORTANT]
> Avec SSMA v7.4 et versions ultérieures, .net 4.5.2 est un préalable de l’installation.

## <a name="ssma-v78"></a>SSMA v7.8
La version v7.8 de SSMA pour MySQL contient les modifications suivantes :
- Mappage du type de modifications mises en évidence dans les paramètres du projet.
- Fourni à la capacité des utilisateurs à désactiver la télémétrie.

> [!IMPORTANT]
> Avec SSMA v7.4 et versions ultérieures, .net 4.5.2 est un préalable de l’installation.

## <a name="ssma-v77"></a>SSMA v7.7
La version v7.7 de SSMA pour MySQL contient les modifications suivantes :
- SSMA pour MySQL a été amélioré avec des correctifs ciblés qui améliorent les métriques de qualité et de conversion.
- Selon l’à la demande générale, la version 32 bits de SSMA pour MySQL est de retour. Par rapport à l’implémentation précédente (avant v7.4), il existe deux packages de programme d’installation, mais ils ne peuvent pas être installés côte à côte. Par conséquent, vous devez choisir la version la plus appropriée en fonction des composants de connectivité que vous disposez. Il est toujours préférable d’utiliser la version 64 bits, si possible.
- SSMA pour MySQL a maintenant le mode de connexion de chaîne de connexion ODBC, ce qui vous permet d’utiliser des pilotes ODBC de fournisseurs tiers qui sont compatibles avec MySQL.

> [!IMPORTANT]
> Avec SSMA v7.4 et versions ultérieures, .net 4.5.2 est un préalable de l’installation.

## <a name="ssma-v76"></a>SSMA v7.6
La version v7.6 de SSMA pour MySQL a été améliorée avec des correctifs ciblés visant qui améliorent la qualité et conversion des mesures et prise en charge de SQL Server 2017 (version préliminaire publique). Prise en charge de SQL Server 2017 sur Windows et Linux en version préliminaire publique et ne doit pas être utilisé pour les migrations de production.

> [!IMPORTANT]
> Avec SSMA v7.4 et versions ultérieures, .net 4.5.2 est un préalable de l’installation et la version 32 bits de l’outil a été abandonnée.

## <a name="ssma-v75"></a>SSMA v7.5
La version v7.5 de SSMA pour MySQL a été améliorée avec plusieurs améliorations pour garantir une meilleure accessibilité des personnes handicapées.

> [!IMPORTANT]
> .NET 4.5.2 est requis pour l’installation de SSMA v7.5. En outre, à compter de v7.4, la version 32 bits de SSMA est en cours de retrait.

## <a name="ssma-v74"></a>SSMA v7.4
La version v7.4 de SSMA pour MySQL contient les modifications suivantes :
- Le **Query timeout** option est désormais disponible au cours de la découverte d’objets de schéma à la source et cible.
![option de délai d’attente de requête](../media/query-timeout_red.png)
- Les mesures de qualité et la conversion a été améliorée avec des correctifs ciblés, en fonction des commentaires des clients.

> [!IMPORTANT]
> .NET 4.5.2 est requis pour l’installation de SSMA v7.4. En outre, à compter de v7.4, la version 32 bits de SSMA est en cours de retrait. 

## <a name="ssma-v73"></a>SSMA v7.3
La version v7.3 de SSMA pour MySQL contient les modifications suivantes :
- Métrique de qualité et de conversion améliorée avec des correctifs ciblés en fonction des commentaires des clients.
- Infrastructure d’extensibilité SSMA exposé via les éléments suivants :
  - Fonctionnalité d’exportation à un projet SQL Server Data Tools (SSDT).
    -   Vous pouvez désormais exporter des scripts de schéma à partir de SSMA pour un projet SSDT. Vous pouvez utiliser les scripts de schéma pour apporter des modifications de schéma supplémentaires et de déployer votre base de données.
![Enregistrer en tant que commande de projet SSDT](../media/export-schema-scripts_red.png)
  - Bibliothèques qui peuvent être consommées par SSMA pour effectuer des conversions personnalisées.
    - Vous pouvez désormais construire le code qui peut gérer les conversions de syntaxe personnalisée et les conversions qui n’ont pas été précédemment gérées par SSMA.
      - Obtenir des instructions sur la construction d’un convertisseur personnalisé sont disponibles dans ce billet de blog, [fonctions de conversion d’extension Assistant Migration SQL Server](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      - Exemple de projet pour la conversion peut être le télécharger [billet de blog](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).

## <a name="ssma-v72"></a>SSMA v7.2
La version v7.2 de SSMA pour MySQL contient les modifications suivantes :
- Métrique de qualité et de conversion améliorée avec des correctifs ciblés en fonction des commentaires des clients.
- Améliorations de télémétrie pour fournir une meilleure points de données pour résoudre les problèmes des clients et d’améliorer le taux de conversion de SSMA.

## <a name="ssma-v71"></a>SSMA v7.1
La version v7.1 de SSMA pour Access contient les modifications suivantes :
- SQL Server 2017 sur Windows et Linux CTP1 est désormais une plateforme cible prise en charge pour la migration. Cette fonctionnalité est dans technical preview et permet le déplacement de schéma et les données aux serveurs de SQL Server cible.
- SSMA prend désormais en charge les mises à jour automatiques pour télécharger la dernière version de SSMA dès qu’il est disponible.
- Fichiers binaires installables SSMA sont maintenant fournies via fichiers de package Windows installer (.msi).

**Ressources**

[Extension des fonctionnalités de SQL Server Migration Assistant conversion](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[Évaluer et migrer des données à partir des plateformes de données non Microsoft pour SQL Server *(avec l’exemple d’Oracle)*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>Mai 2016  
La version de mai 2016 de SSMA pour MySQL contient les modifications suivantes :.

-  Prise en charge pour SQL Server 2016.
-  Analyseur améliorée et programme de résolution.
-  Supprimé la vérification du programme d’installation pour .net 2.0.
-  Dépendance Extension Pack mis à jour à partir de .net 3.5 vers .net 4.0.
-  Typemapping de BigInt fixe par défaut pour MySql.
-  Fixe « enregistrer le projet » et « ouvrir le projet » des commandes pour la Console SSMA.
-  Commande fixe « securepassword » pour la Console SSMA.
-  Correction de comptage des objets pour le chargement initial.
-  Objets de MsSql fixes le chargement.
-  Résolution de bogue dans les paramètres globaux.
 
## <a name="march-2016"></a>Mars 2016  
La version préliminaire de mars 2016 de SSMA pour MySQL contient les modifications suivantes :  
  
-  Prise en charge pour la migration vers SQL Server 2016. 
  
## <a name="january-2016"></a>Janvier 2016  
La version de maintenance de janvier 2016 de SSMA pour MySQL contient les modifications suivantes :  
  
-  Élément de Menu ajouté vue journal pour SSMA (RFC 5706203).  
-  Ajout de télémétrie.  
  
## <a name="july-2014"></a>Juillet 2014  
La version de juillet 2014 de SSMA pour MySQL contient les modifications suivantes :  
  
-  Conversion de code de base de données SQL Azure améliorée. 
-  Fonctionnalité du pack d’extension déplacé au schéma pour prendre en charge de la base de données SQL Azure.  
-  Améliorations des performances testé pour les bases de données avec plus de 10k objets.  
-  Améliorations de l’interface utilisateur pour la gestion avec un grand nombre d’objets.  
-  La mise en surbrillance de « connues » schémas LOB (afin qu’ils peuvent être ignorés dans la conversion).  
-  Améliorations de la vitesse de conversion.  
-  Afficher le nombre de l’objet dans l’interface utilisateur.  
-  Réduction de taille de rapport de plus de 25 %.  
-  Messages d’erreur améliorés pour les constructions non analysées.  
  
## <a name="april-2014"></a>Avril 2014  
La version de juillet 2011 de SSMA pour MySQL contient les modifications suivantes :  
  
-  Prise en charge ajoutée de MS SQL Server 2014.  
-  Bogues résolus concernant la conversion vers Azure  
-  Bogues résolus concernant les pages de rapport invisible dans Internet Explorer 10.  
  
## <a name="july-2011"></a>Juillet 2011  
La version de juillet 2011 de SSMA pour MySQL contient les modifications suivantes :  
  
-   Prise en charge pour la conversion de limite à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] décalage « Denali ».  
-   Amélioration signalement d’erreurs pendant la migration des données.  
  
## <a name="april-2011"></a>Avril 2011  
La version d’avril 2011 de SSMA pour MySQL contient les modifications suivantes :  
  
-   Seul installable de « SSMA pour MySQL », qui prend en charge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] « Denali » et SQL Azure.  
-   La possibilité de connecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] « Denali ».  
-   Moteur de migration améliorée des données côté client, prise en charge de la migration parallèle des données.  
-   Performances de migration de données améliorées avec Simple et en bloc connecté les modes de récupération.  
-   SSMA pour la version de la Console de MySQL prend en charge la compatibilité descendante. Vous pouvez ouvrir les projets créés par les versions antérieures à SSMA v5.0.  
-   SSMA pour MySQL v5.0 produit peut être installé côte à côte (SxS) avec les versions antérieures du produit de SSMA.  
  
## <a name="july-2010"></a>Juillet 2010  
La version de juillet 2010 de SSMA pour MySQL contient les fonctionnalités suivantes :  
  
1.  **Améliorations de l’Interface utilisateur :**  
  
    -   Onglet « Modes SQL » pour les objets de base de données MySQL  
    -   Onglet « Paramètres » pour les objets de base de données MySQL  
    -   Onglet « Données » pour les Tables de MySQL  
    -   Paramètres de projet mis à jour dans les Pages de la Migration et de Conversion  
    -   « Paramètres de Migration de données » au niveau Table  
  
2.  **Améliorations apportées à se connecter à MySQL et SQL Server :**  
  
    -   Connectivité SSL dans MySQL  
    -   Connectivité chiffrée dans SQL Server  
  
3.  **Améliorations apportées à l’Explorateur de métabase de MySQL :**  
  
    -   Chargement de tous les objets de base de données MySQL et leurs onglets respectifs.  
  
4.  **Améliorations apportées à la Conversion de l’objet :**  
  
    -   Conversion d’objets de la MySQL métabase – procédures, des fonctions, des vues, des déclencheurs et des instructions.  
    -   Prise en charge limitée des Types de données spatiales dans les Tables.  
    -   Option permettant de convertir des fonctions de MySQL pour les procédures stockées SQL Server  
    -   Option pour appliquer le mappage de Modes SQL et le jeu de caractères lors de la Conversion de l’objet  
  
5.  **Améliorations de la Migration des données :**  
  
    -   Prise en charge la Migration des données à l’aide côté serveur et côté Client des moteurs de Migration de données  
    -   Prise en charge pour la Migration de données spatiales  
    -   SQL personnalisé pour la Migration de données pour les Tables  
  
6.  **SSMA pour MySQL Console :**  
  
    -   Fonctionnalité de Console de support de SSMA pour MySQL  
    -   Prise en charge pour l’interface de niveau de Script  
  
## <a name="january-2010"></a>Janvier 2010  
La version de janvier 2010 de SSMA pour MySQL était la version initiale. Elle contenait les fonctionnalités suivantes :  
  
-   Prise en charge pour la migration vers les deux en local SQL Server et SQL Azure.  
  
-   **Instantané de la fonctionnalité :** migration de schéma et les données de Tables/index/contraintes MySQL.
