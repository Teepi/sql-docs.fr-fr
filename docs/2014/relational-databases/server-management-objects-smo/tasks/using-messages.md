---
title: À l’aide de Messages | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- messages [SMO]
ms.assetid: 4037a866-4826-4c1f-890c-e7e3658adf13
caps.latest.revision: 38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 868af8443b01b44b79642b6c7f2ef321b9513203
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164230"
---
# <a name="using-messages"></a>Utilisation de messages
  Dans SMO, les messages système sont représentés par l'objet <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection> qui appartient à l'objet `Server`. Comme les messages système ne peuvent pas être modifiés, les propriétés d'objet `SystemMessage` sont en lecture seule.  
  
 Les messages définis par l'utilisateur sont représentés par programme dans SMO par l'objet <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection>. Les messages définis par l'utilisateur existants peuvent être découverts en parcourant la collection. Les nouveaux messages définis par l'utilisateur peuvent être créés par instanciation d'un nouvel objet `UserDefinedMessage` et définition des propriétés appropriées.  
  
## <a name="examples"></a>Exemples  
 Dans les exemples de code suivants, vous devez sélectionner l'environnement, le modèle et le langage de programmation à utiliser pour créer votre application. Pour plus d’informations, consultez [créer un projet SMO Visual Basic dans Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) et [créer un Visual C&#35; projet SMO dans Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="finding-a-particular-system-message-in-visual-basic"></a>Recherche d'un message système particulier en Visual Basic  
 L'exemple de code montre comment identifier un message système par son numéro d'ID et afficher le message.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMessages1](SMO How to#SMO_VBMessages1)]  -->  
  
## <a name="finding-a-particular-system-message-in-visual-c"></a>Recherche d'un message système particulier en Visual C#  
 L'exemple de code montre comment identifier un message système par son numéro d'ID et afficher le message.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference an existing system message using the   
            //ItemByIdAndLanguage method.   
            SystemMessage msg = default(SystemMessage);  
            msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
        }  
```  
  
## <a name="finding-a-particular-system-message-in-powershell"></a>Recherche d'un message système particulier dans PowerShell  
 L'exemple de code montre comment identifier un message système par son numéro d'ID et afficher le message.  
  
```  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Get the message 14126 in US English and display it  
$msg = $srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")  
$msg.ID.ToString() + " "+ $msg.Text  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-basic"></a>Ajout d'un nouveau message défini par l'utilisateur en Visual Basic  
 L'exemple de code montre comment créer un message défini par l'utilisateur avec un ID supérieur à 50000.  
  
```  
Dim mysrv As Server  
mysrv = New Server  
Dim udm As UserDefinedMessage  
udm = New UserDefinedMessage(mysrv, 50003, "us_english", 16, "Test message")  
udm.Create()  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-c"></a>Ajout d'un nouveau message défini par l'utilisateur en Visual C#  
 L'exemple de code montre comment créer un message défini par l'utilisateur avec un ID supérieur à 50000.  
  
```  
{  
  
            Server mysrv = new Server();  
  
            UserDefinedMessage udm = new UserDefinedMessage(mysrv, 50030, "us_english",16, "Test message");  
            udm.Create();  
             UserDefinedMessage  msg = mysrv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
  
        }  
```  
  
## <a name="adding-a-new-user-defined-message-in-powershell"></a>Ajout d'un nouveau message défini par l'utilisateur dans PowerShell  
 L'exemple de code montre comment créer un message défini par l'utilisateur avec un ID supérieur à 50000.  
  
```  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a new message  
  
$udm = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedMessage -argumentlist `  
$srv, 50030, "us_english", 16, "Test message"  
$udm.Create()  
$msg = $srv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
$msg  
```  
  
  
