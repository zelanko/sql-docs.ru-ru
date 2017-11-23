---
title: "Образец данных кэширования результирующего набора | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13a95ebb-996c-4713-a1bd-5834fe22a334
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 131bf443f88c0071dcb158fb67c997d6b0c57de2
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="caching-result-set-data-sample"></a>Образец кэширования данных результирующего набора
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Это [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] образец демонстрирует способы извлечения больших объемов данных из базы данных, а затем управлять количеством строк данных, кэшированных на клиенте с помощью [setFetchSize](../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) метод [ SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
> [!NOTE]  
>  Ограничение количества строк, кэшируемых на клиенте, отличается от ограничения общего количества строк, которое может содержаться в результирующем наборе. Чтобы управлять общее число строк, содержащихся в результирующем наборе, используйте [setMaxRows](../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) объекта, который наследуется и [ SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) объектов.  
  
 Чтобы установить лимит на количество строк, кэшируемых на клиенте, необходимо сначала использовать серверный курсор при создании одного из объектов инструкции, специально указав тип курсора, который нужно использовать при создании объекта инструкции. Например, драйвер JDBC обеспечивает тип курсора TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, который является быстрый однопроходный, только для чтения серверный курсор для использования с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] баз данных.  
  
> [!NOTE]  
>  Альтернативой использованию определенного типа курсора SQL Server является использование свойства строки соединения selectMethod при задании для него значения "cursor". Дополнительные сведения о типах курсоров, поддерживаемых драйвером JDBC см. в разделе [Общие сведения о типах курсоров](../../connect/jdbc/understanding-cursor-types.md).  
  
 После выполнения запроса, содержащегося в объекте инструкции и данные возвращается клиенту как результирующий набор, можно вызвать метод setFetchSize для управления объемом данных извлекается из базы данных за один раз. Например, если имеется таблица, в которой содержится 100 строк данных, и значение размера выборки равно 10, то на клиенте в определенный момент времени будет кэшироваться только 10 строк. Хотя при этом будет уменьшена скорость обработки данных, преимуществом является использование меньшего объема памяти на клиенте, что особенно ценно при необходимости обработки больших объемов данных.  
  
 Файл кода для этого образца имеет имя cacheRS.java и находится в следующей папке:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \samples\resultsets  
  
## <a name="requirements"></a>Требования  
 Чтобы запустить образец приложения, необходимо в пути к классу указать файл sqljdbc.jar или файл sqljdbc4.jar. Если в пути к классу не указан файл sqljdbc.jar или sqljdbc4.jar, то образец приложения вызовет распространенное исключение «Класс не найден». Также потребуется доступ к [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных. Дополнительные сведения о том, как задать значение переменной classpath см. в разделе [с помощью драйвера JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Предоставляет файлы библиотек классов для использования в зависимости от выбранных параметров среды выполнения Java (JRE) sqljdbc.jar и sqljdbc4.jar. Дополнительные сведения о какие файлы JAR следует выбрать см. в разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Пример  
 В следующем примере образец кода устанавливает соединение для [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных. Затем она использует инструкции SQL с [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) объекта, указывает тип серверный курсор и выполняет инструкцию SQL и помещает данные, возвращенные в объект SQLServerResultSet.  
  
 Далее образец кода вызывает метод пользовательского timerTest, передача в качестве аргументов размер выборки для использования и результирующий набор. Метод timerTest затем задает размер выборки результирующего набора с помощью метода setFetchSize задает время начала теста и затем просматривает результирующий набор с `While` цикла. Как только `While` цикла, код задает время остановки теста, а затем отображает результат проверки, включая размер выборки, количество строк, обработанных, и количество времени, затраченного на выполнение теста.  
  
```java
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.SQLServerResultSet;  
  
public class cacheRS {  
  
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
  
         // Create and execute an SQL statement that returns a large  
         // set of data and then display it.  
         String SQL = "SELECT * FROM Sales.SalesOrderDetail;";  
         stmt = con.createStatement(SQLServerResultSet.TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, +  
               SQLServerResultSet.CONCUR_READ_ONLY);  
  
         // Perform a fetch for every row in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(1, rs);  
         rs.close();  
  
         // Perform a fetch for every tenth row in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(10, rs);  
         rs.close();  
  
         // Perform a fetch for every 100th row in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(100, rs);  
         rs.close();  
  
         // Perform a fetch for every 1000th row in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(1000, rs);  
         rs.close();  
  
         // Perform a fetch for every 128th row (the default) in the result set.  
         rs = stmt.executeQuery(SQL);  
         timerTest(0, rs);  
         rs.close();  
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
  
   private static void timerTest(int fetchSize, ResultSet rs) {  
      try {  
  
         // Declare the variables for tracking the row count and elapsed time.  
         int rowCount = 0;  
         long startTime = 0;  
         long stopTime = 0;  
         long runTime = 0;  
  
         // Set the fetch size then iterate through the result set to  
         // cache the data locally.  
         rs.setFetchSize(fetchSize);  
         startTime = System.currentTimeMillis();  
         while (rs.next()) {  
            rowCount++;  
         }  
         stopTime = System.currentTimeMillis();  
         runTime = stopTime - startTime;  
  
         // Display the results of the timer test.  
         System.out.println("FETCH SIZE: " + rs.getFetchSize());  
         System.out.println("ROWS PROCESSED: " + rowCount);  
         System.out.println("TIME TO EXECUTE: " + runTime);  
         System.out.println();  
  
      } catch (Exception e) {  
         e.printStackTrace();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Работа с результирующими наборами](../../connect/jdbc/working-with-result-sets.md)  
  
  
