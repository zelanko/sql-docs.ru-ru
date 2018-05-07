---
title: Образец URL-адреса подключения | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 96fabc42-59d1-4cc0-93c5-db00cbe55e95
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 38d0ae6f113968d2774ce5d842a34d38b2274609
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connection-url-sample"></a>Образец URL-адреса соединения
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Это [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] образец приложения показано, как подключиться к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных с помощью URL-адрес подключения. Также демонстрируется извлечение данных из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных с помощью инструкции SQL.  
  
 Файл кода для этого образца имеет имя connectURL.java и находится в следующей папке:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \samples\connections  
  
## <a name="requirements"></a>Требования  
 Чтобы запустить этот образец приложения, необходимо в пути к классу указать файл sqljdbc.jar или файл sqljdbc4.jar. Если в пути к классу не указан файл sqljdbc.jar или sqljdbc4.jar, то образец приложения вызовет распространенное исключение «Класс не найден». Также потребуется доступ к [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных. Дополнительные сведения о том, как задать значение переменной classpath см. в разделе [с помощью драйвера JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Предоставляет файлы библиотек классов для использования в зависимости от выбранных параметров среды выполнения Java (JRE) sqljdbc.jar и sqljdbc4.jar. Дополнительные сведения о какие файлы JAR следует выбрать см. в разделе [требования к системе для драйвера JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Пример  
 В следующем примере образец кода задает различные свойства соединения в URL-АДРЕСЕ соединения и затем вызывает метод getConnection для возвращения класса DriverManager [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.  
  
 Затем в примере кода используется [createStatement](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) метод для создания объекта SQLServerConnection [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта, а затем [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) метод вызывается для выполнения инструкции SQL.  
  
 Наконец, в образце используется [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект, возвращенный из метода executeQuery для перебора результатов, возвращенных инструкцией SQL.  
  
```java  
import java.sql.*;  
  
public class connectURL {  
  
   public static void main(String[] args) {  
  
      // Create a variable for the connection string.  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
         "databaseName=AdventureWorks;user=UserName;password=*****";  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
         // Establish the connection.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
  
         // Create and execute an SQL statement that returns some data.  
         String SQL = "SELECT TOP 10 * FROM Person.Contact";  
         stmt = con.createStatement();  
         rs = stmt.executeQuery(SQL);  
  
         // Iterate through the data in the result set and display it.  
         while (rs.next()) {  
            System.out.println(rs.getString(4) + " " + rs.getString(6));  
         }  
      }  
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
      finally {  
         if (rs != null) try { rs.close(); } catch(Exception e) {}  
         if (stmt != null) try { stmt.close(); } catch(Exception e) {}  
         if (con != null) try { con.close(); } catch(Exception e) {}  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Подключение к данным и их извлечение](../../../connect/jdbc/connecting-and-retrieving-data.md)  
  
  
