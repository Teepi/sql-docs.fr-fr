---
title: Appel de méthodes | Microsoft Docs
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
helpviewer_keywords:
- methods [SMO]
- calling methods
- SQL Server Management Objects, method calling
- SMO [SQL Server], method calling
ms.assetid: c88d5c5f-9ff0-4f84-b2b6-24c6b90fa15e
caps.latest.revision: 44
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b2d2cce4fa8bf38e8403af1a783c9b1d85eb14aa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37264305"
---
# <a name="calling-methods"></a>Appel de méthodes
  Méthodes effectuent des tâches spécifiques liées à l’objet, telles que l’exécution une `Checkpoint` sur une base de données ou de la demande d’une liste énumérée d’ouvertures de session pour l’instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Les méthodes effectuent une opération sur un objet. Les méthodes peuvent accepter des paramètres et possèdent souvent une valeur de retour. La valeur de retour peut être un type de données simple, un objet complexe ou une structure qui contient de nombreux membres.  
  
 Utilisez la gestion des exceptions pour détecter si la méthode a réussi. Pour plus d’informations, consultez [Handling SMO Exceptions](handling-smo-exceptions.md).  
  
## <a name="examples"></a>Exemples  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="using-a-simple-smo-method-in-visual-basic"></a>Utilisation d'une méthode SMO simple en Visual Basic  
 Dans cet exemple, la méthode <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> n'accepte aucun paramètre et ne possède aucune valeur de retour.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods1](SMO How to#SMO_VBMethods1)]  -->  
  
## <a name="using-a-simple-smo-method-in-visual-c"></a>Utilisation d'une méthode SMO simple en Visual C#  
 Dans cet exemple, la méthode <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> n'accepte aucun paramètre et ne possède aucune valeur de retour.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define a Database object variable by supplying the parent server and the database name arguments in the constructor.   
Database db;   
db = new Database(srv, "Test_SMO_Database");   
//Call the Create method to create the database on the instance of SQL Server.   
db.Create();   
```  
  
 }  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-basic"></a>Utilisation d'une méthode SMO avec un paramètre en Visual Basic  
 Le <xref:Microsoft.SqlServer.Management.Smo.Table> objet possède une méthode appelée <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>. Cette méthode requiert un paramètre numérique qui spécifie le `FillFactor`.  
  
```  
Dim srv As Server  
srv = New Server  
Dim tb As Table  
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources")  
tb.RebuildIndexes(70)  
```  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-c"></a>Utilisation d'une méthode SMO avec un paramètre en Visual C#  
 Le <xref:Microsoft.SqlServer.Management.Smo.Table> objet possède une méthode appelée <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>. Cette méthode requiert un paramètre numérique qui spécifie le `FillFactor`.  
  
```  
{   
Server srv = default(Server);   
srv = new Server();   
Table tb = default(Table);   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
}   
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-basic"></a>Utilisation d'une méthode d'énumération qui retourne un objet DataTable en Visual Basic  
 Cette section décrit comment appeler une méthode d’énumération et comment gérer les données dans la liste retournée <xref:System.Data.DataTable> objet.  
  
 La méthode <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> retourne un objet <xref:System.Data.DataTable>, qui requiert une navigation supplémentaire pour accéder à toutes les informations de classement disponibles sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
'Connect to the local, default instance of SQL Server.  
Dim srv As Server  
srv = New Server  
'Call the EnumCollations method and return collation information to DataTable variable.  
Dim d As DataTable  
'Select the returned data into an array of DataRow.  
d = srv.EnumCollations  
'Iterate through the rows and display collation details for the instance of SQL Server.  
Dim r As DataRow  
Dim c As DataColumn  
For Each r In d.Rows  
    Console.WriteLine("==")  
    For Each c In r.Table.Columns  
        Console.WriteLine(c.ColumnName + " = " + r(c).ToString)  
    Next  
Next  
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-c"></a>Utilisation d'une méthode d'énumération qui retourne un objet DataTable en Visual C#  
 Cette section décrit comment appeler une méthode d’énumération et comment gérer les données dans la liste retournée <xref:System.Data.DataTable> objet.  
  
 Le <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> méthode retourne un système <xref:System.Data.DataTable> objet. Le <xref:System.Data.DataTable> objet requiert une navigation pour accéder à toutes les informations de classement disponibles sur l’instance de supplémentaire [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumCollations;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=========");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="constructing-an-object-in-visual-basic"></a>Construction d'un objet en Visual Basic  
 Le constructeur d'un objet quelconque peut être appelé au moyen de l'opérateur `New`. Le constructeur d'objet <xref:Microsoft.SqlServer.Management.Smo.Database> est surchargé et la version du constructeur d'objet <xref:Microsoft.SqlServer.Management.Smo.Database> utilisée dans l'exemple accepte deux paramètres : l'objet parent <xref:Microsoft.SqlServer.Management.Smo.Server> auquel la base de données appartient et une chaîne qui représente le nom de la nouvelle base de données.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods4](SMO How to#SMO_VBMethods4)]  -->  
  
## <a name="constructing-an-object-in-visual-c"></a>Construction d'un objet en Visual C#  
 Le constructeur d'un objet quelconque peut être appelé au moyen de l'opérateur `New`. Le constructeur d'objet <xref:Microsoft.SqlServer.Management.Smo.Database> est surchargé et la version du constructeur d'objet <xref:Microsoft.SqlServer.Management.Smo.Database> utilisée dans l'exemple accepte deux paramètres : l'objet parent <xref:Microsoft.SqlServer.Management.Smo.Server> auquel la base de données appartient et une chaîne qui représente le nom de la nouvelle base de données.  
  
```  
{   
Server srv;   
srv = new Server();   
Table tb;   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Declare and define a Database object by supplying the parent server and the database name arguments in the constructor.   
Database d;   
d = new Database(srv, "Test_SMO_Database");   
//Create the database on the instance of SQL Server.   
d.Create();   
Console.WriteLine(d.Name);   
}  
```  
  
## <a name="copying-an-smo-object-in-visual-basic"></a>Copie d'un objet SMO en Visual Basic  
 Cet exemple de code utilise le <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> méthode pour créer une copie de la <xref:Microsoft.SqlServer.Management.Smo.Server> objet. Le <xref:Microsoft.SqlServer.Management.Smo.Server> objet représente une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VCMethods6](SMO How to#SMO_VCMethods6)]  -->  
  
## <a name="copying-an-smo-object-in-visual-c"></a>Copie d'un objet SMO en Visual C#  
 Cet exemple de code utilise le <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> méthode pour créer une copie de la <xref:Microsoft.SqlServer.Management.Smo.Server> objet. Le <xref:Microsoft.SqlServer.Management.Smo.Server> objet représente une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv1;   
srv1 = new Server();   
//Modify the default database and the timeout period for the connection.   
srv1.ConnectionContext.DatabaseName = "AdventureWorks2012";   
srv1.ConnectionContext.ConnectTimeout = 30;   
//Make a second connection using a copy of the ConnectionContext property and verify settings.   
Server srv2;   
srv2 = new Server(srv1.ConnectionContext.Copy);   
Console.WriteLine(srv2.ConnectionContext.ConnectTimeout.ToString);   
}  
```  
  
## <a name="monitoring-server-processes-in-visual-basic"></a>Surveillance des processus serveur en Visual Basic  
 Vous pouvez obtenir les informations de type d’état en cours sur l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] via les méthodes d’énumération. L'exemple de code utilise la méthode <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> pour découvrir des informations sur les processus en cours. Il montre également comment utiliser les colonnes et les lignes incluses dans l'objet <xref:System.Data.DataTable> retourné.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods5](SMO How to#SMO_VBMethods5)]  -->  
  
## <a name="monitoring-server-processes-in-visual-c"></a>Surveillance des processus serveur en Visual C#  
 Vous pouvez obtenir les informations de type d’état en cours sur l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] via les méthodes d’énumération. L'exemple de code utilise la méthode <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> pour découvrir des informations sur les processus en cours. Il montre également comment utiliser les colonnes et les lignes incluses dans l'objet <xref:System.Data.DataTable> retourné.  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumProcesses;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=====");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
