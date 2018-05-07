---
title: Использование зеркального отображения (JDBC) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
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
ms.openlocfilehash: 7528a85cd8e2eb258a89e6d7971ce0f80fa90258
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-database-mirroring-jdbc"></a>Использование зеркального отображения базы данных (JDBC)
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Зеркальное отображение базы данных представляет решение по повышению доступности базы данных и резервированию данных, реализуемое в основном программными средствами. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Предоставляет неявную поддержку зеркального отображения базы данных, поэтому разработчику не требуется писать дополнительный код или выполнять другие действия, если она настроена для базы данных.  
  
 Зеркальное отображение базы данных, реализованное отдельно для каждой базы данных, хранит копию [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] рабочей базы данных на резервном сервере. Это или «горячий», или «теплый» резервный сервер, в зависимости от конфигурации и состояния сеанса зеркального отображения базы данных. Сервер горячей замены поддерживает быструю отработку отказа без потери зафиксированных транзакций, а резервный сервер поддерживает принудительное обслуживание (с возможной потерей данных).  
  
 Рабочая база данных называется *основной* базы данных и резервная копия называется *зеркальный* базы данных. Основная и зеркальная базы данных должны находиться в разных экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] (экземпляры сервера), и их следует размещать на отдельных компьютерах, если это возможно.  
  
 Рабочий экземпляр сервера, который называется основным сервером, обменивается данными с резервным экземпляром сервера, который называется зеркальным сервером. Основной и зеркальный серверы выступают в роли участников в сеансе зеркального отображения базы данных. В случае сбоя основного сервера зеркальный сервер делает свою базу данных в основную базу данных в ходе процесса, называемого *перехода на другой ресурс*. Например, имеется два сервера-участника, Partner_A and Partner_B, при этом основная база данных изначально находится на сервере Partner_A (основной сервер), а зеркальная база данных — на сервере Partner_B (зеркальный сервер). Если сервер Partner_A переходит в режим вне сети, база данных на сервере Partner_B становится текущей основной базой данных. Когда сервер Partner_A возвращается в сеанс зеркального отображения, он становится зеркальным сервером, а его база данных — зеркальной базой данных.  
  
 В случае, когда сервер Partner_A вышел из строя без возможности восстановления, сервер Partner_C можно перевести в режим «в сети», чтобы работать в качестве зеркального сервера для Partner_B, который теперь играет роль основного. Однако в этой ситуации клиентское приложение должно содержать логику программирования, обеспечивающую обновление свойств строк соединения с учетом новых имен серверов, используемых в конфигурации зеркального отображения базы данных. В противном случае соединение с серверами может завершиться ошибкой.  
  
 Другие конфигурации зеркального отображения баз данных имеют разные уровни производительности и безопасности данных, а также поддерживают разные формы отработки отказа. Дополнительные сведения см. в разделе «Обзор для зеркального отображения базы данных» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="programming-considerations"></a>Замечания по программированию  
 Если сервер, на котором размещается основная база данных, дает сбой, в ответ на вызовы API клиентское приложение получает ошибки, которые указывают на потерю соединения с базой данных. В этом случае утрачиваются все незафиксированные изменения в базе данных и выполняется откат текущей транзакции. Приложение должно закрыть соединение (или освободить объект источника данных), а затем снова открыть его. После подключения новое соединение автоматически направляется на зеркальную базу данных, которая теперь играет роль основного сервера, а клиенту не нужно изменять строку соединения или объект источника данных.  
  
 Во время первоначального установления соединения основной сервер отправляет удостоверение партнера по обеспечению обработки отказа на клиент, который будет использоваться при отработке отказа. Когда приложение пытается установить первоначальное соединение с отказавшим основным сервером, клиенту неизвестно удостоверение партнера по обеспечению обработки отказа. Чтобы дать клиентам возможность справиться с этой ситуацией, свойство строки соединения failoverPartner и при необходимости [setFailoverPartner](../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) метод источника данных, позволяет клиенту указывать идентификатор отработки отказа Партнер по себе. Свойство клиента используется только в этом сценарии и не используется, если доступен основной сервер.  
  
> [!NOTE]  
>  Если свойство failoverPartner указывается в строке соединения или в объекте источника данных, то также необходимо установить свойство databaseName. В противном случае будет вызвано исключение. Если свойства failoverPartner и databaseName не заданы явно, то приложение не будет запускать отработку отказа в случае отказа основного сервера базы данных. Иначе говоря, автоматическое перенаправление работает только для соединений, где явно указаны свойства failoverPartner и databaseName. Дополнительные сведения о свойстве failoverPartner и других свойствах строки соединения см. в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Если сервер-партнер по обеспечению обработки отказа, указанный клиентом, не является сервером, который играет роль партнера по обеспечению отработки отказа для указанной базы данных, и если указанный сервер (база данных) участвует в зеркальном отображении, то соединение будет отклонено сервером. Несмотря на то что [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) класс предоставляет [getFailoverPartner](../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md) метода, этот метод возвращает только имя партнера отработки отказа, указанное в строке подключения или метод setFailoverPartner. Чтобы получить имя фактического перехода на другой ресурс участника, который используется в данный момент, воспользуйтесь следующим [!INCLUDE[tsql](../../includes/tsql_md.md)] инструкции:  
  
```  
SELECT m.mirroring_role_DESC, m.mirroring_state_DESC,  
m.mirroring_partner_instance FROM sys.databases as db,  
sys.database_mirroring AS m WHERE db.name = 'MirroringDBName'  
AND db.database_id = m.database_id  
```  
  
> [!NOTE]  
>  Эту инструкцию нужно изменить в соответствии с именем зеркальной базы данных.  
  
 Рекомендуется кэшировать сведения об участниках для обновления строки соединения или разработать план повторных попыток в случае, если первая попытка установления соединения завершается ошибкой.  
  
## <a name="example"></a>Пример  
 В следующем примере сначала выполняется попытка подключения к основному серверу. Если эта попытка завершается созданием исключения, выполняется попытка подключения к зеркальному серверу, который мог стать новым основным сервером. Заметьте, что в строке соединения используется свойство failoverPartner.  
  
```  
import java.sql.*;  
  
public class clientFailover {  
  
   public static void main(String[] args) {  
  
      // Create a variable for the connection string.  
      String connectionUrl = "jdbc:sqlserver://serverA:1433;" +  
         "databaseName=AdventureWorks;integratedSecurity=true;" +  
         "failoverPartner=serverB";  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      Statement stmt = null;  
  
      try {  
         // Establish the connection to the principal server.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
         System.out.println("Connected to the principal server.");  
  
         // Note that if a failover of serverA occurs here, then an  
         // exception will be thrown and the failover partner will  
         // be used in the first catch block below.  
  
         // Create and execute an SQL statement that inserts some data.  
         stmt = con.createStatement();  
  
         // Note that the following statement assumes that the   
         // TestTable table has been created in the AdventureWorks  
         // sample database.  
         stmt.executeUpdate("INSERT INTO TestTable (Col2, Col3) VALUES ('a', 10)");  
      }  
  
      // Handle any errors that may have occurred.  
      catch (SQLException se) {  
         try {  
            // The connection to the principal server failed,  
            // try the mirror server which may now be the new  
            // principal server.  
            System.out.println("Connection to principal server failed, " +  
            "trying the mirror server.");  
            con = DriverManager.getConnection(connectionUrl);  
            System.out.println("Connected to the new principal server.");  
            stmt = con.createStatement();  
            stmt.executeUpdate("INSERT INTO TestTable (Col2, Col3) VALUES ('a', 10)");  
         }  
         catch (Exception e) {  
            e.printStackTrace();  
         }  
      }  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
      // Close the JDBC objects.  
      finally {  
         if (stmt != null) try { stmt.close(); } catch(Exception e) {}  
         if (con != null) try { con.close(); } catch(Exception e) {}  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Соединение с SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
