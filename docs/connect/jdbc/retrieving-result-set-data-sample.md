---
title: Получение образца данных результирующего набора | Документация Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1b190c36-3d38-49a2-8599-612329675851
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8fe0d97c8a8ec0f29e8a6b85542ea0627a5c6fb
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279145"
---
# <a name="retrieving-result-set-data-sample"></a>Получение образца данных результирующего набора
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этом образце приложения [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] показано получение набора данных из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и последующее отображение этих данных.  
  
 Файл кода для этого примера с имением RetrieveRS.java находится в следующей папке:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \samples\resultsets  
  
## <a name="requirements"></a>Требования  
 Чтобы запустить этот пример приложения, необходимо включить в параметр classpath путь к файлу mssql-jdbc.jar. Также потребуется доступ к примеру базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Дополнительные сведения о том, как путь к классу см. в разделе [с помощью драйвера JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Дополнительные сведения о какие файлы JAR следует выбрать, см. в разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере образец кода будет использоваться для соединения с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Затем с помощью инструкции SQL с объектом [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) выполняется инструкция SQL, а возвращенные ею данные помещаются в объект [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
 Далее пример кода вызывает настраиваемый метод displayRow для прохода по строкам данных в результирующем наборе, и некоторые из этих данных отображаются с помощью метода [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md).  
  
```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class RetrieveRS {

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            String SQL = "SELECT * FROM Production.Product;";
            ResultSet rs = stmt.executeQuery(SQL);
            displayRow("PRODUCTS", rs);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void displayRow(String title,
            ResultSet rs) throws SQLException {
        System.out.println(title);
        while (rs.next()) {
            System.out.println(rs.getString("ProductNumber") + " : " + rs.getString("Name"));
        }
    }
}
```  
  
## <a name="see-also"></a>См. также:  
 [Работа с результирующими наборами](../../connect/jdbc/working-with-result-sets.md)  
  
  
