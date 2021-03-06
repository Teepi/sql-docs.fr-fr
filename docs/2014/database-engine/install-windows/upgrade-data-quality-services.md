---
title: Mettre à niveau Data Quality Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f396666b-7754-4efc-9507-0fd114cc32d5
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ecbf266c87e5aebe47f0f7af9c7a244c0e8dfb20
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171430"
---
# <a name="upgrade-data-quality-services"></a>Mettre à niveau Data Quality Services
  Cette rubrique fournit des informations sur la mise à niveau de votre installation existante de Data Quality Services (DQS) vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2. Dans le cadre de la mise à niveau de Data Quality Server dans DQS vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous devez également mettre à niveau le schéma de bases de données DQS.  
  
> [!IMPORTANT]  
>  -   Vous devez sauvegarder vos bases de données DQS avant de mettre à niveau DQS afin d'empêcher toute perte accidentelle de données lors de la mise à niveau du schéma. Pour plus d'informations sur la sauvegarde des bases de données DQS, consultez [Sauvegarde et restauration de bases de données DQS](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
> -   Connectez-vous à la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de Data Quality Server en utilisant la version actuelle ou une version antérieure de Data Quality Client ou la [transformation de nettoyage DQS](../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md) dans Integration Services pour effectuer les tâches de qualité des données.  
> -   Vous pouvez continuer à utiliser la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 du complément Master Data Services pour Excel après la mise à niveau de Data Quality Services et de Master Data Services vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2. Toutefois, aucune version antérieure du complément Master Data Services pour Excel ne fonctionnera après la mise à niveau vers SQL Server 2014 CTP2. Vous pouvez télécharger le [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] version SP1 de Master Data Services complément pour Excel à partir de [ici](http://go.microsoft.com/fwlink/?LinkId=328664).  
  
##  <a name="Prerequisites"></a> Conditions préalables  
  
-   Vous devez être connecté en tant que membre du groupe Administrateurs sur l'ordinateur [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
-   Votre compte d'utilisateur Windows doit être membre du rôle serveur fixe sysadmin dans l'instance de SQL Server où le [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] est installé.  
  
##  <a name="Upgrade"></a> Mise à niveau de DQS  
 Pour mettre à niveau DQS :  
  
1.  Sauvegardez vos bases de données DQS avant de lancer le processus de mise à niveau. Pour plus d'informations sur la sauvegarde des bases de données DQS, consultez [Backing Up and Restoring DQS Databases](../../data-quality-services/backing-up-and-restoring-dqs-databases.md).  
  
2.  Mettez à niveau l'instance SQL Server où DQS est installé vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    1.  Exécutez l'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
    2.  Dans le volet gauche, cliquez sur **Installation**.  
  
    3.  Dans le volet droit, cliquez sur **mise à niveau à partir de SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 ou SQL Server 2012**.  
  
    4.  Exécutez toutes les étapes de l'Assistant Installation.  
  
        > [!NOTE]  
        >  Votre instance de SQL Server sera mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et vous installerez la dernière version de Data Quality Client, si Data Quality Client était déjà installé sur cet ordinateur. Si Data Quality Client est installé sur d'autres ordinateurs, vous devez exécuter les sous-étapes de l'Étape 2 sur ces ordinateurs pour installer la version actuelle de Data Quality Client. L'Assistant Installation installe la version actuelle de Data Quality Client à côté de la version existante. Après la mise à niveau du schéma de bases de données DQS, connectez-vous à la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] de Data Quality Server en utilisant la version actuelle ou une version antérieure de Data Quality Client.  
  
3.  Mettez à niveau le schéma de bases de données DQS.  
  
    1.  Démarrez une invite de commandes d'administrateur.  
  
    2.  À l'invite de commandes, remplacez votre répertoire à l'emplacement où DQSInstaller.exe est disponible. Pour l'instance par défaut de SQL Server, le fichier DQSInstaller.exe est copié sous C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:  
  
        ```  
        cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
        ```  
  
    3.  À l'invite de commandes, tapez la commande suivante et appuyez sur Entrée :  
  
        ```  
        dqsinstaller.exe -upgrade  
        ```  
  
    4.  Le programme d'installation vous invite à sauvegarder les bases de données DQS avant de continuer. Si vous avez déjà sauvegardé vos bases de données DQS, tapez `Y` ou `Yes`, puis appuyez sur ENTRÉE pour poursuivre la mise à niveau.  
  
    5.  Un message d'achèvement s'affiche une fois la mise à niveau du schéma des bases de données DQS terminée.  
  
##  <a name="Verify"></a> Vérification de la mise à niveau du schéma des bases de données DQS  
 Pour vérifier que le schéma de bases de données DQS a été correctement mis à niveau, vérifiez la version actuelle dans les bases de données DQS_MAIN et DQS_PROJECTS en interrogeant la table A_DB_VERSION dans chaque base de données. Pour cela :  
  
1.  Démarrez SQL Server Management Studio et connectez-vous à l'instance de SQL Server qui contient les bases de données DQS mises à niveau.  
  
2.  Exécutez la requête suivante :  
  
    ```  
    SELECT * FROM DQS_MAIN.dbo.A_DB_VERSION WHERE STATUS=2;  
    SELECT * FROM DQS_PROJECTS.dbo.A_DB_VERSION WHERE STATUS=2;  
    ```  
  
3.  La sortie indiquera une entrée pour chaque mise à niveau, avec la date correspondante. Les valeurs VERSION_ID et ASSEMBLY_VERSION maximales de la dernière date correspondent à la version actuelle. Une valeur de 2 dans la colonne STATUS indique que l'opération a réussi. Si une erreur s'est produite, elle sera indiquée dans la colonne ERROR. Exemple de sortie :  
  
    |ID|UPGRADE_DATE|VERSION_ID|ASSEMBLY_VERSION|USER_NAME|STATUS|d’erreur|  
    |--------|-------------------|-----------------|-----------------------|----------------|------------|-----------|  
    |1000|2013-08-11 05:26:39.567|1200|11.0.3000.0|\<DOMAINE\nom d’utilisateur>|2||  
    |1001|2013-09-19 15:09:37.750|1600|12.0.xxxx.0|\<DOMAINE\nom d’utilisateur>|2||  
  
## <a name="see-also"></a>Voir aussi  
 [Installer Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [Supprimer des objets Data Quality Server](../../sql-server/install/remove-data-quality-server-objects.md)   
 [Mise à niveau vers SQL Server 2014](upgrade-sql-server.md)  
  
  
