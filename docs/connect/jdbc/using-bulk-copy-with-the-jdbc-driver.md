---
title: Использование массового копирования с помощью JDBC Driver | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 21e19635-340d-49bb-b39d-4867102fb5df
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 75ee40e0b7ca753efd32e0ab057340f61824acef
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "79286508"
---
# <a name="using-bulk-copy-with-the-jdbc-driver"></a>Использование массового копирования с помощью JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Microsoft SQL Server включает популярную служебную программу командной строки **bcp**, позволяющую быстро выполнять массовое копирование больших файлов в таблицы или представления баз данных SQL Server. Класс SQLServerBulkCopy позволяет создавать решения на языке Java, которые предоставляют аналогичные возможности. Существуют другие способы загрузки данных в таблицу SQL Server (например, с помощью инструкции INSERT), но SQLServerBulkCopy делает это значительно быстрее.  
  
Класс SQLServerBulkCopy можно использовать для записи данных только в таблицы SQL Server. Но источником данных может быть не только SQL Server, а любой источник данных, если данные можно считать с помощью реализации ResultSet, RowSet или ISQLServerBulkRecord.  
  
С помощью класса SQLServerBulkCopy вы можете выполнить:  
  
- одну операцию массового копирования;  
  
- несколько операций массового копирования;  
  
- операцию массового копирования с транзакцией.  
  
> [!NOTE]  
> При использовании драйвера Microsoft JDBC 4.1 для SQL Server или более ранней версии (которая не поддерживает класс SQLServerBulkCopy) вместо него можно воспользоваться инструкцией SQL Server Transact-SQL BULK INSERT.  
  
## <a name="bulk-copy-example-setup"></a>Пример настройки массового копирования  

Класс SQLServerBulkCopy можно использовать для записи данных только в таблицы SQL Server. В примерах кода в этой статье используется пример базы данных SQL Server с именем AdventureWorks. Чтобы не допустить изменения существующих таблиц, примеры кода записывают данные в таблицы, которые сначала необходимо создать.  
  
Таблицы BulkCopyDemoMatchingColumns и BulkCopyDemoDifferentColumns основаны на таблице AdventureWorks Production.Products. В примерах кода, использующих эти таблицы, данные из таблицы Production.Products добавляются к одной из этих таблиц-образцов. Таблица BulkCopyDemoDifferentColumns используется для демонстрации сопоставления столбцов из источника данных с целевой таблицей. Таблица BulkCopyDemoMatchingColumns используется в большинстве других примеров.  
  
Некоторые примеры кода демонстрируют использование одного класса SQLServerBulkCopy для записи в несколько таблиц. В этих примерах в качестве целевых таблиц применяются BulkCopyDemoOrderHeader и BulkCopyDemoOrderDetail. Эти таблицы основаны на таблицах Sales.SalesOrderHeader и Sales.SalesOrderDetail из базы данных AdventureWorks.  
  
> [!NOTE]  
> Примеры кода SQLServerBulkCopy предназначены только для демонстрации синтаксиса использования SQLServerBulkCopy. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL INSERT ... Инструкция SELECT для копирования данных.  

### <a name="table-setup"></a>Настройка таблицы  

Чтобы создать таблицы, необходимые для правильной работы примеров кода, выполните следующие инструкции Transact-SQL в базе данных SQL Server.  

```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobject
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
```

## <a name="single-bulk-copy-operations"></a>Одинарные операции массового копирования

Самый простой способ массового копирования SQL Server — выполнение одной операции в базе данных. По умолчанию операция массового копирования выполняется как изолированная, т. е. не как транзакция и без возможности отката.  
  
> [!NOTE]  
> Если при возникновении ошибки необходимо частично или полностью отменить массовое копирование, можно использовать управляемую SQLServerBulkCopy транзакцию или выполнить операцию массового копирования в существующей транзакции.  
> Дополнительные сведения см. в статье [Транзакции и операции массового копирования](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#transaction-and-bulk-copy-operations).  
  
 Для массового копирования выполните следующие действия.  
  
1. Подключитесь к исходному серверу и получите данные для копирования. Данные также могут поступать из других источников, если их можно извлечь из объекта ResultSet или реализации ISQLServerBulkRecord.  
  
2. Подключитесь к целевому серверу (если не хотите, чтобы **SQLServerBulkCopy** установил соединение автоматически).  
  
3. Создайте объект SQLServerBulkCopy, задав необходимые свойства с помощью **setBulkCopyOptions**.  
  
4. Вызовите метод **setDestinationTableName**, чтобы указать целевую таблицу для операции массовой вставки.  
  
5. Вызовите один из методов **writeToServer**.  
  
6. При необходимости обновите свойства с помощью **setBulkCopyOptions** и вызовите **writeToServer** еще раз.  
  
7. Вызовите **close** или заключите код операций массового копирования в инструкцию "try-with-resources".  
  
> [!CAUTION]  
> Мы рекомендуем, чтобы исходные и целевые типы данных столбцов совпадали. Если типы данных не совпадают, SQLServerBulkCopy попытается преобразовать каждое исходное значение в целевой тип данных. Преобразование может повлиять на производительность и может привести к непредвиденным ошибкам. Например, в большинстве случаев тип данных double может преобразовываться в тип данных decimal, но это происходит не всегда.  
  
### <a name="example"></a>Пример

Следующее приложение показывает, как загрузить данные с помощью класса SQLServerBulkCopy. В этом примере ResultSet используется для копирования данных из таблицы Production.Product в базе данных AdventureWorks в аналогичную таблицу в той же базе данных.  
  
> [!IMPORTANT]  
> Этот пример не будет работать, если вы не создали рабочие таблицы, как описано в разделе [Настройка таблиц](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#table-setup). Этот пример кода предназначен только для демонстрации синтаксиса использования SQLServerBulkCopy. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL INSERT ... Инструкция SELECT для копирования данных.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;

public class BulkCopySingle {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;
        ResultSet rsSourceData;

        try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
                Connection destinationConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(destinationConnection)) {

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Get data from the source table as a ResultSet.
            rsSourceData = stmt.executeQuery("SELECT ProductID, Name, ProductNumber FROM Production.Product");

            // In real world applications you would
            // not use SQLServerBulkCopy to move data from one table to the other
            // in the same database. This is for demonstration purposes only.

            // Set up the bulk copy object.
            // Note that the column positions in the source
            // table match the column positions in
            // the destination table so there is no need to
            // map columns.
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            bulkCopy.writeToServer(rsSourceData);

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

### <a name="performing-a-bulk-copy-operation-using-transact-sql"></a>Выполнение операции массового копирования с помощью Transact-SQL

Следующий пример демонстрирует использование метода executeUpdate для выполнения инструкции BULK INSERT.  
  
> [!NOTE]  
> Путь к источнику данных указан относительно сервера. Для успешного выполнения массового копирования у процесса сервера должен быть доступ к этому пути.  

```java
try (Connection con = DriverManager.getConnection(connectionUrl);
        Statement stmt = con.createStatement()) {
    // Perform the BULK INSERT
    stmt.executeUpdate(
            "BULK INSERT Northwind.dbo.[Order Details] " + "FROM 'f:\\mydata\\data.tbl' " + "WITH ( FORMATFILE='f:\\mydata\\data.fmt' )");
}
```  

## <a name="multiple-bulk-copy-operations"></a>несколько операций массового копирования;  

Вы можете выполнить несколько операций массового копирования, используя один экземпляр класса SQLServerBulkCopy. Если между копированиями параметры операции изменяются (например, имя целевой таблицы), необходимо обновить их до последующих вызовов методов writeToServer, как показано в следующем примере. Если значения свойств не изменяются явным образом, все они остаются такими же, как при предыдущей операции массового копирования для данного экземпляра.  

> [!NOTE]  
> Выполнение нескольких операций массового копирования с использованием одного экземпляра SQLServerBulkCopy обычно более эффективно, чем использование отдельного экземпляра для каждой операции.  
  
При выполнении нескольких операций массового копирования с одним объектом SQLServerBulkCopy не существует ограничений, касающихся совпадения или различий целевой информации в каждой операции. Однако для каждой записи на сервер необходимо убедиться, что связи столбцов настроены правильно.  
  
> [!IMPORTANT]  
> Этот пример не будет работать, если вы не создали рабочие таблицы, как описано в разделе [Настройка таблиц](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#table-setup). Этот пример кода предназначен только для демонстрации синтаксиса использования SQLServerBulkCopy. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL INSERT ... Инструкция SELECT для копирования данных.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;

public class BulkCopyMultiple {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationHeaderTable = "dbo.BulkCopyDemoOrderHeader";
        String destinationDetailTable = "dbo.BulkCopyDemoOrderDetail";
        int countHeaderBefore, countDetailBefore, countHeaderAfter, countDetailAfter;
        ResultSet rsHeader, rsDetail;

        try (Connection sourceConnection1 = DriverManager.getConnection(connectionUrl);
                Connection sourceConnection2 = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection1.createStatement();
                PreparedStatement preparedStmt1 = sourceConnection1.prepareStatement(
                        "SELECT [SalesOrderID], [OrderDate], [AccountNumber] FROM [Sales].[SalesOrderHeader] WHERE [AccountNumber] = ?;");
                PreparedStatement preparedStmt2 = sourceConnection2.prepareStatement(
                        "SELECT [Sales].[SalesOrderDetail].[SalesOrderID], [SalesOrderDetailID], [OrderQty], [ProductID], [UnitPrice] FROM "
                                + "[Sales].[SalesOrderDetail] INNER JOIN [Sales].[SalesOrderHeader] ON "
                                + "[Sales].[SalesOrderDetail].[SalesOrderID] = [Sales].[SalesOrderHeader].[SalesOrderID] WHERE [AccountNumber] = ?;");
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(connectionUrl);) {

            // Empty the destination tables.
            stmt.executeUpdate("DELETE FROM " + destinationHeaderTable);
            stmt.executeUpdate("DELETE FROM " + destinationDetailTable);

            // Perform an initial count on the destination
            // table with matching columns.
            countHeaderBefore = getRowCount(stmt, destinationHeaderTable);

            // Perform an initial count on the destination
            // table with different column positions.
            countDetailBefore = getRowCount(stmt, destinationDetailTable);

            // Get data from the source table as a ResultSet.
            // The Sales.SalesOrderHeader and Sales.SalesOrderDetail
            // tables are quite large and could easily cause a timeout
            // if all data from the tables is added to the destination.
            // To keep the example simple and quick, a parameter is
            // used to select only orders for a particular account
            // as the source for the bulk insert.
            preparedStmt1.setString(1, "10-4020-000034");
            rsHeader = preparedStmt1.executeQuery();

            // Get the Detail data in a separate connection.
            preparedStmt2.setString(1, "10-4020-000034");
            rsDetail = preparedStmt2.executeQuery();

            // Create the SQLServerBulkCopySQLServerBulkCopy object.
            SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();
            copyOptions.setBulkCopyTimeout(100);
            bulkCopy.setBulkCopyOptions(copyOptions);
            bulkCopy.setDestinationTableName(destinationHeaderTable);

            // Guarantee that columns are mapped correctly by
            // defining the column mappings for the order.
            bulkCopy.addColumnMapping("SalesOrderID", "SalesOrderID");
            bulkCopy.addColumnMapping("OrderDate", "OrderDate");
            bulkCopy.addColumnMapping("AccountNumber", "AccountNumber");

            // Write rsHeader to the destination.
            bulkCopy.writeToServer(rsHeader);

            // Set up the order details destination.
            bulkCopy.setDestinationTableName(destinationDetailTable);

            // Clear the existing column mappings
            bulkCopy.clearColumnMappings();

            // Add order detail column mappings.
            bulkCopy.addColumnMapping("SalesOrderID", "SalesOrderID");
            bulkCopy.addColumnMapping("SalesOrderDetailID", "SalesOrderDetailID");
            bulkCopy.addColumnMapping("OrderQty", "OrderQty");
            bulkCopy.addColumnMapping("ProductID", "ProductID");
            bulkCopy.addColumnMapping("UnitPrice", "UnitPrice");

            // Write rsDetail to the destination.
            bulkCopy.writeToServer(rsDetail);

            // Perform a final count on the destination
            // tables to see how many rows were added.
            countHeaderAfter = getRowCount(stmt, destinationHeaderTable);
            countDetailAfter = getRowCount(stmt, destinationDetailTable);

            System.out.println((countHeaderAfter - countHeaderBefore) + " rows were added to the Header table.");
            System.out.println((countDetailAfter - countDetailBefore) + " rows were added to the Detail table.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

## <a name="transaction-and-bulk-copy-operations"></a>Транзакции и операции массового копирования

 Операции массового копирования могут выполняться как изолированные операции или как часть многошаговой транзакции. В последнем случае вы можете выполнить более одной операции массового копирования в одной транзакции, а также выполнять другие операции с базами данных (такие как вставка, обновление и удаление) с возможностью фиксации или отката всей транзакции.  
  
 По умолчанию операция массового копирования выполняется как изолированная. Операция массового копирования выполняется не как транзакция и без возможности отката. Если при возникновении ошибки необходимо частично или полностью отменить массовое копирование, можно использовать управляемую SQLServerBulkCopy транзакцию или выполнить операцию массового копирования в существующей транзакции.  
  
### <a name="performing-a-non-transacted-bulk-copy-operation"></a>Выполнение операции массового копирования без транзакции

Следующее приложение показывает, что происходит, когда во время операции массового копирования без транзакции возникает ошибка.  
  
В этом примере исходная и целевая таблицы содержат столбец идентификаторов с именем **ProductID**. Сначала код подготавливает целевую таблицу, удаляя все строки и вставляя одну строку, у которой **ProductID** точно существует в исходной таблице. По умолчанию в целевой таблице для каждой добавляемой строки создается новое значение столбца идентификаторов. В этом примере при открытии соединения задается параметр, заставляющий процесс массовой загрузки использовать значения идентификаторов из исходной таблицы.  
  
Операция массового копирования выполняется со свойством **BatchSize**, равным 10. Когда операция встречает недопустимую строку, вызывается исключение. В первом примере операция массового копирования выполняется без транзакции. Фиксируются все пакеты, скопированные до появления ошибки. Пакет, содержащий повторяющийся ключ, откатывается, а операция массового копирования прерывается до обработки любых других пакетов.  
  
> [!NOTE]  
> Этот пример не будет работать, если вы не создали рабочие таблицы, как описано в разделе [Настройка таблиц](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#table-setup). Этот пример кода предназначен только для демонстрации синтаксиса использования SQLServerBulkCopy. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL INSERT ... Инструкция SELECT для копирования данных.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;

public class BulkCopyNonTransacted {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;
        ResultSet rsSourceData;

        try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(connectionUrl)) {

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Add a single row that will result in duplicate key
            // when all rows from source are bulk copied.
            // Note that this technique will only be successful in
            // illustrating the point if a row with ProductID = 446
            // exists in the AdventureWorks Production.Products table.
            // If you have made changes to the data in this table, change
            // the SQL statement in the code to add a ProductID that
            // does exist in your version of the Production.Products
            // table. Choose any ProductID in the middle of the table
            // (not first or last row) to best illustrate the result.
            stmt.executeUpdate("SET IDENTITY_INSERT " + destinationTable + " ON;" + "INSERT INTO " + destinationTable
                    + "([ProductID], [Name] ,[ProductNumber]) VALUES(446, 'Lock Nut 23','LN-3416'); SET IDENTITY_INSERT " + destinationTable
                    + " OFF");

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Get data from the source table as a ResultSet.
            rsSourceData = stmt.executeQuery("SELECT ProductID, Name, ProductNumber FROM Production.Product");

            // Set up the bulk copy object using the KeepIdentity option and BatchSize = 10.
            SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();
            copyOptions.setKeepIdentity(true);
            copyOptions.setBatchSize(10);

            bulkCopy.setBulkCopyOptions(copyOptions);
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            // This should fail with a duplicate key error
            // after some of the batches have been copied.
            try {
                bulkCopy.writeToServer(rsSourceData);
            }
            catch (SQLException e) {
                e.printStackTrace();
            }

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

### <a name="performing-a-dedicated-build-copy-operation-in-a-transaction"></a>Выполнение выделенной операции массового копирования в транзакции 

По умолчанию операция массового копирования является своей собственной транзакцией. Если вы хотите выполнить выделенную операцию массового копирования, создайте новый экземпляр SQLServerBulkCopy со строкой подключения. В этом случае операция массового копирования создает и затем фиксирует или откатывает транзакцию. Вы можете явно указать параметр **UseInternalTransaction** в **SQLServerBulkCopyOptions**, чтобы в явном виде заставить операцию массового копирования выполняться в своей собственной транзакции, вследствие чего каждый пакет операции будет выполняться в отдельной транзакции.  
  
> [!NOTE]  
> Поскольку разные пакеты выполняются в разных транзакциях, если во время операции массового копирования возникает ошибка, для всех строк в текущем пакете будет выполнен откат, но строки из предыдущих пакетов останутся в базе данных.  
  
При указании параметра **UseInternalTransaction** в **BulkCopyNonTransacted** операция массового копирования включается в большую, внешнюю транзакцию. Если возникает ошибка нарушения первичного ключа, производится откат всей транзакции и никакие строки не добавляются в целевую таблицу.

```java
SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();
copyOptions.setKeepIdentity(true);
copyOptions.setBatchSize(10);
copyOptions.setUseInternalTransaction(true);
```

### <a name="using-existing-transactions"></a>Использование существующих транзакций

Вы можете передать объект Connection с включенными транзакциями в качестве параметра конструктора SQLServerBulkCopy. В этом случае операция массового копирования выполняется в существующей транзакции, а состояние транзакции не изменяется (то есть она не фиксируется и не прерывается). Это позволяет приложению включить операцию массового копирования в транзакцию с другими операциями базы данных. Если необходимо выполнить откат всей операции массового копирования из-за ошибки или если массовое копирование должно выполняться как часть большего процесса, который может быть отменен, можно выполнить откат в объекте Connection в любой момент после массового копирования.  
  
Следующее приложение похоже на **BulkCopyNonTransacted** с одним исключением: в этом примере операция массового копирования включена в большую, внешнюю транзакцию. Если возникает ошибка нарушения первичного ключа, производится откат всей транзакции и никакие строки не добавляются в целевую таблицу.

> [!NOTE]  
> Этот пример не будет работать, если вы не создали рабочие таблицы, как описано в разделе [Настройка таблиц](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#table-setup). Этот пример кода предназначен только для демонстрации синтаксиса использования SQLServerBulkCopy. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL INSERT ... Инструкция SELECT для копирования данных.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;

public class BulkCopyExistingTransactions {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;
        ResultSet rsSourceData;
        SQLServerBulkCopyOptions copyOptions;

        try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
                Connection destinationConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = sourceConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(destinationConnection);) {

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Add a single row that will result in duplicate key
            // when all rows from source are bulk copied.
            // Note that this technique will only be successful in
            // illustrating the point if a row with ProductID = 446
            // exists in the AdventureWorks Production.Products table.
            // If you have made changes to the data in this table, change
            // the SQL statement in the code to add a ProductID that
            // does exist in your version of the Production.Products
            // table. Choose any ProductID in the middle of the table
            // (not first or last row) to best illustrate the result.
            stmt.executeUpdate("SET IDENTITY_INSERT " + destinationTable + " ON;" + "INSERT INTO " + destinationTable
                    + "([ProductID], [Name] ,[ProductNumber]) VALUES(446, 'Lock Nut 23','LN-3416'); SET IDENTITY_INSERT " + destinationTable
                    + " OFF");

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Get data from the source table as a ResultSet.
            rsSourceData = stmt.executeQuery("SELECT ProductID, Name, ProductNumber FROM Production.Product");

            // Set up the bulk copy object inside the transaction.
            destinationConnection.setAutoCommit(false);

            copyOptions = new SQLServerBulkCopyOptions();
            copyOptions.setKeepIdentity(true);
            copyOptions.setBatchSize(10);

            bulkCopy.setBulkCopyOptions(copyOptions);
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            // This should fail with a duplicate key error.
            try {
                bulkCopy.writeToServer(rsSourceData);
                destinationConnection.commit();
            }
            catch (SQLException e) {
                e.printStackTrace();
            }

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        catch (Exception e) {
            // Handle any errors that may have occurred.
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```

### <a name="bulk-copy-from-a-csv-file"></a>Массовое копирование из CSV-файла  

 Следующее приложение показывает, как загрузить данные с помощью класса SQLServerBulkCopy. В этом примере CSV-файл используется для копирования данных, экспортированных из таблицы Production.Product в базе данных AdventureWorks, в аналогичную таблицу в той же базе данных.  
  
> [!IMPORTANT]  
> Этот пример не будет работать, если вы не создали рабочие таблицы, как описано в разделе [Настройка таблиц](../../ssms/download-sql-server-management-studio-ssms.md).  
  
1. Откройте**SQL Server Management Studio** и подключитесь к SQL Server с базой данных AdventureWorks.  
  
2. Разверните базы данных, щелкните правой кнопкой мыши базу данных AdventureWorks, выберите **Задачи** и **Экспорт данных**.  
  
3. Выберите **Источник данных**, который позволяет подключиться к SQL Server (например, SQL Server Native Client 11.0), проверьте конфигурацию и нажмите **Далее**  
  
4. Выберите **назначение "Неструктурированный файл"** и введите **Имя файла** с путем назначения, например: C:\Test\TestBulkCSVExample.csv. Задайте значения **Формат** — "С разделителями" и **Ограничитель текста** — "Нет", установите флажок **Имена столбцов в первой строке данных** и нажмите **Далее**  
  
5. Установите флажок **Написать запрос, указывающий данные для передачи** и вновь нажмите **Далее**.  Введите **SQL-инструкцию** "SELECT ProductID, Name, ProductNumber FROM Production.Product" и снова щелкните **Далее**.  
  
6. Проверьте конфигурацию. Можно оставить разделитель строк {CR}{LF} и разделитель столбцов — запятую {,}.  Выберите **Изменить сопоставления**… и проверьте **Тип** данных для каждого столбца (например, целое число для ProductID и строка Юникода для других столбцов).  
  
7. Нажмите **Готово** и запустите экспорт.  

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerBulkCSVFileRecord;
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;

public class BulkCopyCSV {
    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";
        String destinationTable = "dbo.BulkCopyDemoMatchingColumns";
        int countBefore, countAfter;

        // Get data from the source file by loading it into a class that implements ISQLServerBulkRecord.
        // Here we are using the SQLServerBulkCSVFileRecord implementation to import the example CSV file.
        try (Connection destinationConnection = DriverManager.getConnection(connectionUrl);
                Statement stmt = destinationConnection.createStatement();
                SQLServerBulkCopy bulkCopy = new SQLServerBulkCopy(destinationConnection);
                SQLServerBulkCSVFileRecord fileRecord = new SQLServerBulkCSVFileRecord("C:\\Test\\TestBulkCSVExample.csv", true);) {

            // Set the metadata for each column to be copied.
            fileRecord.addColumnMetadata(1, null, java.sql.Types.INTEGER, 0, 0);
            fileRecord.addColumnMetadata(2, null, java.sql.Types.NVARCHAR, 50, 0);
            fileRecord.addColumnMetadata(3, null, java.sql.Types.NVARCHAR, 25, 0);

            // Empty the destination table.
            stmt.executeUpdate("DELETE FROM " + destinationTable);

            // Perform an initial count on the destination table.
            countBefore = getRowCount(stmt, destinationTable);

            // Set up the bulk copy object.
            // Note that the column positions in the source
            // data reader match the column positions in
            // the destination table so there is no need to
            // map columns.
            bulkCopy.setDestinationTableName(destinationTable);

            // Write from the source to the destination.
            bulkCopy.writeToServer(fileRecord);

            // Perform a final count on the destination
            // table to see how many rows were added.
            countAfter = getRowCount(stmt, destinationTable);
            System.out.println((countAfter - countBefore) + " rows were added.");
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static int getRowCount(Statement stmt,
            String tableName) throws SQLException {
        ResultSet rs = stmt.executeQuery("SELECT COUNT(*) FROM " + tableName);
        rs.next();
        int count = rs.getInt(1);
        rs.close();
        return count;
    }
}
```  

### <a name="bulk-copy-with-always-encrypted-columns"></a>Использование массового копирования со столбцами Always Encrypted  

Начиная с версии Microsoft JDBC Driver 6.0 для SQL Server массовое копирование поддерживается для столбцов, зашифрованных с помощью Always Encrypted.  
  
В зависимости от параметров массового копирования, а также типа шифрования исходной и конечной таблиц драйвер JDBC может осуществлять прозрачное шифрование данных с последующей расшифровкой либо отправлять зашифрованные данные "как есть". Например, при массовом копировании данных из зашифрованного столбца в незашифрованный драйвер прозрачным образом расшифровывает данные перед их отправкой в SQL Server. Аналогичным образом, при массовом копировании данных из незашифрованного столбца (или из файла CSV) в зашифрованный драйвер прозрачным образом зашифровывает данные перед их отправкой в SQL Server. Если зашифрованы и исходный и конечный столбец, то в зависимости от значения параметра массового копирования **allowEncryptedValueModifications** драйвер будет отправлять данные "как есть" или расшифровывать данные, а затем снова зашифровывать их перед отправкой в SQL Server.  
  
Дополнительные сведения см. в описании параметра массового копирования **allowEncryptedValueModifications** ниже и в статье [Использование функции Always Encrypted с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!IMPORTANT]  
> При использовании Microsoft JDBC Driver 6.0 для SQL Server с целью массового копирования данных из файла CSV в зашифрованные столбцы действуют указанные ниже ограничения.  
>
> Для типов даты и времени поддерживается только формат строковых литералов Transact-SQL по умолчанию.  
>
> Типы данных DATETIME и SMALLDATETIME не поддерживаются.  
  
## <a name="bulk-copy-api-for-jdbc-driver"></a>Массовое копирование API для драйвера JDBC  
  
### <a name="sqlserverbulkcopy"></a>SQLServerBulkCopy 

Позволяет эффективно выполнять массовую загрузку таблицы SQL Server с данными из другого источника.  
  
Microsoft SQL Server включает популярную программу командной строки bcp, используемую для перемещения данных из одной таблицы в другую как на одном сервере, так и между серверами. Класс SQLServerBulkCopy позволяет создавать решения на языке Java, которые предоставляют аналогичные возможности. Существуют другие способы загрузки данных в таблицу SQL Server (например, с помощью инструкции INSERT), но SQLServerBulkCopy делает это значительно быстрее.  
  
Класс SQLServerBulkCopy можно использовать для записи данных только в таблицы SQL Server. Но источником данных может быть не только SQL Server, а любой источник данных, если данные можно считать с помощью экземпляра ResultSet или реализации ISQLServerBulkRecord.  
  
| Конструктор                             | Описание                                                                                                                                                                                                                    |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| SQLServerBulkCopy(Connection)           | Инициализирует новый экземпляр класса SQLServerBulkCopy, используя указанный открытый экземпляр SQLServerConnection. Если для объекта Connection включены транзакции, операции копирования будут выполняться в контексте этой транзакции. |
| SQLServerBulkCopy(String connectionURL) | Инициализирует и открывает новый экземпляр SQLServerConnection на основе предоставленного URL-адреса подключения (connectionURL). Конструктор использует SQLServerConnection для инициализации нового экземпляра класса SQLServerBulkCopy.                     |
  
| Свойство                    | Описание                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| String DestinationTableName | Имя целевой таблицы на сервере.<br /><br /> Если имя DestinationTableName не было задано при вызове writeToServer, вызывается исключение SQLServerException.<br /><br /> Имя DestinationTableName состоит из трех компонентов (\<база данных>.\<схема-владелец>.\<имя>). При необходимости можно уточнить имя таблицы с помощью указания базы данных и схемы-владельца. Но если имя таблицы содержит символ подчеркивания («_») или другие специальные символы, необходимо заключить имя в скобки. Дополнительные сведения см. в разделе «Идентификаторы» в электронной документации по SQL Server. |
| ColumnMappings              | Сопоставления столбцов определяют связи между столбцами в источнике данных и столбцами в месте назначения.<br /><br /> Если сопоставления не определены, столбцы сопоставляются неявно по порядковому номеру. При этом исходная и целевая схемы должны совпадать. Иначе будет вызвано исключение.<br /><br /> Если сопоставления не пусты, не обязательно задавать все столбцы, присутствующие в источнике данных. Несопоставленные столбцы будут проигнорированы.<br /><br /> Обращаться к исходным и целевым столбцам можно по имени или порядковому номеру.               |
  
| Метод                                                                | Описание                                                                                                                                                                |
| --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Void addColumnMapping((int sourceColumn, int destinationColumn)       | Добавляет новое сопоставление столбцов, используя порядковые номера исходного и целевого столбцов.                                                                                  |
| Void addColumnMapping ((int sourceColumn, String destinationColumn)   | Добавляет новое сопоставление столбцов, используя порядковый номер исходного столбца и имя целевого столбца.                                                            |
| Void addColumnMapping ((String sourceColumn, int destinationColumn)   | Добавляет новое сопоставление столбцов, используя имя исходного столбца и порядковый номер целевого столбца.                                             |
| Void addColumnMapping (String sourceColumn, String destinationColumn) | Добавляет новое сопоставление столбцов, используя имена исходного и целевого столбцов.                                                                              |
| Void clearColumnMappings()                                            | Очищает содержимое сопоставления столбцов.                                                                                                                                |
| Void close()                                                          | Закрывает экземпляр SQLServerBulkCopy.                                                                                                                                     |
| SQLServerBulkCopyOptions getBulkCopyOptions()                         | Получает текущий набор SQLServerBulkCopyOptions.                                                                                                                     |
| String getDestinationTableName()                                      | Получает имя текущей целевой таблицы.                                                                                                                               |
| Void setBulkCopyOptions(SQLServerBulkCopyOptions copyOptions)         | Обновляет экземпляр SQLServerBulkCopy в соответствии с предоставленными параметрами.                                                                                  |
| Void setDestinationTableName(String tableName)                        | Задает имя целевой таблицы.                                                                                                                                    |
| Void writeToServer(ResultSet sourceData)                              | Копирует все строки в предоставленном результирующем наборе ResultSet в целевую таблицу, указанную в свойстве DestinationTableName объекта SQLServerBulkCopy.                           |
| Void writeToServer(RowSet sourceData)                                 | Копирует все строки в предоставленном наборе строк RowSet в целевую таблицу, указанную в свойстве DestinationTableName объекта SQLServerBulkCopy.                              |
| Void writeToServer(ISQLServerBulkRecord sourceData)                   | Копирует все строки в предоставленной реализации ISQLServerBulkRecord в целевую таблицу, указанную в свойстве DestinationTableName объекта SQLServerBulkCopy. |
  
### <a name="sqlserverbulkcopyoptions"></a>SQLServerBulkCopyOptions  

 Коллекция параметров, которые управляют поведением методов writeToServer в экземпляре SQLServerBulkCopy.  
  
| Конструктор                | Описание                                                                                              |
| -------------------------- | -------------------------------------------------------------------------------------------------------- |
| SQLServerBulkCopyOptions() | Инициализирует новый экземпляр класса SQLServerBulkCopyOptions, используя для всех параметров значения по умолчанию. |
  
 Методы get и set существуют для следующих параметров.  
  
| Параметр                                   | Описание                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | По умолчанию                                                              |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Boolean CheckConstraints                 | Проверка ограничений при вставке данных.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | False — ограничения не проверяются.                                   |
| Boolean FireTriggers                     | Если этот параметр указан, сервер выполняет триггеры вставки для строк, вставляемых в базу данных.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | False — триггеры не выполняются.                                        |
| Boolean KeepIdentity                     | Сохранять идентификационные значения источника.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | False — значения идентификаторов назначаются целевым объектом.              |
| Boolean KeepNulls                        | Сохранять значения null в целевой таблице независимо от значений параметров по умолчанию.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | False — значения null заменяются значениями по умолчанию, где это применимо. |
| Boolean TableLock                        | Применить блокировку массового обновления на время операции массового копирования.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | False — блокировки строк используются.                                          |
| Boolean UseInternalTransaction           | Если этот параметр указан, каждый пакет операции массового копирования будет выполняться в рамках транзакции. Если SQLServerBulkCopy использует существующее подключение (как указано конструктором), вызывается исключение SQLServerException.  Если объект SQLServerBulkCopy создал выделенное соединение, транзакция будет разрешена.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | False — транзакция отсутствует.                                               |
| Int BatchSize                            | Количество строк в каждом пакете. В конце каждого пакета строки из пакета передаются на сервер.<br /><br /> Пакет завершается, когда число обработанных строк равно BatchSize или отсутствуют строки для отправки в целевой источник данных.  Если экземпляр SQLServerBulkCopy объявлен без параметра UseInternalTransaction, на сервер передается число строк, равное BatchSize, но не выполняются никакие действия, связанные с транзакциями. Если параметр UseInternalTransaction включен, каждый пакет строк вставляется как отдельная транзакция.                                                                                                                                                                                                                                                                                                                                                                                                                                           | Значение 0 указывает, что каждая операция writeToServer представляет один пакет.    |
| Int BulkCopyTimeout                      | Время выполнения операции до истечения времени ожидания в секундах. Значение 0 означает отсутствие ограничений; операция массового копирования будет находиться в ожидании бесконечно долго.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 60 секунд.                                                          |
| Boolean allowEncryptedValueModifications | Этот параметр доступен в Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server.<br /><br /> Если параметр **allowEncryptedValueModifications** указан, разрешается массовое копирование зашифрованных данных между таблицами или базами данных без их расшифровки. Как правило, приложение выбирает данные из зашифрованных столбцов в одной таблице, не расшифровывая их (для подключения к базе данных используется ключевое слово Column Encryption Setting со значением Disabled), а затем с помощью этого параметра выполняет массовую вставку данных, которые по-прежнему зашифрованы. Дополнительные сведения: [Использование функции Always Encrypted с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).<br /><br /> Используйте параметр **allowEncryptedValueModifications** с осторожностью. Драйвер не проверяет, являются ли данные зашифрованными и используется ли при шифровании тот же тип, алгоритм и ключ шифрования, что у целевого столбца. Поэтому изменение значений может повредить целевую базу данных. |
  
 Методы получения и методы задания:  
  
| Методы                                                                            | Описание                                                                                                                                                                               |
| ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Boolean isCheckConstraints()                                                       | Показывает, должны ли проверяться ограничения при вставке данных.                                                                                                      |
| Void setCheckConstraints(Boolean checkConstraints)                                 | Определяет, должны ли проверяться ограничения при вставке данных.                                                                                                           |
| Boolean isFireTriggers()                                                           | Показывает, должен ли сервер выполнять триггеры вставки для строк, вставляемых в базу данных.                                                                                    |
| Void setFireTriggers(Boolean fireTriggers)                                         | Определяет, должен ли сервер выполнять триггеры вставки для строк, вставляемых в базу данных.                                                                                     |
| Boolean isKeepIdentity()                                                           | Показывает, должны ли сохраняться исходные значения идентификаторов.                                                                                                                          |
| Void setKeepIdentity(Boolean keepIdentity)                                         | Определяет, должны ли сохраняться значения идентификаторов.                                                                                                                                          |
| Boolean isKeepNulls()                                                              | Показывает, должны ли сохраняться значения NULL в конечной таблице независимо от значений параметров по умолчанию или они должны заменяться значениями по умолчанию (если это возможно). |
| Void setKeepNulls(Boolean keepNulls)                                               | Определяет, должны ли сохраняться значения NULL в конечной таблице независимо от значений параметров по умолчанию или они должны заменяться значениями по умолчанию (если это возможно).      |
| Boolean isTableLock()                                                              | Показывает, должен ли объект SQLServerBulkCopy получать блокировку массового изменения на время операции массового копирования.                                                                         |
| Void setTableLock(Boolean tableLock)                                               | Определяет, должен ли объект SQLServerBulkCopy получать блокировку массового изменения на время операции массового копирования.                                                                              |
| Boolean isUseInternalTransaction()                                                 | Указывает, должен ли каждый пакет операции массового копирования выполняться в рамках транзакции.                                                                                                  |
| Void setUseInternalTranscation(Boolean useInternalTransaction)                     | Указывает, должен ли каждый пакет операции массового копирования выполняться в рамках транзакции.                                                                                               |
| Int getBatchSize()                                                                 | Получает число строк в каждом пакете. По окончании каждого пакета его строки отправляются на сервер                                                                             |
| Void setBatchSize(int batchSize)                                                   | Задает число строк в каждом пакете. В конце каждого пакета строки из пакета передаются на сервер.                                                                            |
| Int getBulkCopyTimeout()                                                           | Получает время выполнения операции до истечения времени ожидания, в секундах.                                                                                                             |
| Void setBulkCopyTimeout(int timeout)                                              | Задает время выполнения операции до истечения времени ожидания, в секундах.                                                                                                             |
| boolean isAllowEncryptedValueModifications()                                       | Показывает, включен ли параметр allowEncryptedValueModifications.                                                                                                        |
| void setAllowEncryptedValueModifications(boolean allowEncryptedValueModifications) | Настраивает параметр allowEncryptedValueModifications, используемый для массового копирования столбцов Always Encrypted.                                                                         |
  
### <a name="isqlserverbulkrecord"></a>ISQLServerBulkRecord  

 Интерфейс ISQLServerBulkRecord можно использовать для создания классов, которые считывают данные из любого источника (например, файла), чтобы позволить экземпляру SQLServerBulkCopy выполнить массовую загрузку данных таблицы SQL Server.  
  
| Методы интерфейса                   | Описание                                                                                                                                                                                                                                                                                            |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Set\<целое число> getColumnOrdinals()   | Получение порядковых номеров столбцов, представленных в этой записи данных.                                                                                                                                                                                                                              |
| String getColumnName(int column)    | Получение имени заданного столбца.                                                                                                                                                                                                                                                                      |
| Int getColumnType(int column)       | Получение типа данных JDBC заданного столбца.                                                                                                                                                                                                                                                            |
| Int getPrecision(int column)        | Получение точности для данного столбца.                                                                                                                                                                                                                                                                |
| Object[] getRowData()               | Возвращает данные для текущей строки как массив объектов.<br /><br /> Тип каждого объекта должен соответствовать типу Java, используемому для представления указанного типа данных JDBC этого столбца.  Дополнительные сведения см. в разделе "Основные сведения о типах данных драйвера JDBC" для соответствующих сопоставлений. |
| Int getScale(int column)            | Получение масштаба для данного столбца.                                                                                                                                                                                                                                                                    |
| Boolean isAutoIncrement(int column) | Обозначает, содержит ли столбец идентификаторы.                                                                                                                                                                                                                                            |
| Boolean next()                      | Переход на следующую строку данных.                                                                                                                                                                                                                                                                         |
  
### <a name="sqlserverbulkcsvfilerecord"></a>SQLServerBulkCSVFileRecord  

Простая реализация интерфейса ISQLServerBulkRecord, которая может использоваться для чтения базовых типов данных Java из файла с разделителями, где каждая строка представляет строку данных.  
  
Примечания по реализации и ограничения  
  
1. Максимальный объем данных в любой строке ограничивается объемом доступной памяти, поскольку данные считываются по одной строке за раз.  
  
2. Потоковая передача типов данных большого размера, таких как varchar(max), varbinary(max), nvarchar(max), sqlxml и ntext, не поддерживается.  
  
3. Разделитель, указанный для CSV-файла, не должен содержаться в данных и, если это зарезервированный символ, должен быть надлежащим образом экранирован в регулярных выражениях Java.  
  
4. В реализации CSV-файла двойные кавычки рассматриваются как часть данных. Например, строка hello,"world","hello,world" будет рассматриваться как строка с четырьмя столбцами со значениями hello, "world", "hello, world", если разделитель — запятая.  
  
5. Символы новой строки используются в качестве признака конца строки и не допускаются в данных.  
  
| Конструктор                                                                                                                                                                 | Описание                                                                                                                                                                                                                                                                                                                        |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SQLServerBulkCSVFileRecord(String fileToParse, String encoding, String delimiter, Boolean firstLineIsColumnNamesSQLServerBulkCSVFileRecord(String, String, String, boolean) | Инициализирует новый экземпляр класса SQLServerBulkCSVFileRecord, который будет выполнять синтаксический анализ каждой строки в fileToParse с указанными разделителем и кодировкой. Если firstLineIsColumnNames имеет значение True, первая строка файла будет проанализирована как имена столбцов.  Если кодировка имеет значение NULL, будет использоваться кодировка по умолчанию.            |
| SQLServerBulkCSVFileRecord(String fileToParse, String encoding, Boolean firstLineIsColumnNamesSQLServerBulkCSVFileRecord(String, String, boolean)                           | Инициализирует новый экземпляр класса SQLServerBulkCSVFileRecord, который будет выполнять синтаксический анализ каждой строки в fileToParse с указанными разделителем-запятой и кодировкой. Если firstLineIsColumnNames имеет значение True, первая строка файла будет проанализирована как имена столбцов.  Если кодировка имеет значение NULL, будет использоваться кодировка по умолчанию. |
| SQLServerBulkCSVFileRecord(String fileToParse, Boolean firstLineIsColumnNamesSQLServerBulkCSVFileRecord(String, boolean)                                                    | Инициализирует новый экземпляр класса SQLServerBulkCSVFileRecord, который будет выполнять синтаксический анализ каждой строки в fileToParse с указанными разделителем-запятой и кодировкой по умолчанию. Если firstLineIsColumnNames имеет значение True, первая строка файла будет проанализирована как имена столбцов.                                                           |
  
| Метод                                                                                                 | Описание                                                                                         |
| ------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- |
| Void addColumnMetadata(int positionInFile, String columnName, int jdbcType, int precision, int scale)  | Добавляет метаданные для указанного столбца в файле.                                                     |
| Void close()                                                                                           | Освобождает все ресурсы, связанные со средством чтения файла.                                             |
| Void setTimestampWithTimezoneFormat(DateTim eFormatter dateTimeFormatter                               | Задает формат для синтаксического анализа данных отметки времени из файла как java.sql.Types.TIMESTAMP_WITH_TIMEZONE. |
| Void setTimestampWithTimezoneFormat(String dateTimeFormat)setTimeWithTimezoneFormat(DateTimeFormatter) | Задает формат для синтаксического анализа данных времени из файла как java.sql.Types.TIME_WITH_TIMEZONE.           |
| Void setTimeWithTimezoneFormat(DateTimeFormatter dateTimeFormatter)                                   | Задает формат для синтаксического анализа данных времени из файла как java.sql.Types.TIME_WITH_TIMEZONE.           |
| Void setTimeWithTimezoneFormat(String timeFormat)                                                      | Задает формат для синтаксического анализа данных времени из файла как java.sql.Types.TIME_WITH_TIMEZONE.           |
  
## <a name="see-also"></a>См. также раздел  

[Общие сведения о JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
