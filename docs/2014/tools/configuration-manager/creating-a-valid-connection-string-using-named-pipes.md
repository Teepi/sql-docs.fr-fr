---
title: Création d’une chaîne de connexion valide à l’aide de canaux nommés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], named pipes
- pipes [SQL Server]
- pipes [SQL Server], connecting to
- aliases [SQL Server], named pipes
- Named Pipes [SQL Server], connection strings
ms.assetid: 90930ff2-143b-4651-8ae3-297103600e4f
caps.latest.revision: 30
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: b5cd4cc03a1b4254e26750b45704d67af62cef04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317439"
---
# <a name="creating-a-valid-connection-string-using-named-pipes"></a>Création d'une chaîne de connexion valide à l'aide de canaux nommés
  Sauf modification par l’utilisateur, lors de l’instance par défaut de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute sur le protocole canaux nommés, elle utilise `\\.\pipe\sql\query` comme nom de canal. Le point indique que l’ordinateur est l’ordinateur local, `pipe` indique que la connexion est un canal nommé, et `sql\query` est le nom du canal. Pour définir la connexion au canal par défaut, l'alias doit avoir `\\<computer_name>\pipe\sql\query` comme nom de canal. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été configuré de manière à être à l'écoute sur un autre canal, le nom de canal doit correspondre à ce canal. Par exemple, si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise `\\.\pipe\unit\app` comme étant le canal, l’alias doit utiliser `\\<computer_name>\pipe\unit\app` comme nom de canal.  
  
 Pour créer un nom de canal valide, vous devez procéder comme suit :  
  
-   Spécifiez un **nom de l'alias**.  
  
-   Sélectionnez **canaux nommés** en tant que le **protocole**.  
  
-   Entrez le **nom du canal**. Vous pouvez également laisser **nom du canal** vide et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager se termine le nom du canal approprié une fois que vous spécifiez la **protocole** et **Server**  
  
-   Spécifiez un **Server**. Pour une instance nommée, vous pouvez indiquer un nom de serveur et un nom d'instance.  
  
 Au moment de la connexion, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] composant Native Client lit le serveur, protocole et nom du canal de valeurs à partir du Registre pour le nom d’alias spécifié et crée un nom de canal au format `np:\\<computer_name>\pipe\<pipename>` ou `np:\\<IPAddress>\pipe\<pipename>`. Pour une instance nommée, le nom du canal par défaut est `\\<computer_name>\pipe\MSSQL$<instance_name>\sql\query`.  
  
> [!NOTE]  
>  Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] pare-feu de Windows ferme le port 445 par défaut. Étant donné que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] communique via le port 445, vous devez rouvrir ce port si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour écouter les connexions clientes entrantes utilisant des canaux nommés. Pour plus d'informations sur la configuration d'un pare-feu, consultez « Procédure : configurer un pare-feu pour accéder à SQL Server » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou passez en revue la documentation de votre pare-feu.  
  
## <a name="connecting-to-the-local-server"></a>Connexion au serveur local  
 Lorsque vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alors que celui-ci est exécuté sur le même ordinateur que l'ordinateur client, vous pouvez utiliser `(local)` comme nom de serveur. L'utilisation de `(local)` n'est pas conseillée dans la mesure où elle est source d'ambiguïté ; toutefois, elle peut s'avérer utile lorsqu'il est certain que le client s'exécute sur l'ordinateur prévu. Par exemple, lorsque vous créez une application destinée à des utilisateurs itinérants déconnectés, tels que des vendeurs, pour lesquels [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute sur des ordinateurs portables et stocke les données de projet, un client établissant une connexion à (local) se connecte toujours à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cours d'exécution sur l'ordinateur portable. Vous pouvez utiliser le mot `localhost` ou un point (.) à la place de `(local)`.  
  
## <a name="verifying-your-connection-protocol"></a>Vérification de votre protocole de connexion  
 La requête suivante retournera le protocole utilisé pour la connexion active.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>Exemples  
 Connexion au canal par défaut à partir du nom de serveur :  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 Connexion au canal par défaut à partir de l'adresse IP :  
  
```  
Alias Name         <serveralias>  
Pipe Name          <leave blank>  
Protocol           Named Pipes  
Server             <IPAddress>  
  
```  
  
 Connexion à partir du nom de serveur à un canal autre que celui utilisé par défaut :  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\unit\app  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 Connexion à une instance nommée à partir du nom de serveur :  
  
```  
Alias Name         <serveralias>  
Pipe Name          \\<servername>\pipe\MSSQL$<instancename>\SQL\query  
Protocol           Named Pipes  
Server             <servername>  
  
```  
  
 Connexion à l'ordinateur local à l'aide du paramètre `localhost`:  
  
```  
Alias Name         <serveralias>  
Pipe Name          <blank>  
Protocol           Named Pipes  
Server             localhost  
  
```  
  
 Connexion à l'ordinateur local à l'aide d'un point :  
  
```  
Alias Name         <serveralias>  
Pipe Name          <left blank>  
Protocol           Named Pipes  
Server             .  
  
```  
  
> [!NOTE]  
>  Pour spécifier le protocole réseau comme un **sqlcmd** paramètre, consultez « Comment : se connecter au moteur de base de données à l’aide de sqlcmd.exe » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une chaîne de connexion valide à l’aide du protocole de mémoire partagée](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)   
 [Création d’une chaîne de connexion valide avec TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Choix d’un protocole réseau](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)  
  
  
