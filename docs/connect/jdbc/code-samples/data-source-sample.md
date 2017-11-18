---
title: "Образец источника данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4a933ee-f2c6-4e0d-a96d-6dd061abf759
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9cda7cac56de964c97b2f60d416cbb83ff4e2b80
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="data-source-sample"></a>Образец источника данных
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Это [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] образец приложения показано, как подключиться к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных с помощью объекта источника данных. Также демонстрируется извлечение данных из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных с помощью хранимой процедуры.  
  
 Файл кода для этого образца имеет имя connectDS.java и находится в следующей папке:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \samples\connections  
  
## <a name="requirements"></a>Требования  
 Чтобы запустить этот образец приложения, необходимо в пути к классу указать файл sqljdbc.jar или файл sqljdbc4.jar. Если в пути к классу не указан файл sqljdbc.jar или sqljdbc4.jar, то образец приложения вызовет распространенное исключение «Класс не найден». Также потребуется доступ к [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных. Дополнительные сведения о том, как задать значение переменной classpath см. в разделе [с помощью драйвера JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Предоставляет файлы библиотек классов для использования в зависимости от выбранных параметров среды выполнения Java (JRE) sqljdbc.jar и sqljdbc4.jar. Дополнительные сведения о какие файлы JAR следует выбрать см. в разделе [требования к системе для драйвера JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Пример  
 В следующем примере образец кода задает различные свойства соединения, используя методы задания [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) объекта, а затем вызывает [getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) метод Возвращаемый объект SQLServerDataSource [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.  
  
 Затем в примере кода используется [prepareCall](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) метод для создания объекта SQLServerConnection [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) объекта, а затем [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) метод вызывается для выполнения хранимой процедуры.  
  
 Наконец, в образце используется [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект, возвращенный из метода executeQuery для перебора результатов, возвращаемых хранимой процедурой.  
  
```java
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  
  
public class connectDS {  
  
   public static void main(String[] args) {  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      CallableStatement cstmt = null;  
      ResultSet rs = null;  
  
      try {  
         // Establish the connection.   
         SQLServerDataSource ds = new SQLServerDataSource();  
         ds.setUser("UserName");  
         ds.setPassword("*****");  
         ds.setServerName("localhost");  
         ds.setPortNumber(1433);   
         ds.setDatabaseName("AdventureWorks");  
         con = ds.getConnection();  
  
         // Execute a stored procedure that returns some data.  
         cstmt = con.prepareCall("{call dbo.uspGetEmployeeManagers(?)}");  
         cstmt.setInt(1, 50);  
         rs = cstmt.executeQuery();  
  
         // Iterate through the data in the result set and display it.  
         while (rs.next()) {  
            System.out.println("EMPLOYEE: " + rs.getString("LastName") +   
               ", " + rs.getString("FirstName"));  
            System.out.println("MANAGER: " + rs.getString("ManagerLastName") +   
               ", " + rs.getString("ManagerFirstName"));  
            System.out.println();  
         }  
      }  
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
      finally {  
         if (rs != null) try { rs.close(); } catch(Exception e) {}  
         if (cstmt != null) try { cstmt.close(); } catch(Exception e) {}  
         if (con != null) try { con.close(); } catch(Exception e) {}  
         System.exit(1);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Подключение к данным и их извлечение](../../../connect/jdbc/connecting-and-retrieving-data.md)  
  
  

