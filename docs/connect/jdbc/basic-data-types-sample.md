---
title: Пример основных типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 59ac80cf-fc66-4493-933d-38e479c5f54d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9374c76a76aa12f60fc3fa5f911916f39000d8b4
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028461"
---
# <a name="basic-data-types-sample"></a>Пример базовых типов данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этом примере приложения, использующем драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], показано использование методов считывания результирующего набора для получения значений базовых типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а также использование методов обновления результирующего набора для обновления таких значений.

Файл кода для этого примера имеет имя BasicDT.java и находится в следующей папке:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\datatypes
```

## <a name="requirements"></a>Требования

Чтобы запустить этот пример приложения, необходимо включить в параметр classpath путь к файлу mssql-jdbc.jar. Также потребуется доступ к примеру базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Дополнительные сведения о настройке подкаталогов классов см. в разделе [Использование драйвера JDBC](../../connect/jdbc/using-the-jdbc-driver.md).

Образец создаст необходимую таблицу и вставит образец данных в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образец базы данных:

> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Для получения дополнительных сведений о том, какой JAR-файл выбрать, см. статью [Требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Пример

В следующем примере образец кода устанавливает соединение с базой данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], а затем получает одну строку данных из тестовой таблицы DataTypesTable. Затем вызывается пользовательский метод displayRow, чтобы вывести все данные в результирующем наборе с помощью различных методов get\<Type> класса [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).

Затем с помощью различных методов update\<Type> класса SQLServerResultSet выполняется обновление данных в результирующем наборе и вызывается метод [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md), записывающий данные обратно в базу данных.

Наконец, в образце обновляются данные в результирующем наборе и снова вызывается пользовательский метод displayRow, чтобы показать данные в результирующем наборе.

```java
import java.sql.Connection;
import java.sql.Date;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.sql.Time;
import java.sql.Timestamp;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

import microsoft.sql.DateTimeOffset;

public class BasicDataTypes {
    private static final String tableName = "DataTypesTable";

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_UPDATABLE);) {

            dropAndCreateTable(stmt);
            insertOriginalData(con);

            String SQL = "SELECT * FROM " + tableName;
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

    private static void dropAndCreateTable(Statement stmt) throws SQLException {
        stmt.executeUpdate("if object_id('" + tableName + "','U') is not null" + " drop table " + tableName);

        String sql = "create table " + tableName + " (" + "c1 int, " + "c2 char(20), " + "c3 varchar(20), " + "c4 bit, "
                + "c5 decimal(10,5), " + "c6 money, " + "c7 datetime, " + "c8 date, " + "c9 time(7), "
                + "c10 datetime2(7), " + "c11 datetimeoffset(7), " + ");";

        stmt.execute(sql);
    }

    private static void insertOriginalData(Connection con) throws SQLException {
        String sql = "insert into " + tableName + " values( " + "?,?,?,?,?,?,?,?,?,?,?" + ")";
        try (PreparedStatement pstmt = con.prepareStatement(sql)) {
            pstmt.setObject(1, 100);
            pstmt.setObject(2, "original text");
            pstmt.setObject(3, "original text");
            pstmt.setObject(4, false);
            pstmt.setObject(5, 12.34);
            pstmt.setObject(6, 56.78);
            pstmt.setObject(7, new java.util.Date(1453500034839L));
            pstmt.setObject(8, new java.util.Date(1453500034839L));
            pstmt.setObject(9, new java.util.Date(1453500034839L));
            pstmt.setObject(10, new java.util.Date(1453500034839L));
            pstmt.setObject(11, new java.util.Date(1453500034839L));
            pstmt.execute();
        }
    }
}

```

## <a name="see-also"></a>См. также раздел

[Работа с типами данных (JDBC)](../../connect/jdbc/working-with-data-types-jdbc.md)
