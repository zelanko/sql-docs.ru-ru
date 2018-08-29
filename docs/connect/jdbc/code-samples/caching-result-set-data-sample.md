---
title: Образец данных кэширования результирующего набора | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 13a95ebb-996c-4713-a1bd-5834fe22a334
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5e8a0435a606152852c39450801497cd100fe90d
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785388"
---
# <a name="caching-result-set-data-sample"></a>Образец кэширования данных результирующего набора

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Этот пример приложения, использующего драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], демонстрирует способы извлечения больших объемов данных из базы данных и управления количеством строк данных, кэшируемых на клиенте с помощью метода [setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md) объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
> [!NOTE]  
> Ограничение количества строк, кэшируемых на клиенте, отличается от ограничения общего количества строк, которое может содержаться в результирующем наборе. Для управления общим количеством строк, которое может содержаться в результирующем наборе, следует использовать метод [setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md) объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), наследуемый объектами [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md).  
  
Чтобы ограничить количество строк, кэшируемых на клиенте, необходимо сначала использовать курсор на стороне сервера при создании одного из объектов Statement, специально указав тип курсора, который необходимо использовать при создании объекта Statement. Например, драйвер JDBC обеспечивает тип курсора TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, который является быстрым однопроходным курсором только для чтения на стороне сервера для использования при работе с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
> Альтернативой использованию определенного типа курсора SQL Server является использование свойства строки соединения selectMethod при задании для него значения "cursor". Дополнительные сведения о типах курсоров, поддерживаемых драйвером JDBC, см. в разделе [Общие сведения о типах курсоров](../../../connect/jdbc/understanding-cursor-types.md).  
  
После выполнения запроса в объекте Statement и возврате данных клиенту в виде результирующего набора можно вызвать метод setFetchSize для управления объемом данных, извлекаемых единовременно из базы данных. Например, если имеется таблица, в которой содержится 100 строк данных, и значение размера выборки равно 10, то на клиенте в определенный момент времени будет кэшироваться только 10 строк. Хотя при этом будет уменьшена скорость обработки данных, преимуществом является использование меньшего объема памяти на клиенте, что особенно ценно при необходимости обработки больших объемов данных.  
  
Файл кода для этого примера с именем CacheResultSet.java находится в следующей папке:  

```bash  
\<installation directory>\sqljdbc_<version>\<language>\samples\resultsets  
```

## <a name="requirements"></a>Требования  

Чтобы запустить этот пример приложения, необходимо включить в параметр classpath путь к файлу mssql-jdbc.jar. Также потребуется доступ к примеру базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Дополнительные сведения о том, как путь к классу см. в разделе [с помощью драйвера JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Дополнительные сведения о какие файлы JAR следует выбрать, см. в разделе [требования к системе для драйвера JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  

## <a name="example"></a>Пример  

В приведенном ниже примере образец кода будет использоваться для соединения с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Затем используется инструкция SQL с объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), указывается тип курсора на стороне сервера и выполняется инструкция SQL, а возвращенные ею данные помещаются в объект SQLServerResultSet.  
  
Затем образец кода вызывает специальный метод timerTest, передавая в качестве аргументов размер выборки для использования и результирующий набор. Затем метод timerTest задает размер выборки результирующего набора с помощью метода setFetchSize, задает время начала проверки и затем просматривает результирующий набор в цикле `While`. После завершения цикла `While` код задает время завершения проверки и отображает результат проверки, включая размер выборки, количество обработанных строк и время выполнения проверки.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.ArrayList;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

public class CacheResultSet {

    @SuppressWarnings("serial")
    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(SQLServerResultSet.TYPE_SS_SERVER_CURSOR_FORWARD_ONLY, SQLServerResultSet.CONCUR_READ_ONLY);) {

            String SQL = "SELECT * FROM Sales.SalesOrderDetail;";

            for (int n : new ArrayList<Integer>() {
                {
                    add(1);
                    add(10);
                    add(100);
                    add(1000);
                    add(0);
                }
            }) {
                // Perform a fetch for every nth row in the result set.
                try (ResultSet rs = stmt.executeQuery(SQL)) {
                    timerTest(n, rs);
                }
            }
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void timerTest(int fetchSize,
            ResultSet rs) throws SQLException {

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
    }
}
```

## <a name="see-also"></a>См. также:  

[Работа с результирующими наборами](../../../connect/jdbc/code-samples/working-with-result-sets.md)  
