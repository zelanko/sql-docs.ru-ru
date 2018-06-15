---
title: Изменение образца данных результирующего набора | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b5ae54dc-2a79-4664-bb21-cacdb7d745e1
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47b2f8566607ec119aaa61a29468c7fca6388b5e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32831949"
---
# <a name="modifying-result-set-data-sample"></a>Изменение образца данных результирующего набора
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Это [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] образце приложения показано излечение обновляемого набора данных из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных. Затем с помощью методов класса [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта добавляет, изменяет и наконец удаляет строки данных из набора данных.  
  
 Файл кода для этого образца имеет имя updateRS.java и находится в следующей папке:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \samples\resultsets  
  
## <a name="requirements"></a>Требования  
 Чтобы запустить образец приложения, необходимо в пути к классу указать файл sqljdbc.jar или файл sqljdbc4.jar. Если в пути к классу не указан файл sqljdbc.jar или sqljdbc4.jar, то образец приложения вызовет распространенное исключение «Класс не найден». Также потребуется доступ к [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных. Дополнительные сведения о том, как задать значение переменной classpath см. в разделе [с помощью драйвера JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Предоставляет файлы библиотек классов для использования в зависимости от выбранных параметров среды выполнения Java (JRE) sqljdbc.jar и sqljdbc4.jar. Дополнительные сведения о какие файлы JAR следует выбрать см. в разделе [требования к системе для драйвера JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Пример  
 В следующем примере образец кода устанавливает соединение для [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных. Затем с помощью инструкции SQL с [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта, он выполняет инструкцию SQL и помещает данные, возвращенные в обновляемый объект SQLServerResultSet.  
  
 Затем в примере кода используется [moveToInsertRow](../../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md) метод, чтобы переместить курсор результирующего набора в строку вставки использует ряд [updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md) методов для вставки данных в новую строку, а затем вызывает [insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md) метод для сохранения новой строки данных в базе данных.  
  
 После вставки новой строки данных, в примере кода используется инструкция SQL для получения предварительно введенную строку и затем используется комбинация методов updateString и [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) методы для обновления строки данных и ее сохранения обратно в База данных.  
  
 Наконец, образец кода извлекает предварительно обновленную строку данных, а затем удаляет его из базы данных с помощью [deleteRow](../../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md) метод.  
  
```java
import java.sql.*;  
  
public class updateRS {  
  
   public static void main(String[] args) {  
  
      // Create a variable for the connection string.  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
            "databaseName=AdventureWorks;integratedSecurity=true;";  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
  
         // Establish the connection.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
  
         // Create and execute an SQL statement, retrieving an updateable result set.  
         String SQL = "SELECT * FROM HumanResources.Department;";  
         stmt = con.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE);  
         rs = stmt.executeQuery(SQL);  
  
         // Insert a row of data.  
         rs.moveToInsertRow();  
         rs.updateString("Name", "Accounting");  
         rs.updateString("GroupName", "Executive General and Administration");  
         rs.updateString("ModifiedDate", "08/01/2006");  
         rs.insertRow();  
  
         // Retrieve the inserted row of data and display it.  
         SQL = "SELECT * FROM HumanResources.Department WHERE Name = 'Accounting';";  
         rs = stmt.executeQuery(SQL);  
         displayRow("ADDED ROW", rs);  
  
         // Update the row of data.  
         rs.first();  
         rs.updateString("GroupName", "Finance");  
         rs.updateRow();  
  
         // Retrieve the updated row of data and display it.  
         rs = stmt.executeQuery(SQL);  
         displayRow("UPDATED ROW", rs);  
  
         // Delete the row of data.  
         rs.first();  
         rs.deleteRow();  
         System.out.println("ROW DELETED");  
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
  
   private static void displayRow(String title, ResultSet rs) {  
      try {  
         System.out.println(title);  
         while (rs.next()) {  
            System.out.println(rs.getString("Name") + " : " + rs.getString("GroupName"));  
            System.out.println();  
         }  
      } catch (Exception e) {  
         e.printStackTrace();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Работа с результирующими наборами](../../../connect/jdbc/working-with-result-sets.md)  
  
  
