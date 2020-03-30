---
title: Пример получения данных результирующего набора | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1b190c36-3d38-49a2-8599-612329675851
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2cca84ebc59bdefb43e2aa1a5f8b62bbf6301d51
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "69028375"
---
# <a name="retrieving-result-set-data-sample"></a>Пример получения данных результирующего набора

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

В этом образце приложения [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] показано получение набора данных из базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и последующее отображение этих данных.

Файл кода для этого примера с именем RetrieveResultSet.java находится в следующей папке:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\resultsets  
```

## <a name="requirements"></a>Требования

Чтобы запустить этот пример приложения, необходимо включить в параметр classpath путь к файлу mssql-jdbc.jar. Также потребуется доступ к примеру базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Дополнительные сведения о том, как настроить параметр classpath, см. в статье [Использование JDBC Driver](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Дополнительные сведения о выборе JAR-файла см. в описании [требований к системе для JDBC Driver](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Пример

В приведенном ниже примере образец кода будет использоваться для соединения с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Затем с помощью инструкции SQL с объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) выполняется инструкция SQL, а возвращенные ею данные помещаются в объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).

Далее пример кода вызывает настраиваемый метод displayRow для прохода по строкам данных в результирующем наборе, и некоторые из этих данных отображаются с помощью метода [getString](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md).

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
            createTable(stmt);
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

    private static void createTable(Statement stmt) throws SQLException {
        stmt.execute("if exists (select * from sys.objects where name = 'Product_JDBC_Sample')"
                + "drop table Product_JDBC_Sample");

        String sql = "CREATE TABLE [Product_JDBC_Sample](" + "[ProductID] [int] IDENTITY(1,1) NOT NULL,"
                + "[Name] [varchar](30) NOT NULL," + "[ProductNumber] [nvarchar](25) NOT NULL,"
                + "[MakeFlag] [bit] NOT NULL," + "[FinishedGoodsFlag] [bit] NOT NULL," + "[Color] [nvarchar](15) NULL,"
                + "[SafetyStockLevel] [smallint] NOT NULL," + "[ReorderPoint] [smallint] NOT NULL,"
                + "[StandardCost] [money] NOT NULL," + "[ListPrice] [money] NOT NULL," + "[Size] [nvarchar](5) NULL,"
                + "[SizeUnitMeasureCode] [nchar](3) NULL," + "[WeightUnitMeasureCode] [nchar](3) NULL,"
                + "[Weight] [decimal](8, 2) NULL," + "[DaysToManufacture] [int] NOT NULL,"
                + "[ProductLine] [nchar](2) NULL," + "[Class] [nchar](2) NULL," + "[Style] [nchar](2) NULL,"
                + "[ProductSubcategoryID] [int] NULL," + "[ProductModelID] [int] NULL,"
                + "[SellStartDate] [datetime] NOT NULL," + "[SellEndDate] [datetime] NULL,"
                + "[DiscontinuedDate] [datetime] NULL," + "[rowguid] [uniqueidentifier] ROWGUIDCOL  NOT NULL,"
                + "[ModifiedDate] [datetime] NOT NULL,)";

        stmt.execute(sql);

        sql = "INSERT Product_JDBC_Sample VALUES ('Adjustable Time','AR-5381','0','0',NULL,'1000','750','0.00','0.00',NULL,NULL,NULL,NULL,'0',NULL,NULL,NULL,NULL,NULL,'2008-04-30 00:00:00.000',NULL,NULL,'694215B7-08F7-4C0D-ACB1-D734BA44C0C8','2014-02-08 10:01:36.827') ";
        stmt.execute(sql);

        sql = "INSERT Product_JDBC_Sample VALUES ('ML Bottom Bracket','BB-8107','0','0',NULL,'1000','750','0.00','0.00',NULL,NULL,NULL,NULL,'0',NULL,NULL,NULL,NULL,NULL,'2008-04-30 00:00:00.000',NULL,NULL,'694215B7-08F7-4C0D-ACB1-D734BA44C0C8','2014-02-08 10:01:36.827') ";
        stmt.execute(sql);

        sql = "INSERT Product_JDBC_Sample VALUES ('Mountain-500 Black, 44','BK-M18B-44','0','0',NULL,'1000','750','0.00','0.00',NULL,NULL,NULL,NULL,'0',NULL,NULL,NULL,NULL,NULL,'2008-04-30 00:00:00.000',NULL,NULL,'694215B7-08F7-4C0D-ACB1-D734BA44C0C8','2014-02-08 10:01:36.827') ";
        stmt.execute(sql);
    }

    private static void displayRow(String title, ResultSet rs) {
        try {
            System.out.println(title);
            while (rs.next()) {
                System.out.println(rs.getString("ProductNumber") + " : " + rs.getString("Name"));
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

```

## <a name="see-also"></a>См. также раздел

[Работа с результирующими наборами](../../../connect/jdbc/code-samples/working-with-result-sets.md)
