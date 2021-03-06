---
title: Bien démarrer avec SQL Server 2017 sur Red Hat Enterprise Linux | Microsoft Docs
description: Ce démarrage rapide montre comment installer SQL Server 2017 sur Red Hat Enterprise Linux et ensuite créer et interroger une base de données avec sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: 4438184f6e14af1097ff05ea6e463f626025bb46
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103739"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>Démarrage rapide : Installer SQL Server et créer une base de données sur Red Hat

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dans ce guide de démarrage rapide, vous installez d’abord SQL Server 2017 sur Red Hat Enterprise Linux (RHEL) 7.3 +. Puis vous vous connectez avec **sqlcmd** pour créer votre première base de données et exécuter des requêtes.

> [!TIP]
> Ce didacticiel nécessite une saisie de la part de l’utilisateur et une connexion Internet. Si vous êtes intéressé par les procédures d'installation [sans assistance](sql-server-linux-setup.md#unattended) ou [hors connexion](sql-server-linux-setup.md#offline), consultez [aide à l’installation de SQL Server sur Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Prérequis

Vous devez avoir un RHEL 7.3 ou 7.4 machine avec **au moins 2 Go** de mémoire.

Pour installer Red Hat Enterprise Linux sur votre propre machine, accédez à [ http://access.redhat.com/products/red-hat-enterprise-linux/evaluation ](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation). Vous pouvez également créer des machines virtuelles RHEL dans Azure. Consultez [créer et gérer des machines virtuelles Linux avec Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm)et utiliser `--image RHEL` dans l’appel à `az vm create`.

Pour les autres exigences système, consultez [configuration système requise pour SQL Server sur Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installer SQL Server

Pour configurer SQL Server sur RHEL, exécutez les commandes suivantes dans un terminal pour installer le package **mssql-server** : 

> [!IMPORTANT]
> Si vous avez déjà installé une version CTP ou RC de SQL Server 2017, vous devez d’abord supprimer l’ancien référentiel avant d’inscrire un des référentiels de la disponibilité générale (GA). Pour plus d’informations, consultez [passer du référentiel de version préliminaire au référentiel de disponibilité générale](sql-server-linux-change-repo.md).

1. Téléchargez le fichier de configuration du référentiel de Microsoft SQL Server Red Hat :

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!NOTE]
   > Il s’agit du référentiel de mise à jour cumulative (CU). Pour plus d’informations sur les options de votre référentiel et leurs différences, consultez [modifier les référentiels sources](sql-server-linux-change-repo.md).

1. Exécutez les commandes suivantes pour installer SQL Server :

   ```bash
   sudo yum install -y mssql-server
   ```

1. Après la fin de l’installation du package, exécutez le programme d’installation **mssql-conf** et suivez les invites pour définir le mot de passe SA et choisir votre édition.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```
   > [!TIP]
   > Si vous testez SQL Server 2017 dans ce didacticiel, les éditions suivantes sont concédées librement sous licence : Evaluation, Developer et Express.

   > [!NOTE]
   > Veillez à spécifier un mot de passe fort pour le compte d’administrateur système (longueur minimale de 8 caractères, incluant des majuscules et des minuscules, des chiffres et/ou des caractères spéciaux).

1. Une fois la configuration terminée, vérifiez que le service est en cours d’exécution :

   ```bash
   systemctl status mssql-server
   ```
   
1. Pour autoriser les connexions à distance, ouvrez le port SQL Server sur le pare-feu sur RHEL. Le port de SQL Server par défaut est TCP 1433. Si vous utilisez **FirewallD** comme pare-feu, vous pouvez utiliser les commandes suivantes :

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

À ce stade, SQL Server est en cours d’exécution sur votre ordinateur RHEL et est prêt à être utilisé.

## <a id="tools"></a>Installer les outils de ligne de commande SQL Server

Pour créer une base de données, vous devez vous connecter avec un outil qui peut exécuter des instructions Transact-SQL sur le serveur SQL Server. Les étapes suivantes permettent d'installer les outils de ligne de commande de SQL Server : [sqlcmd](../tools/sqlcmd-utility.md) et [bcp](../tools/bcp-utility.md).

1. Téléchargez le fichier de configuration du référentiel Microsoft Red Hat.

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. Si vous aviez une version précédente de **mssql-tools** installée, supprimez tous les packages unixODBC plus anciens.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Exécutez les commandes suivantes pour installer **mssql-tools** avec le package développeur unixODBC.

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. Pour plus de commodité, ajoutez `/opt/mssql-tools/bin/` à votre variable d'environnement de **chemin d’accès**. Cela vous permet d’exécuter les outils sans spécifier le chemin d’accès complet. Exécutez les commandes suivantes pour modifier le **chemin d’accès** pour les sessions interactives avec et sans login :

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
