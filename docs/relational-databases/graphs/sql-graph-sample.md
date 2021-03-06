---
title: Exemple de base de données SQL graphique | Microsoft Docs
description: Un exemple rapide qui vous aideront à bien démarrer avec les nouvelles syntaxes introduites dans la base de données de graphique SQL.
ms.date: 04/19/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: graphs
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, tsql reference
ms.assetid: ''
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: e1ac7e1d94dbe8c4f69493eb9e6d27d99a76831a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39538849"
---
# <a name="create-a-graph-database-and-run-some-pattern-matching-queries-using-t-sql"></a>Créer une base de données de graphique et exécuter certains critères spéciaux des requêtes à l’aide de T-SQL
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Cet exemple fournit un [!INCLUDE[tsql-md](../../includes/tsql-md.md)] script pour créer une base de données de graphique avec les nœuds et les bords, puis utiliser la nouvelle clause de correspondance pour faire correspondre des modèles et de parcourir le graphique. Cet exemple de script fonctionne sur les deux de base de données SQL Azure et [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)]  
 
## <a name="sample-schema"></a>Exemple de schéma  
Cet exemple crée un schéma de graphique, comme montré dans la Figure 1, pour un réseau social hypothétique qui a des nœuds de personnes, Restaurant et City. Ces nœuds sont connectés entre eux à l’aide de vos amis, j’aime, les bords LivesIn et trouvera dans. 

![personne-villes-restaurants-tables](../../relational-databases/graphs/media/person-cities-restaurants-tables.png "exemple de base de données de graphique Sql")  
Figure 1 : Exemple de schéma avec un restaurant, ville, nœuds de la personne et LivesIn, trouvera dans, les bords de mentions j’aime.


## <a name="sample-script"></a>Exemple de script
```
-- Create a graph demo database
CREATE DATABASE graphdemo;
go

USE  graphdemo;
go

-- Create NODE tables
CREATE TABLE Person (
  ID INTEGER PRIMARY KEY, 
  name VARCHAR(100)
) AS NODE;

CREATE TABLE Restaurant (
  ID INTEGER NOT NULL, 
  name VARCHAR(100), 
  city VARCHAR(100)
) AS NODE;

CREATE TABLE City (
  ID INTEGER PRIMARY KEY, 
  name VARCHAR(100), 
  stateName VARCHAR(100)
) AS NODE;

-- Create EDGE tables. 
CREATE TABLE likes (rating INTEGER) AS EDGE;
CREATE TABLE friendOf AS EDGE;
CREATE TABLE livesIn AS EDGE;
CREATE TABLE locatedIn AS EDGE;

-- Insert data into node tables. Inserting into a node table is same as inserting into a regular table
INSERT INTO Person VALUES (1,'John');
INSERT INTO Person VALUES (2,'Mary');
INSERT INTO Person VALUES (3,'Alice');
INSERT INTO Person VALUES (4,'Jacob');
INSERT INTO Person VALUES (5,'Julie');

INSERT INTO Restaurant VALUES (1,'Taco Dell','Bellevue');
INSERT INTO Restaurant VALUES (2,'Ginger and Spice','Seattle');
INSERT INTO Restaurant VALUES (3,'Noodle Land', 'Redmond');

INSERT INTO City VALUES (1,'Bellevue','wa');
INSERT INTO City VALUES (2,'Seattle','wa');
INSERT INTO City VALUES (3,'Redmond','wa');

-- Insert into edge table. While inserting into an edge table, 
-- you need to provide the $node_id from $from_id and $to_id columns.
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 1), 
       (SELECT $node_id FROM Restaurant WHERE id = 1),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 2), 
      (SELECT $node_id FROM Restaurant WHERE id = 2),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 3), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 4), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);
INSERT INTO likes VALUES ((SELECT $node_id FROM Person WHERE id = 5), 
      (SELECT $node_id FROM Restaurant WHERE id = 3),9);

INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 1),
      (SELECT $node_id FROM City WHERE id = 1));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 2),
      (SELECT $node_id FROM City WHERE id = 2));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 3),
      (SELECT $node_id FROM City WHERE id = 3));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 4),
      (SELECT $node_id FROM City WHERE id = 3));
INSERT INTO livesIn VALUES ((SELECT $node_id FROM Person WHERE id = 5),
      (SELECT $node_id FROM City WHERE id = 1));

INSERT INTO locatedIn VALUES ((SELECT $node_id FROM Restaurant WHERE id = 1),
      (SELECT $node_id FROM City WHERE id =1));
INSERT INTO locatedIn VALUES ((SELECT $node_id FROM Restaurant WHERE id = 2),
      (SELECT $node_id FROM City WHERE id =2));
INSERT INTO locatedIn VALUES ((SELECT $node_id FROM Restaurant WHERE id = 3),
      (SELECT $node_id FROM City WHERE id =3));

-- Insert data into the friendof edge.
INSERT INTO friendof VALUES ((SELECT $NODE_ID FROM person WHERE ID = 1), (SELECT $NODE_ID FROM person WHERE ID = 2));
INSERT INTO friendof VALUES ((SELECT $NODE_ID FROM person WHERE ID = 2), (SELECT $NODE_ID FROM person WHERE ID = 3));
INSERT INTO friendof VALUES ((SELECT $NODE_ID FROM person WHERE ID = 3), (SELECT $NODE_ID FROM person WHERE ID = 1));
INSERT INTO friendof VALUES ((SELECT $NODE_ID FROM person WHERE ID = 4), (SELECT $NODE_ID FROM person WHERE ID = 2));
INSERT INTO friendof VALUES ((SELECT $NODE_ID FROM person WHERE ID = 5), (SELECT $NODE_ID FROM person WHERE ID = 4));


-- Find Restaurants that John likes
SELECT Restaurant.name
FROM Person, likes, Restaurant
WHERE MATCH (Person-(likes)->Restaurant)
AND Person.name = 'John';

-- Find Restaurants that John's friends like
SELECT Restaurant.name 
FROM Person person1, Person person2, likes, friendOf, Restaurant
WHERE MATCH(person1-(friendOf)->person2-(likes)->Restaurant)
AND person1.name='John';

-- Find people who like a restaurant in the same city they live in
SELECT Person.name
FROM Person, likes, Restaurant, livesIn, City, locatedIn
WHERE MATCH (Person-(likes)->Restaurant-(locatedIn)->City AND Person-(livesIn)->City);

```

## <a name="clean-up"></a>Nettoyer  
Nettoyer le schéma et la base de données créée pour l’exemple.
```
USE graphdemo;
go

DROP TABLE IF EXISTS likes;
DROP TABLE IF EXISTS Person;
DROP TABLE IF EXISTS Restaurant;
DROP TABLE IF EXISTS City;
DROP TABLE IF EXISTS friendOf;
DROP TABLE IF EXISTS livesIn;
DROP TABLE IF EXISTS locatedIn;

USE master;
go
DROP DATABASE graphdemo;
go


```

## <a name="script-explanation"></a>Explication du script  
Ce script utilise la nouvelle syntaxe T-SQL pour créer des tables de nœuds et d’arêtes. Montre comment insérer des données dans les tables de nœuds et edge à l’aide de `INSERT` instruction et montre également comment utiliser `MATCH` clause pour la navigation et de critères spéciaux.

|Command    |Remarques
|---  |---  |
|[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-sql-graph.md)  |Créer la table de nœuds ou d’arêtes de graphe  |
|[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-sql-graph.md)  |Insérer dans une table de nœuds ou d’arêtes  |
|[CORRESPONDANCE &#40;Transact-SQL&#41;](../../t-sql/queries/match-sql-graph.md)  |Utiliser la correspondance pour faire correspondre un modèle ou de parcourir le graphique  |
