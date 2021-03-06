---
title: Installation de SSMA pour Client Oracle (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Licensing SSMA
ms.assetid: d5d4903d-e296-4bbf-8780-63674c4d62d5
caps.latest.revision: 19
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 95a763bf4f66e7a502d154dd56b5fab981f39306
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40394211"
---
# <a name="installing-ssma-for-oracle-client-oracletosql"></a>Installation du client SSMA pour le client Oracle (OracleToSQL)
Le client SSMA comprend les fichiers de programme qui effectuent les tâches suivantes :  
  
-   Connectez-vous à une base de données Oracle.  
  
-   Connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Convertir des objets de base de données Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe.  
  
-   Charger les objets dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Cette rubrique fournit les conditions préalables d’installation et les instructions d’installation de SSMA.  
  
## <a name="prerequisites"></a>Prérequis  
SSMA est conçu pour fonctionner avec Oracle 9 ou versions ultérieures et toutes les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Avant d’installer SSMA, assurez-vous que l’ordinateur remplit les conditions suivantes :  
  
-   Windows 7 ou versions ultérieures, ou Windows Server 2008 ou versions ultérieures.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 ou une version ultérieure.  
  
-   Le [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] version 4.0 ou une version ultérieure. Le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] version 4.0 est disponible sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support du produit. Vous pouvez également les obtenir à partir de la [centre de développement .NET Framework](http://go.microsoft.com/fwlink/?LinkId=48882).  
  
-   Client Oracle 9.0 ou une version ultérieure et la connectivité aux bases de données Oracle que vous souhaitez migrer. La version du client Oracle doit être la même version que, ou une version ultérieure à la version de base de données Oracle.  
  
    Vous pouvez installer le Client Oracle à partir du support du produit Oracle ou à partir du site Web d’Oracle. Pour plus d’informations sur la connectivité, consultez [connexion à la base de données Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
-   Accès à et autorisations suffisantes sur l’ordinateur qui héberge l’instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou base de données SQL Azure dans lequel vous effectuez la migration des objets de base de données et des données. Pour plus d’informations, consultez [connexion à SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).  
  
-   4 Go de RAM recommandé.  
  
## <a name="installing-the-ssma-for-oracle-client"></a>Installation de SSMA pour Oracle Client  
SSMA est téléchargeable sur le Web. Pour télécharger la dernière version, consultez le [page de téléchargement de l’Assistant Migration de SQL Server](http://aka.ms/ssmafororacle).  
  
Après avoir téléchargé la dernière version, vous devez extraire les fichiers d’installation avant que vous puissiez installer SSMA.  
  
**Pour installer le client SSMA**  
  
1.  Double-cliquez sur SSMA pour Oracle *n*. Install.exe, où *n* est le numéro de build.  
  
2.  Dans la page d’accueil, cliquez sur **suivant**.  
  
    Si vous n’avez pas les composants requis installés, un message s’affiche indiquant que vous devez tout d’abord installer les composants requis. Assurez-vous que vous avez installé tous les composants requis et puis exécutez à nouveau le programme d’installation.  
  
3.  Lisez le contrat de licence utilisateur final. Si vous acceptez, cochez **J’accepte les termes du contrat de licence**, puis cliquez sur **suivant**.  
  
4.  Dans la page Choisir un Type d’installation, cliquez sur **standard**.  
  
5.  Cliquez sur **Installer**.  
  
> [!IMPORTANT]  
> 1.  Veuillez désinstaller toutes les versions précédentes de SSMA pour Oracle avant d’installer la nouvelle version.  
  
L’emplacement d’installation par défaut est C:\Program Files\Microsoft SQL Server Migration Assistant pour Oracle.  
  
Outre les fichiers de programme SSMA, vous devez également installer SSMA pour le pack d’extension Oracle sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [installation des composants SSMA sur SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>Voir aussi  
[Installation des composants SSMA sur SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Bases de données de migration d’Oracle vers SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
