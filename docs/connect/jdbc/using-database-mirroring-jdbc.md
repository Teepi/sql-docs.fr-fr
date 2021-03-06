---
title: À l’aide de la base de données mise en miroir (JDBC) | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4ff59218-0d3b-4274-b647-9839c4955865
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 686e62581e2c18b79f20a25be6c5cd0ec0bcb3f8
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278673"
---
# <a name="using-database-mirroring-jdbc"></a>Utilisation de la mise en miroir de bases de données (JDBC)
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  La mise en miroir de bases de données est principalement une solution logicielle visant à augmenter la disponibilité de la base de données et la redondance des données. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] assure la prise en charge implicite de la mise en miroir de bases de données : lorsqu’il a été configuré pour la base de données, le développeur n’a pas de code à écrire ou d’autre mesure à prendre.  
  
 La mise en miroir de bases de données, implémentée pour chaque base de données, conserve une copie d’une base de données de production [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sur un serveur de secours. Ce serveur est un serveur de secours automatique ou semi-automatique, selon la configuration et l'état de la session de mise en miroir de bases de données. Un serveur en veille automatique prend en charge un basculement rapide sans perte de transactions validées ; un serveur en veille semi-automatique prend quant à lui en charge le service forcé (avec une perte de données éventuelle).  
  
 La base de données de production est appelée base de données *principale*, et la copie « en veille » est appelée base de données *miroir*. La base de données principale et la base de données miroir doivent résider sur des instances distinctes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] (instances de serveur) et, si possible, sur des ordinateurs distincts.  
  
 L'instance de serveur de production, également appelée serveur principal, communique avec l'instance de serveur en veille, également appelée serveur miroir. Les serveurs principal et miroir font agissent en tant que partenaires dans une session de mise en miroir de bases de données. En cas d’échec du serveur principal, le serveur miroir peut créer sa base de données dans la base de données principale grâce à un processus appelé *basculement*. Par exemple, Partner_A et Partner_B sont deux serveurs partenaires, avec initialement la base de données principale sur Partner_A comme serveur principal et la base de données miroir sur Partner_B comme serveur miroir. Si Partner_A se retrouve hors connexion, la base de données sur Partner_B peut basculer pour devenir la base de données principale en cours. Lorsque Partner_A rejoint la session de mise en miroir, il devient le serveur miroir et sa base de données devient la base de données miroir.  
  
 Si le serveur Partner_A est irrémédiablement endommagé, un serveur Partner_C peut être connecté pour faire office de serveur miroir pour Partner_B, qui est maintenant le serveur principal. Cependant, dans ce scénario, l'application cliente doit inclure une logique de programmation, afin de garantir la mise à jour des propriétés de chaîne de connexion avec les nouveaux noms de serveurs utilisés dans la configuration de la mise en miroir de bases de données. Si ce n'est pas le cas, la connexion aux serveurs risque d'échouer.  
  
 D'autres configurations de mise en miroir de bases de données offrent des niveaux différents de performances et de sécurité des données, et prennent en charge diverses formes de basculement. Pour plus d’informations, consultez « Présentation de la mise en miroir de bases de données » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="programming-considerations"></a>Éléments de programmation à prendre en considération  
 Lorsque le serveur de la base de données principale échoue, l'application cliente reçoit des erreurs en réponse aux appels d'API, erreurs qui signifient que la connexion à la base de données a été perdue. Lorsque cela se produit, toutes les modifications non validées apportées à la base de données sont perdues et la transaction actuelle est annulée. Dans ce cas, l'application doit fermer la connexion (ou libérer l'objet de la source de données) et essayer de la rouvrir. Lors de la connexion, la nouvelle connexion est redirigée de façon transparente vers la base de données miroir, qui joue maintenant le rôle de serveur principal, sans que le client ait à modifier l’objet de source de données ou la chaîne de connexion.  
  
 Lorsqu'une connexion est établie initialement, le serveur principal envoie l'identité de son partenaire de basculement au client qui sera utilisé lors d'un basculement. Lorsqu’une application tente d’établir une connexion initiale avec un serveur principal en échec, le client ne connaît pas l’identité du partenaire de basculement. Pour permettre aux clients de faire face à ce scénario, la propriété de chaîne de connexion failoverPartner, et éventuellement la méthode de source de données [setFailoverPartner](../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md), permet au client de spécifier tout seul l’identité du partenaire de basculement. La propriété du client ne sert que dans ce scénario ; si le serveur principal est disponible, elle n’est pas utilisée.  
  
> [!NOTE]  
>  Lorsqu'une propriété failoverPartner est spécifiée dans la chaîne de connexion ou conjointement avec un objet de la source de données, la propriété databaseName doit également être définie, sinon une exception sera levée. Si les propriétés failoverPartner et databaseName ne sont pas spécifiées explicitement, l'application ne tentera pas de basculer en cas d'échec du serveur de base de données principal. En d'autres termes, la redirection transparente fonctionne uniquement pour les connexions qui spécifient explicitement les propriétés failoverPartner et databaseName. Pour plus d’informations sur failoverPartner et d’autres propriétés de chaîne de connexion, consultez [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Si le serveur partenaire de basculement fourni par le client ne fait pas référence à un serveur jouant le rôle de partenaire de basculement de la base de données spécifiée et si le serveur/la base de données mentionné(e) est mis(e) en miroir, la connexion est refusée par le serveur. Bien que la classe [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) fournisse la méthode [getFailoverPartner](../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md), cette méthode retourne uniquement le nom du partenaire de basculement spécifié dans la chaîne de connexion ou la méthode setFailoverPartner. Pour extraire le nom du partenaire de basculement réel actuellement en cours d’utilisation, utilisez l’instruction [!INCLUDE[tsql](../../includes/tsql_md.md)] suivante :  
  
```sql
SELECT m.mirroring_role_DESC, m.mirroring_state_DESC,  
m.mirroring_partner_instance FROM sys.databases as db,  
sys.database_mirroring AS m WHERE db.name = 'MirroringDBName'  
AND db.database_id = m.database_id  
```  
  
> [!NOTE]  
>  Vous devrez modifier cette instruction pour utiliser le nom de votre base de données de mise en miroir.  
  
 Vous devez envisager de mettre en cache les informations du partenaire afin de mettre à jour la chaîne de connexion ou concevoir une stratégie de nouvelle tentative en cas d'échec de la première tentative de création d'une connexion.  
  
## <a name="example"></a> Exemple  
 Dans l'exemple suivant, une tentative est réalisée en premier lieu pour établir une connexion au serveur de principe. En cas d'échec et de génération d'une exception, une tentative est réalisée pour établir une connexion au serveur miroir, qui peut avoir été promu serveur de principe. Remarquez l'utilisation de la propriété failoverPartner dans la chaîne de connexion.  
  
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;

public class ClientFailover {
    public static void main(String[] args) {

        String connectionUrl = "jdbc:sqlserver://serverA:1433;" 
                + "databaseName=AdventureWorks;integratedSecurity=true;" 
                + "failoverPartner=serverB";

        // Establish the connection to the principal server.
        try (Connection con = DriverManager.getConnection(connectionUrl); 
                Statement stmt = con.createStatement();) {
            System.out.println("Connected to the principal server.");

            // Note that if a failover of serverA occurs here, then an
            // exception will be thrown and the failover partner will
            // be used in the first catch block below.

            // Execute a SQL statement that inserts some data.

            // Note that the following statement assumes that the
            // TestTable table has been created in the AdventureWorks
            // sample database.
            stmt.executeUpdate("INSERT INTO TestTable (Col2, Col3) VALUES ('a', 10)");
        }
        catch (SQLException se) {
            System.out.println("Connection to principal server failed, " + "trying the mirror server.");
            // The connection to the principal server failed,
            // try the mirror server which may now be the new
            // principal server.
            try (Connection con = DriverManager.getConnection(connectionUrl); 
                    Statement stmt = con.createStatement();) {
                System.out.println("Connected to the new principal server.");
                stmt.executeUpdate("INSERT INTO TestTable (Col2, Col3) VALUES ('a', 10)");
            }
            // Handle any errors that may have occurred.
            catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
}
```  
  
## <a name="see-also"></a> Voir aussi  
 [Connexion à SQL Server avec le pilote JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
