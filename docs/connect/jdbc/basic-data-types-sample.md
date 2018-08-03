---
title: Типы пример основных данных | Документация Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 59ac80cf-fc66-4493-933d-38e479c5f54d
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ad4aae1e069b487351dd63f6f7bc7f5fc791407
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278896"
---
# <a name="basic-data-types-sample"></a>Образец базовых типов данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этом примере приложения, использующем драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], показано использование методов считывания результирующего набора для получения значений базовых типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], а также использование методов обновления результирующего набора для обновления таких значений.  
  
 Файл кода для этого примера имеет имя BasicDT.java и находится в следующей папке:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \samples\datatypes  
  
## <a name="requirements"></a>Требования  
 Чтобы запустить этот пример приложения, необходимо включить в параметр classpath путь к файлу mssql-jdbc.jar. Также потребуется доступ к образцу базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Дополнительные сведения о том, как путь к классу см. в разделе [с помощью драйвера JDBC](../../connect/jdbc/using-the-jdbc-driver.md).  
  
 Создайте следующую таблицу и образец данных в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]:  
  
```sql
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
>  Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Дополнительные сведения о какие файлы JAR следует выбрать, см. в разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Пример  
 В следующем примере образец кода устанавливает соединение с базой данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], а затем получает одну строку данных из тестовой таблицы DataTypesTable. Затем вызывается пользовательский метод displayRow, чтобы вывести все данные в результирующем наборе с помощью различных методов get\<Type> класса [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
 Затем с помощью различных методов update\<Type> класса SQLServerResultSet выполняется обновление данных в результирующем наборе и вызывается метод [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md), записывающий данные обратно в базу данных.  
  
 Наконец, в образце обновляются данные в результирующем наборе и снова вызывается пользовательский метод displayRow, чтобы показать данные в результирующем наборе.  
  
```java
import java.sql.Connection;
import java.sql.Date;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.sql.Time;
import java.sql.Timestamp;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

import microsoft.sql.DateTimeOffset;

public class BasicDT {
    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_UPDATABLE);) {

            String SQL = "SELECT * FROM DataTypesTable";
            ResultSet rs = stmt.executeQuery(SQL);
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

            // -480 indicates GMT - 8:00 hrs
            ((SQLServerResultSet) rs).updateDateTimeOffset(11, DateTimeOffset.valueOf(ts, -480));

            rs.updateRow();

            // Get the updated data from the database and display it.
            rs = stmt.executeQuery(SQL);
            rs.next();
            displayRow("UPDATED DATA", rs);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void displayRow(String title,
            ResultSet rs) throws SQLException {
        System.out.println(title);
        System.out.println(rs.getInt(1) + " , " +                 // SQL integer type.
                rs.getString(2) + " , " +                         // SQL char type.
                rs.getString(3) + " , " +                         // SQL varchar type.
                rs.getBoolean(4) + " , " +                        // SQL bit type.
                rs.getDouble(5) + " , " +                         // SQL decimal type.
                rs.getDouble(6) + " , " +                         // SQL money type.
                rs.getTimestamp(7) + " , " +                      // SQL datetime type.
                rs.getDate(8) + " , " +                           // SQL date type.
                rs.getTime(9) + " , " +                           // SQL time type.
                rs.getTimestamp(10) + " , " +                     // SQL datetime2 type.
                ((SQLServerResultSet) rs).getDateTimeOffset(11)); // SQL datetimeoffset type.
        System.out.println();
    }
}
```  
  
## <a name="see-also"></a>См. также:  
 [Работа с типами данных (JDBC)](../../connect/jdbc/working-with-data-types-jdbc.md)  
  
  
