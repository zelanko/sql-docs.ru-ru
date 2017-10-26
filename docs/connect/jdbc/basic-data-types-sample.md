---
title: "Типы основных данных образец | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59ac80cf-fc66-4493-933d-38e479c5f54d
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 424b1442a554cc2e4e52b0bf11c50c276d2a32cf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="basic-data-types-sample"></a>Образец базовых типов данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Это [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] образце приложения показано использование методов считывания результирующих наборов для извлечения базовых [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] тип данных значения, а также использование методов обновления результирующего набора для обновления этих величин.  
  
 Файл кода для этого образца имеет имя basicDT.java и находится в следующей папке:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \samples\datatypes  
  
## <a name="requirements"></a>Требования  
 Чтобы запустить этот образец приложения, необходимо в пути к классу указать файл sqljdbc.jar или файл sqljdbc4.jar. Если в пути к классу не указан файл sqljdbc.jar или sqljdbc4.jar, то образец приложения вызовет распространенное исключение «Класс не найден». Также потребуется доступ к [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных. Дополнительные сведения о том, как задать значение переменной classpath см. в разделе [с помощью драйвера JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
 Также необходимо создать следующие таблицы и образцы данных в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных:  
  
```  
use AdventureWorks  
CREATE TABLE DataTypesTable   
   (Col1 int IDENTITY,   
    Col2 char,  
    Col3 varchar(50),   
    Col4 bit,  
    Col5 decimal(18, 2),  
    Col6 money,  
    Col7 datetime,  
    Col8 date,  
    Col9 time,  
    Col10 datetime2,  
    Col11 datetimeoffset  
    );  
  
INSERT INTO DataTypesTable   
VALUES ('A', 'Some text.', 0, 15.25, 10.00, '01/01/2006 23:59:59.991', '01/01/2006', '23:59:59', '01/01/2006 23:59:59.12345', '01/01/2006 23:59:59.12345 -1:00')  
```  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Предоставляет файлы библиотек классов для использования в зависимости от выбранных параметров среды выполнения Java (JRE) sqljdbc.jar и sqljdbc4.jar. Дополнительные сведения о какие файлы JAR следует выбрать см. в разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Пример  
 В следующем примере образец кода устанавливает соединение для [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] базы данных, а затем получает одну строку данных из тестовой таблицы DataTypesTable. Чтобы отобразить все данные, содержащиеся в результирующем наборе, с помощью различных get затем вызывается метод пользовательских displayRow\<типа > методы [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) класса.  
  
 Затем в образце используется различные обновления\<типа > методы класса SQLServerResultSet класса для обновления данных, содержащихся в результирующем наборе, а затем вызывает [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) метод, чтобы снова сохранить данные в базу данных.  
  
 Наконец в образце обновляются данные, содержащиеся в результирующий набор и затем вызывает метод пользовательского displayRow еще раз, чтобы отобразить данные, содержащиеся в результирующем установлен.  
  
```java
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerResultSet;  
import microsoft.sql.DateTimeOffset;  
  
public class basicDT {  
   public static void main(String[] args) {  
  
      // Create a variable for the connection string.  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;databaseName=AdventureWorks;integratedSecurity=true;";  
  
      // Declare the JDBC objects.  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
         // Establish the connection.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
  
         // Create and execute an SQL statement that returns some data  
         // and display it.  
         String SQL = "SELECT * FROM DataTypesTable";  
         stmt = con.createStatement(ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_UPDATABLE);  
         rs = stmt.executeQuery(SQL);           
         rs.next();  
         displayRow("ORIGINAL DATA", rs);  
  
         // Update the data in the result set.  
         rs.updateString(2, "B");  
         rs.updateString(3, "Some updated text.");  
         rs.updateBoolean(4, true);  
         rs.updateDouble(5, 77.89);  
         rs.updateDouble(6, 1000.01);  
         long timeInMillis = System.currentTimeMillis();  
         Timestamp ts = new Timestamp(timeInMillis);  
         rs.updateTimestamp(7, ts);  
         rs.updateDate(8, new Date(timeInMillis));  
         rs.updateTime(9, new Time(timeInMillis));  
         rs.updateTimestamp(10, ts);  
  
         //-480 indicates GMT - 8:00 hrs  
         ((SQLServerResultSet)rs).updateDateTimeOffset(11, DateTimeOffset.valueOf(ts, -480));  
  
         rs.updateRow();  
  
         // Get the updated data from the database and display it.  
         rs = stmt.executeQuery(SQL);  
         rs.next();  
         displayRow("UPDATED DATA", rs);  
      }  
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
  
      finally {  
         if (rs != null)   
         try {   
         rs.close();   
         }   
         catch(Exception e) {}  
  
         if (stmt != null)   
         try { stmt.close();   
         }   
         catch(Exception e) {}  
  
         if (con != null)   
         try {   
         con.close();   
         }   
         catch(Exception e) {}  
      }  
   }  
  
   private static void displayRow(String title, ResultSet rs) {  
      try {  
         System.out.println(title);  
         System.out.println(rs.getInt(1) + " , " +  // SQL integer type.  
               rs.getString(2) + " , " +            // SQL char type.  
               rs.getString(3) + " , " +            // SQL varchar type.  
               rs.getBoolean(4) + " , " +           // SQL bit type.  
               rs.getDouble(5) + " , " +            // SQL decimal type.  
               rs.getDouble(6) + " , " +            // SQL money type.  
               rs.getTimestamp(7) + " , " +            // SQL datetime type.  
               rs.getDate(8) + " , " +              // SQL date type.  
               rs.getTime(9) + " , " +              // SQL time type.  
               rs.getTimestamp(10) + " , " +            // SQL datetime2 type.  
               ((SQLServerResultSet)rs).getDateTimeOffset(11)); // SQL datetimeoffset type.   
  
         System.out.println();  
      } catch (Exception e) {  
         e.printStackTrace();  
      }  
   }  
}  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Работа с типами данных &#40; JDBC &#41;](../../connect/jdbc/working-with-data-types-jdbc.md)  
  
  

