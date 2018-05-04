---
title: С помощью массового копирования с драйвером JDBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 21e19635-340d-49bb-b39d-4867102fb5df
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9f1a53821f6a8e0354b992b8110d300e96633b03
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-bulk-copy-with-the-jdbc-driver"></a>Использование массового копирования с драйвером JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Microsoft SQL Server включает популярную программу командной строки **bcp** обеспечивающую быстрое массовое копирование больших файлов в таблицы или представления в базах данных SQL Server. Класс SQLServerBulkCopy позволяет создавать решения на языке Java, которые предоставляют аналогичные возможности. Существуют другие способы загрузки данных в таблицу SQL Server (например, с помощью инструкции INSERT), но SQLServerBulkCopy делает это значительно быстрее.  
  
 Класс SQLServerBulkCopy можно использовать для записи данных только в таблицы SQL Server. Но источником данных может быть не только SQL Server, а любой источник данных, если данные могут быть прочитаны с помощью реализации ResultSet, RowSet или ISQLServerBulkRecord.  
  
 С помощью класса SQLServerBulkCopy вы можете выполнить:  
  
-   одну операцию массового копирования;  
  
-   несколько операций массового копирования;  
  
-   операцию массового копирования с транзакцией.  
  
> [!NOTE]  
>  При использовании драйвера Microsoft JDBC 4.1 для SQL Server или более ранней версии (которая не поддерживает класс SQLServerBulkCopy) вместо него можно воспользоваться инструкцией SQL Server Transact-SQL BULK INSERT.  
  
## <a name="bulk-copy-example-setup"></a>Пример настройки массового копирования  
 Класс SQLServerBulkCopy можно использовать для записи данных только в таблицы SQL Server. В примерах кода в этом разделе используется образец базы данных SQL Server AdventureWorks. Чтобы не допустить изменения существующих таблиц, примеры кода записывают данные в таблицы, которые сначала необходимо создать.  
  
 Таблицы BulkCopyDemoMatchingColumns и BulkCopyDemoDifferentColumns основаны на таблице AdventureWorks Production.Products. В примерах кода, использующих эти таблицы, данные из таблицы Production.Products добавляются к одной из этих таблиц-образцов. Таблица BulkCopyDemoDifferentColumns используется для демонстрации сопоставления столбцов из источника данных с целевой таблицей. Таблица BulkCopyDemoMatchingColumns используется в большинстве других примеров.  
  
 Некоторые примеры кода демонстрируют использование одного класса SQLServerBulkCopy для записи в несколько таблиц. В этих примерах в качестве целевых таблиц применяются BulkCopyDemoOrderHeader и BulkCopyDemoOrderDetail. Эти таблицы основаны на таблицах Sales.SalesOrderHeader и Sales.SalesOrderDetail из базы данных AdventureWorks.  
  
> [!NOTE]  
>  Примеры кода SQLServerBulkCopy предназначены только для демонстрации синтаксиса использования SQLServerBulkCopy. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL INSERT ... SELECT для копирования данных.  
  
###  <a name="BKMK_TableSetup"></a> Настройка таблицы  
 Чтобы создать таблицы, необходимые для правильной работы примеров кода, выполните следующие инструкции Transact-SQL в базе данных SQL Server.  
  
```  
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
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
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
>  Если при возникновении ошибки необходимо частично или полностью отменить массовое копирование, можно использовать управляемую SQLServerBulkCopy транзакцию или выполнить операцию массового копирования в существующей транзакции.  
>   
>  Дополнительные сведения см. в разделе [транзакций и массового копирования](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TransactionBulk)  
  
 Для массового копирования выполните следующие действия.  
  
1.  Подключитесь к исходному серверу и получите данные для копирования. Данные также могут поступать из других источников, если их можно извлечь из объекта ResultSet или реализации ISQLServerBulkRecord.  
  
2.  Подключение к серверу назначения (если не требуется **SQLServerBulkCopy** для установления соединения автоматически).  
  
3.  Создайте объект класса SQLServerBulkCopy, задав необходимые свойства через **setBulkCopyOptions**.  
  
4.  Вызовите **setDestinationTableName** метод, чтобы указать целевую таблицу для массовой операции вставки.  
  
5.  Вызовите один из **writeToServer** методы.  
  
6.  При необходимости обновите свойства с помощью **setBulkCopyOptions** и вызвать **writeToServer** еще раз при необходимости.  
  
7.  Вызовите **закрыть**, или помещать в оболочку операций массового копирования в операторе try-with-resources.  
  
> [!CAUTION]  
>  Мы рекомендуем, чтобы исходные и целевые типы данных столбцов совпадали. Если типы данных не совпадают, SQLServerBulkCopy попытается преобразовать каждое исходное значение в целевой тип данных. Преобразование может повлиять на производительность и может привести к непредвиденным ошибкам. Например, в большинстве случаев тип данных double может преобразовываться в тип данных decimal, но это происходит не всегда.  
  
### <a name="example"></a>Пример  
 Следующее приложение показывает, как загрузить данные с помощью класса SQLServerBulkCopy. В этом примере ResultSet используется для копирования данных из таблицы Production.Product в базе данных AdventureWorks в аналогичную таблицу в той же базе данных.  
  
> [!IMPORTANT]  
>  Этот образец не запустится, пока вы не создадите рабочие таблицы, как описано в [Настройка таблицы](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup). Этот пример кода предназначен только для демонстрации синтаксиса использования SQLServerBulkCopy. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL INSERT ... SELECT для копирования данных.  
  
```  
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;  
  
public class Program  
{  
    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        try  
        {  
            // Note: if you are not using try-with-resources statements (as here),  
            // you must remember to call close() on any Connection, Statement,   
            // ResultSet, and SQLServerBulkCopy objects that you create.  
  
            // Open a sourceConnection to the AdventureWorks database.   
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
            {  
                try (Statement stmt = sourceConnection.createStatement())  
                {  
                    // Perform an initial count on the destination table.  
                    long countStart = 0;  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        countStart = rsRowCount.getInt(1);  
                        System.out.println("Starting row count = " + countStart);  
                    }  
  
                    // Get data from the source table as a ResultSet.  
                    try (ResultSet rsSourceData = stmt.executeQuery(  
                            "SELECT ProductID, Name, ProductNumber FROM Production.Product"))  
                    {  
                        // Open the destination connection. In the real world you would    
                        // not use SQLServerBulkCopy to move data from one table to the other    
                        // in the same database. This is for demonstration purposes only.   
                        try (Connection destinationConnection =   
                                DriverManager.getConnection(connectionString))  
                        {  
                            // Set up the bulk copy object.    
                            // Note that the column positions in the source   
                            // table match the column positions in    
                            // the destination table so there is no need to   
                            // map columns.   
                            try (SQLServerBulkCopy bulkCopy =  
                                       new SQLServerBulkCopy(destinationConnection))  
                            {  
                                bulkCopy.setDestinationTableName("dbo.BulkCopyDemoMatchingColumns");  
  
                                try  
                                {  
                                    // Write from the source to the destination.  
                                    bulkCopy.writeToServer(rsSourceData);  
                                }  
                                catch (Exception e)  
                                {  
                                    // Handle any errors that may have occurred.  
                                    e.printStackTrace();  
                                }  
                            }  
  
                            // Perform a final count on the destination    
                            // table to see how many rows were added.  
                            try (ResultSet rsRowCount = stmt.executeQuery(  
                                    "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                            {  
                                rsRowCount.next();  
                                long countEnd = rsRowCount.getInt(1);  
                                System.out.println("Ending row count = " + countEnd);  
                                System.out.println((countEnd - countStart) + " rows were added.");  
                            }  
                        }  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,    
    // you can retrieve it from a configuration file.   
    private static String GetConnectionString()  
    {  
  
        // Create a variable for the connection string.  
        String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
           "databaseName=AdventureWorks;user=UserName;password=*****";  
  
        return connectionUrl;  
    }  
}  
```  
  
### <a name="performing-a-bulk-copy-operation-using-transact-sql"></a>Выполнение операции массового копирования с помощью Transact-SQL  
 Следующий пример демонстрирует использование метода executeUpdate для выполнения инструкции BULK INSERT.  
  
> [!NOTE]  
>  Путь к источнику данных указан относительно сервера. Для успешного выполнения массового копирования у процесса сервера должен быть доступ к этому пути.  
  
```  
try (Connection con = DriverManager.getConnection(connectionString))  
{  
    try (Statement stmt = con.createStatement())  
    {  
        // Perform the BULK INSERT  
        stmt.executeUpdate(  
                "BULK INSERT Northwind.dbo.[Order Details] " +  
                        "FROM 'f:\\mydata\\data.tbl' " +  
                        "WITH ( FORMATFILE='f:\\mydata\\data.fmt' )");  
    }  
}  
```  
  
## <a name="multiple-bulk-copy-operations"></a>несколько операций массового копирования;  
 Вы можете выполнить несколько операций массового копирования, используя один экземпляр класса SQLServerBulkCopy. Если между копированиями параметры операции изменяются (например, имя целевой таблицы), необходимо обновить их до последующих вызовов методов writeToServer, как показано в следующем примере. Если значения свойств не изменяются явным образом, все они остаются такими же, как при предыдущей операции массового копирования для данного экземпляра.  
  
> [!NOTE]  
>  Выполнение нескольких операций массового копирования с использованием одного экземпляра SQLServerBulkCopy обычно более эффективно, чем использование отдельного экземпляра для каждой операции.  
  
 При выполнении нескольких операций массового копирования с одним объектом SQLServerBulkCopy не существует ограничений, касающихся совпадения или различий целевой информации в каждой операции. Однако для каждой записи на сервер необходимо убедиться, что связи столбцов настроены правильно.  
  
> [!IMPORTANT]  
>  Этот образец не запустится, пока вы не создадите рабочие таблицы, как описано в [Настройка таблицы](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup). Этот пример кода предназначен только для демонстрации синтаксиса использования SQLServerBulkCopy. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL INSERT ... SELECT для копирования данных.  
  
```  
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;  
  
public class Program  
{  
    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        try  
        {  
            // Note: if you are not using try-with-resources statements (as here),  
            // you must remember to call close() on any Connection, Statement,   
            // ResultSet, and SQLServerBulkCopy objects that you create.  
  
            // Open a sourceConnection to the AdventureWorks database.   
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection sourceConnection1 = DriverManager.getConnection(connectionString))  
            {  
                try (Statement stmt = sourceConnection1.createStatement())  
                {  
  
                    // Empty the destination tables.   
                    stmt.executeUpdate("DELETE FROM dbo.BulkCopyDemoOrderHeader;");  
                    stmt.executeUpdate("DELETE FROM dbo.BulkCopyDemoOrderDetail;");  
  
                    // Perform an initial count on the destination   
                    //  table with matching columns.  
                    long countStartHeader = 0;  
                    try (ResultSet rsRowCountHeader = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoOrderHeader;"))  
                    {  
                        rsRowCountHeader.next();  
                        countStartHeader = rsRowCountHeader.getInt(1);  
                        System.out.println("Starting row count for Header table = " + countStartHeader);  
                    }  
  
                    // Perform an initial count on the destination   
                    // table with different column positions.  
                    long countStartDetail = 0;  
                    try (ResultSet rsRowCountDetail = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoOrderDetail;"))  
                    {  
                        rsRowCountDetail.next();  
                        countStartDetail = rsRowCountDetail.getInt(1);  
                        System.out.println("Starting row count for Detail table = " + countStartDetail);  
                    }  
  
                    // Get data from the source table as a ResultSet.   
                    // The Sales.SalesOrderHeader and Sales.SalesOrderDetail   
                    // tables are quite large and could easily cause a timeout   
                    // if all data from the tables is added to the destination.    
                    // To keep the example simple and quick, a parameter is     
                    // used to select only orders for a particular account    
                    // as the source for the bulk insert.  
                    try (PreparedStatement preparedStmt1 = sourceConnection1.prepareStatement(  
                            "SELECT [SalesOrderID], [OrderDate], " +  
                            "[AccountNumber] FROM [Sales].[SalesOrderHeader] " +  
                            "WHERE [AccountNumber] = ?;"))  
                    {  
                        preparedStmt1.setString(1, "10-4020-000034");  
  
                        try (ResultSet rsHeader = preparedStmt1.executeQuery())  
                        {  
                            // Get the Detail data in a separate connection.   
                            try (Connection sourceConnection2 = DriverManager.getConnection(connectionString))  
                            {  
                                try (PreparedStatement preparedStmt2 = sourceConnection2.prepareStatement(  
                                        "SELECT [Sales].[SalesOrderDetail].[SalesOrderID], " +  
                                                "[SalesOrderDetailID], [OrderQty], [ProductID], " +  
                                                "[UnitPrice] FROM [Sales].[SalesOrderDetail] " +  
                                                "INNER JOIN [Sales].[SalesOrderHeader] " +  
                                                "ON [Sales].[SalesOrderDetail].[SalesOrderID] " +  
                                                "= [Sales].[SalesOrderHeader].[SalesOrderID] " +  
                                                "WHERE [AccountNumber] = ?;"))  
                                {  
                                    preparedStmt2.setString(1, "10-4020-000034");  
  
                                    try (ResultSet rsDetail = preparedStmt2.executeQuery())  
                                    {  
                                        // Create the SQLServerBulkCopySQLServerBulkCopy object.    
                                        try (SQLServerBulkCopy bulkCopy =  
                                                   new SQLServerBulkCopy(connectionString))  
                                        {  
                                            bulkCopy.setBulkCopyOptions(copyOptions);  
                                            bulkCopy.setDestinationTableName("dbo.BulkCopyDemoOrderHeader");  
  
                                            // Guarantee that columns are mapped correctly by   
                                            // defining the column mappings for the order.  
                                            bulkCopy.addColumnMapping("SalesOrderID", "SalesOrderID");  
                                            bulkCopy.addColumnMapping("OrderDate", "OrderDate");  
                                            bulkCopy.addColumnMapping("AccountNumber", "AccountNumber");  
  
                                            // Write rsHeader to the destination.   
                                            try  
                                            {  
                                                bulkCopy.writeToServer(rsHeader);  
                                            }  
                                            catch (Exception e)  
                                            {  
                                                // Handle any errors that may have occurred.  
                                                e.printStackTrace();  
                                            }  
  
                                            // Set up the order details destination.   
                                            bulkCopy.setDestinationTableName("dbo.BulkCopyDemoOrderDetail");  
  
                                            // Clear the existing column mappings  
                                            bulkCopy.clearColumnMappings();  
  
                                            // Add order detail column mappings.  
                                            bulkCopy.addColumnMapping("SalesOrderID", "SalesOrderID");  
                                            bulkCopy.addColumnMapping(  
                                                    "SalesOrderDetailID",   
                                                    "SalesOrderDetailID");  
                                            bulkCopy.addColumnMapping("OrderQty", "OrderQty");  
                                            bulkCopy.addColumnMapping("ProductID", "ProductID");  
                                            bulkCopy.addColumnMapping("UnitPrice", "UnitPrice");  
  
                                            // Write rsDetail to the destination.   
                                            try  
                                            {  
                                                bulkCopy.writeToServer(rsDetail);  
                                            }  
                                            catch (Exception e)  
                                            {  
                                                // Handle any errors that may have occurred.  
                                                e.printStackTrace();  
                                            }  
                                        }  
                                    }  
                                }  
                            }  
                        }  
                    }  
  
                    // Perform a final count on the destination   
                    // tables to see how many rows were added.  
                    try (ResultSet rsRowCountHeader = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoOrderHeader;"))  
                    {  
                        rsRowCountHeader.next();  
                        long countEndHeader =  rsRowCountHeader.getInt(1);  
                        System.out.println(  
                                (countEndHeader - countStartHeader) +   
                                " rows were added to the Header table.");  
                    }  
  
                    try (ResultSet rsRowCountDetail = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoOrderDetail;"))  
                    {  
                        rsRowCountDetail.next();  
                        long countEndDetail = rsRowCountDetail.getInt(1);  
                        System.out.println(  
                                (countEndDetail - countStartDetail) +   
                                " rows were added to the Detail table.");  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,    
    // you can retrieve it from a configuration file.   
    private static String GetConnectionString()  
    {  
        // Create a variable for the connection string.  
        String connectionUrl = "jdbc:sqlserver://localhost:1433;"  
                + "databaseName=AdventureWorks;user=UserName;password=*****";  
  
        return connectionUrl;  
    }  
}  
  
```  
  
##  <a name="BKMK_TransactionBulk"></a> Транзакции и операции массового копирования  
 Операции массового копирования могут выполняться как изолированные операции или как часть многошаговой транзакции. В последнем случае вы можете выполнить более одной операции массового копирования в одной транзакции, а также выполнять другие операции с базами данных (такие как вставка, обновление и удаление) с возможностью фиксации или отката всей транзакции.  
  
 По умолчанию операция массового копирования выполняется как изолированная. Операция массового копирования выполняется не как транзакция и без возможности отката. Если при возникновении ошибки необходимо частично или полностью отменить массовое копирование, можно использовать управляемую SQLServerBulkCopy транзакцию или выполнить операцию массового копирования в существующей транзакции.  
  
### <a name="performing-a-non-transacted-bulk-copy-operation"></a>Выполнение операции массового копирования без транзакции  
 Следующее приложение показывает, что происходит, когда во время операции массового копирования без транзакции возникает ошибка.  
  
 В примере исходная таблица и целевая таблица включают столбец идентификаторов с именем **ProductID**. Вначале код подготавливает целевую таблицу, удаляя все строки, а потом вставляя одну строку, для которой **ProductID** известно существует в исходной таблице. По умолчанию в целевой таблице для каждой добавляемой строки создается новое значение столбца идентификаторов. В этом примере при открытии соединения задается параметр, заставляющий процесс массовой загрузки использовать значения идентификаторов из исходной таблицы.  
  
 Операция массового копирования выполняется с **BatchSize** равным 10. Когда операция встречает недопустимую строку, вызывается исключение. В первом примере операция массового копирования выполняется без транзакции. Фиксируются все пакеты, скопированные до появления ошибки. Пакет, содержащий повторяющийся ключ, откатывается, а операция массового копирования прерывается до обработки любых других пакетов.  
  
> [!NOTE]  
>  Этот образец не запустится, пока вы не создадите рабочие таблицы, как описано в [Настройка таблицы](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup). Этот пример кода предназначен только для демонстрации синтаксиса использования SQLServerBulkCopy. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL INSERT ... SELECT для копирования данных.  
  
```  
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;  
  
public class Program  
{  
    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        try  
        {  
            // Note: if you are not using try-with-resources statements (as here),  
            // you must remember to call close() on any Connection, Statement,   
            // ResultSet, and SQLServerBulkCopy objects that you create.  
  
            // Open a sourceConnection to the AdventureWorks database.   
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
            {  
                try (Statement stmt = sourceConnection.createStatement())  
                {  
                    //  Delete all from the destination table.  
                    stmt.executeUpdate("DELETE FROM dbo.BulkCopyDemoMatchingColumns");  
  
                    //  Add a single row that will result in duplicate key            
                    //  when all rows from source are bulk copied.            
                    //  Note that this technique will only be successful in             
                    //  illustrating the point if a row with ProductID = 446              
                    //  exists in the AdventureWorks Production.Products table.             
                    //  If you have made changes to the data in this table, change            
                    //  the SQL statement in the code to add a ProductID that            
                    //  does exist in your version of the Production.Products            
                    //  table. Choose any ProductID in the middle of the table            
                    //  (not first or last row) to best illustrate the result.  
                    stmt.executeUpdate("SET IDENTITY_INSERT dbo.BulkCopyDemoMatchingColumns ON;" +  
                            "INSERT INTO " + "dbo.BulkCopyDemoMatchingColumns " +  
                            "([ProductID], [Name] ,[ProductNumber]) " +  
                            "VALUES(446, 'Lock Nut 23','LN-3416');" +  
                            "SET IDENTITY_INSERT dbo.BulkCopyDemoMatchingColumns OFF");  
  
                    // Perform an initial count on the destination table.  
                    long countStart = 0;  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        countStart = rsRowCount.getInt(1);  
                        System.out.println("Starting row count = " + countStart);  
                    }  
  
                    //  Get data from the source table as a ResultSet.  
                    try (ResultSet rsSourceData = stmt.executeQuery(  
                            "SELECT ProductID, Name, ProductNumber FROM Production.Product"))  
                    {  
  
                        // Set up the bulk copy object using the KeepIdentity option and BatchSize = 10.  
                        SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();  
                        copyOptions.setKeepIdentity(true);  
                        copyOptions.setBatchSize(10);  
  
                        try (SQLServerBulkCopy bulkCopy =   
                                new SQLServerBulkCopy(connectionString))  
                        {  
                            bulkCopy.setBulkCopyOptions(copyOptions);  
                            bulkCopy.setDestinationTableName("dbo.BulkCopyDemoMatchingColumns");  
  
                            // Write from the source to the destination.   
                            // This should fail with a duplicate key error   
                            // after some of the batches have been copied.   
                            try  
                            {  
                                bulkCopy.writeToServer(rsSourceData);  
                            }  
                            catch (Exception e)  
                            {  
                                // Handle any errors that may have occurred.  
                                e.printStackTrace();  
                            }  
                        }  
                    }  
  
                    // Perform a final count on the destination    
                    // table to see how many rows were added.  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        long countEnd = rsRowCount.getInt(1);  
                        System.out.println("Ending row count = " + countEnd);  
                        System.out.println((countEnd - countStart) + " rows were added.");  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,    
    // you can retrieve it from a configuration file.   
    private static String GetConnectionString()  
    {  
        // Create a variable for the connection String.  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
              "databaseName=AdventureWorks;user=UserName;password=*****";  
  
        return connectionUrl;  
    }  
}  
```  
  
### <a name="performing-a-dedicated-build-copy-operation-in-a-transaction"></a>Выполнение выделенной операции массового копирования в транзакции  
 По умолчанию операция массового копирования является своей собственной транзакцией. Если вы хотите выполнить выделенную операцию массового копирования, создайте новый экземпляр SQLServerBulkCopy со строкой подключения. В этом случае операция массового копирования создает и затем фиксирует или откатывает транзакцию. Можно явно указать **UseInternalTransaction** в диалоговом окне **SQLServerBulkCopyOptions** явным образом вызвать операции массового копирования выполнить свою собственную транзакцию, в результате чего каждый пакет массовой Скопируйте операции будет выполняться в отдельной транзакции.  
  
> [!NOTE]  
>  Поскольку разные пакеты выполняются в разных транзакциях, если во время операции массового копирования возникает ошибка, для всех строк в текущем пакете будет выполнен откат, но строки из предыдущих пакетов останутся в базе данных.  
  
 Следующее приложение похоже на предыдущий пример с одним исключением: в этом примере операция массового копирования обрабатывает собственные транзакции. Фиксируются все пакеты, скопированные до появления ошибки. Пакет, содержащий повторяющийся ключ, откатывается, а операция массового копирования прерывается до обработки любых других пакетов.  
  
> [!NOTE]  
>  Этот образец не запустится, пока вы не создадите рабочие таблицы, как описано в [Настройка таблицы](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup). Этот пример кода предназначен только для демонстрации синтаксиса использования SQLServerBulkCopy. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL INSERT ... SELECT для копирования данных.  
  
```  
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;  
  
public class Program  
{  
    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        try  
        {  
            // Note: if you are not using try-with-resources statements (as here),  
            // you must remember to call close() on any Connection, Statement,   
            // ResultSet, and SQLServerBulkCopy objects that you create.  
  
            // Open a sourceConnection to the AdventureWorks database.   
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
            {  
                try (Statement stmt = sourceConnection.createStatement())  
                {  
                    //  Delete all from the destination table.  
                    stmt.executeUpdate("DELETE FROM dbo.BulkCopyDemoMatchingColumns");  
  
                    //  Add a single row that will result in duplicate key            
                    //  when all rows from source are bulk copied.            
                    //  Note that this technique will only be successful in             
                    //  illustrating the point if a row with ProductID = 446              
                    //  exists in the AdventureWorks Production.Products table.             
                    //  If you have made changes to the data in this table, change            
                    //  the SQL statement in the code to add a ProductID that            
                    //  does exist in your version of the Production.Products            
                    //  table. Choose any ProductID in the middle of the table            
                    //  (not first or last row) to best illustrate the result.  
                    stmt.executeUpdate("SET IDENTITY_INSERT dbo.BulkCopyDemoMatchingColumns ON;" +  
                            "INSERT INTO " + "dbo.BulkCopyDemoMatchingColumns " +  
                            "([ProductID], [Name] ,[ProductNumber]) " +  
                            "VALUES(446, 'Lock Nut 23','LN-3416');" +  
                            "SET IDENTITY_INSERT dbo.BulkCopyDemoMatchingColumns OFF");  
  
                    // Perform an initial count on the destination table.  
                    long countStart = 0;  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        countStart = rsRowCount.getInt(1);  
                        System.out.println("Starting row count = " + countStart);  
                    }  
  
                    //  Get data from the source table as a ResultSet.  
                    try (ResultSet rsSourceData = stmt.executeQuery(  
                            "SELECT ProductID, Name, ProductNumber FROM Production.Product"))  
                    {  
  
                        // Set up the bulk copy object.  
                        // Note that when specifying the UseInternalTransaction   
                        // option, you cannot also use an external transaction.   
                        // Therefore, you must use the SQLServerBulkCopy construct that   
                        // requires a string for the connection, rather than an   
                        // existing Connection object.   
                        SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();  
                        copyOptions.setKeepIdentity(true);  
                        copyOptions.setBatchSize(10);  
                        copyOptions.setUseInternalTransaction(true);  
  
                        try (SQLServerBulkCopy bulkCopy =   
                                new SQLServerBulkCopy(connectionString))  
                        {  
                            bulkCopy.setBulkCopyOptions(copyOptions);  
                            bulkCopy.setDestinationTableName("dbo.BulkCopyDemoMatchingColumns");  
  
                            // Write from the source to the destination.   
                            // This should fail with a duplicate key error   
                            // after some of the batches have been copied.   
                            try  
                            {  
                                bulkCopy.writeToServer(rsSourceData);  
                            }  
                            catch (Exception e)  
                            {  
                                // Handle any errors that may have occurred.  
                                e.printStackTrace();  
                            }  
                        }  
                    }  
  
                    // Perform a final count on the destination    
                    // table to see how many rows were added.  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        long countEnd = rsRowCount.getInt(1);  
                        System.out.println("Ending row count = " + countEnd);  
                        System.out.println((countEnd - countStart) + " rows were added.");  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,    
    // you can retrieve it from a configuration file.   
    private static String GetConnectionString()  
    {  
        // Create a variable for the connection string.  
        String connectionUrl = "jdbc:sqlserver://localhost:1433;"  
                + "databaseName=AdventureWorks;user=UserName;password=*****";  
  
        return connectionUrl;  
    }  
}  
```  
  
### <a name="using-existing-transactions"></a>Использование существующих транзакций  
 Вы можете передать объект Connection с включенными транзакциями в качестве параметра конструктора SQLServerBulkCopy. В этом случае операция массового копирования выполняется в существующей транзакции, а состояние транзакции не изменяется (то есть она не фиксируется и не прерывается). Это позволяет приложению включить операцию массового копирования в транзакцию с другими операциями базы данных. Если необходимо выполнить откат всей операции массового копирования из-за ошибки или если массовое копирование должно выполняться как часть большего процесса, который может быть отменен, можно выполнить откат в объекте Connection в любой момент после массового копирования.  
  
 Следующее приложение похоже на первый пример (без транзакции) с одним исключением: в этом примере операция массового копирования включена в большую, внешнюю транзакцию. Если возникает ошибка нарушения первичного ключа, производится откат всей транзакции и никакие строки не добавляются в целевую таблицу.  
  
> [!NOTE]  
>  Этот образец не запустится, пока вы не создадите рабочие таблицы, как описано в [Настройка таблицы](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#BKMK_TableSetup). Этот пример кода предназначен только для демонстрации синтаксиса использования SQLServerBulkCopy. Если исходная и целевая таблицы расположены в одном экземпляре SQL Server, будет проще и быстрее использовать инструкцию Transact-SQL INSERT ... SELECT для копирования данных.  
  
```  
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopyOptions;  
  
public class Program  
{  
    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        try  
        {  
            // Note: if you are not using try-with-resources statements (as here),  
            // you must remember to call close() on any Connection, Statement,   
            // ResultSet, and SQLServerBulkCopy objects that you create.  
  
            // Open a sourceConnection to the AdventureWorks database.   
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
            {  
                try (Statement stmt = sourceConnection.createStatement())  
                {  
                    //  Delete all from the destination table.  
                    stmt.executeUpdate("DELETE FROM dbo.BulkCopyDemoMatchingColumns");  
  
                    //  Add a single row that will result in duplicate key            
                    //  when all rows from source are bulk copied.            
                    //  Note that this technique will only be successful in             
                    //  illustrating the point if a row with ProductID = 446              
                    //  exists in the AdventureWorks Production.Products table.             
                    //  If you have made changes to the data in this table, change            
                    //  the SQL statement in the code to add a ProductID that            
                    //  does exist in your version of the Production.Products            
                    //  table. Choose any ProductID in the middle of the table            
                    //  (not first or last row) to best illustrate the result.  
                    stmt.executeUpdate("SET IDENTITY_INSERT dbo.BulkCopyDemoMatchingColumns ON;" +  
                            "INSERT INTO " + "dbo.BulkCopyDemoMatchingColumns " +  
                            "([ProductID], [Name] ,[ProductNumber]) " +  
                            "VALUES(446, 'Lock Nut 23','LN-3416');" +  
                            "SET IDENTITY_INSERT dbo.BulkCopyDemoMatchingColumns OFF");  
  
                    // Perform an initial count on the destination table.  
                    long countStart = 0;  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        countStart = rsRowCount.getInt(1);  
                        System.out.println("Starting row count = " + countStart);  
                    }  
  
                    //  Get data from the source table as a ResultSet.  
                    try (ResultSet rsSourceData = stmt.executeQuery(  
                            "SELECT ProductID, Name, ProductNumber FROM Production.Product"))  
                    {  
  
                        // Set up the bulk copy object inside the transaction.  
                        try (Connection destinationConnection =   
                                DriverManager.getConnection(connectionString))  
                        {  
                            destinationConnection.setAutoCommit(false);  
  
                            SQLServerBulkCopyOptions copyOptions = new SQLServerBulkCopyOptions();  
                            copyOptions.setKeepIdentity(true);  
                            copyOptions.setBatchSize(10);  
  
                            try (SQLServerBulkCopy bulkCopy =   
                                    new SQLServerBulkCopy(destinationConnection))  
                            {  
                                bulkCopy.setBulkCopyOptions(copyOptions);  
                                bulkCopy.setDestinationTableName("dbo.BulkCopyDemoMatchingColumns");  
  
                                // Write from the source to the destination.   
                                // This should fail with a duplicate key error.   
                                try  
                                {  
                                    bulkCopy.writeToServer(rsSourceData);  
                                    destinationConnection.commit();  
                                }  
                                catch (Exception e)  
                                {  
                                    // Handle any errors that may have occurred.  
                                    e.printStackTrace();  
                                    destinationConnection.rollback();  
                                }  
                            }  
                        }  
                    }  
  
                    // Perform a final count on the destination    
                    // table to see how many rows were added.  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        long countEnd = rsRowCount.getInt(1);  
                        System.out.println("Ending row count = " + countEnd);  
                        System.out.println((countEnd - countStart) + " rows were added.");  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,    
    // you can retrieve it from a configuration file.   
    private static String GetConnectionString()  
    {  
        // Create a variable for the connection string.  
        String connectionUrl = "jdbc:sqlserver://localhost:1433;"  
                + "databaseName=AdventureWorks;user=UserName;password=*****";  
  
        return connectionUrl;  
    }  
}  
  
```  
  
### <a name="bulk-copy-from-a-csv-file"></a>Массовое копирование из CSV-файла  
 Следующее приложение показывает, как загрузить данные с помощью класса SQLServerBulkCopy. В этом примере CSV-файл используется для копирования данных, экспортированных из таблицы Production.Product в базе данных AdventureWorks, в аналогичную таблицу в той же базе данных.  
  
> [!IMPORTANT]  
>  Этот образец не запустится, пока вы не создадите рабочие таблицы, как описано в [Настройка таблицы](../../ssms/download-sql-server-management-studio-ssms.md) его получить.  
  
1.  Откройте **SQL Server Management Studio** и подключитесь к SQL Server с базой данных AdventureWorks.  
  
2.  Разверните узел базы данных, щелкните правой кнопкой мыши базу данных AdventureWorks, выберите **задачи** и **Экспорт данных**...  
  
3.  Источник данных, выберите **источника данных** , позволяющий подключиться к серверу SQL Server (например SQL Server Native Client 11.0), проверьте конфигурацию и затем **Далее**  
  
4.  В качестве места назначения выберите **Flat File Destination** и введите **имя файла** с назначением, например C:\Test\TestBulkCSVExample.csv. Убедитесь, что **формат** в качестве разделителя, **ограничитель текста** не используется и включить **имена столбцов в первой строке данных**и выберите **Далее**  
  
5.  Выберите **написать запрос, указывающий данные для передачи** и **Далее**.  Введите ваш **инструкции SQL** ВЫБЕРИТЕ ProductID, Name, ProductNumber FROM Production.Product и **Далее**  
  
6.  Проверьте конфигурацию: разделитель строк {CR} {LF} и разделитель столбцов как запятую можно оставить {,}.  Выберите **изменить сопоставления**... и убедитесь, что данные **типа** является правильным для каждого столбца (например, целое число для ProductID и строка Юникода для остальных).  
  
7.  Перейдите к **Готово** и выполните экспорт.  
  
```  
  
import java.sql.*;  
  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCSVFileRecord;  
import com.microsoft.sqlserver.jdbc.SQLServerBulkCopy;  
  
public class Program  
{  
    public static void main(String[] args)  
    {  
        String connectionString = GetConnectionString();  
        SQLServerBulkCSVFileRecord fileRecord = null;  
        try  
        {              
            // Get data from the source file by loading it into a class that implements ISQLServerBulkRecord.  
            // Here we are using the SQLServerBulkCSVFileRecord implementation to import the example CSV file.  
            fileRecord = new SQLServerBulkCSVFileRecord("C:\\Test\\TestBulkCSVExample.csv", true);      
  
            // Set the metadata for each column to be copied.  
            fileRecord.addColumnMetadata(1, null, java.sql.Types.INTEGER, 0, 0);  
            fileRecord.addColumnMetadata(2, null, java.sql.Types.NVARCHAR, 50, 0);  
            fileRecord.addColumnMetadata(3, null, java.sql.Types.NVARCHAR, 25, 0);  
  
            // Open a destinationConnection to the AdventureWorks database.   
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
            try (Connection destinationConnection = DriverManager.getConnection(connectionString))  
            {  
                try (Statement stmt = destinationConnection.createStatement())  
                {  
                    // Perform an initial count on the destination table.  
                    long countStart = 0;  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        countStart = rsRowCount.getInt(1);  
                        System.out.println("Starting row count = " + countStart);  
                    }  
  
                    // Set up the bulk copy object.    
                    // Note that the column positions in the source   
                    // data reader match the column positions in    
                    // the destination table so there is no need to   
                    // map columns.   
                    try (SQLServerBulkCopy bulkCopy =  
                               new SQLServerBulkCopy(destinationConnection))  
                    {  
                        bulkCopy.setDestinationTableName("dbo.BulkCopyDemoMatchingColumns");  
  
                        try  
                        {  
                            // Write from the source to the destination.  
                            bulkCopy.writeToServer(fileRecord);  
                        }  
                        catch (Exception e)  
                        {  
                            // Handle any errors that may have occurred.  
                            e.printStackTrace();  
                        }  
                    }  
  
                    // Perform a final count on the destination    
                    // table to see how many rows were added.  
                    try (ResultSet rsRowCount = stmt.executeQuery(  
                            "SELECT COUNT(*) FROM dbo.BulkCopyDemoMatchingColumns;"))  
                    {  
                        rsRowCount.next();  
                        long countEnd = rsRowCount.getInt(1);  
                        System.out.println("Ending row count = " + countEnd);  
                        System.out.println((countEnd - countStart) + " rows were added.");  
                    }  
                }  
            }  
        }  
        catch (Exception e)  
        {  
            // Handle any errors that may have occurred.  
            e.printStackTrace();  
        }  
        finally  
        {  
            if (fileRecord != null) try { fileRecord.close(); } catch(Exception e) {}  
        }  
    }  
  
    // To avoid storing the sourceConnection String in your code,    
    // you can retrieve it from a configuration file.   
    private static String GetConnectionString()  
    {  
  
        // Create a variable for the connection string.  
        String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
           "databaseName=AdventureWorks;user=UserName;password=*****";  
  
        return connectionUrl;  
    }  
}  
  
```  
  
### <a name="bulk-copy-with-always-encrypted-columns"></a>Массовое копирование с помощью постоянного шифрования столбцов  
 Начиная с Microsoft JDBC Driver 6.0 для SQL Server, массовое копирование поддерживается всегда зашифрованным столбцам.  
  
 В зависимости от параметров массового копирования и способ шифрования тип исходной и целевой таблиц, драйвер JDBC может прозрачно расшифровывать и зашифровать данные, или он может отправить зашифрованные данные как есть. Например при массовом копировании данных из зашифрованного столбца со столбцом незашифрованным, драйвер прозрачно расшифровывает данные перед отправкой в SQL Server. Аналогичным образом при массовом копировании данных из незашифрованного столбца (или из CSV-файла), при этом для зашифрованного столбца, драйвер прозрачно шифрует данные перед отправкой в SQL Server. Если оба источника и назначения шифруется, затем в зависимости от **allowEncryptedValueModifications** массового копирования, драйвер будет отправлять данные как есть или может расшифровать данные и зашифровать его еще раз перед отправкой в SQL Server.  
  
 Дополнительные сведения см. в разделе **allowEncryptedValueModifications** массового копирования ниже, и [использование постоянного шифрования с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).  
  
> [!IMPORTANT]  
>  Ограничение Microsoft JDBC Driver 6.0 для SQL Server, при выполнении массового копирования данных из CSV-файла для зашифрованных столбцов:  
>   
>  Для типов даты и времени поддерживается только Transact-SQL по умолчанию формат строковых литералов  
>   
>  Не поддерживаются типы данных DATETIME и SMALLDATETIME  
  
## <a name="bulk-copy-api-for-jdbc-driver"></a>Массовое копирование API для драйвера JDBC  
  
### <a name="sqlserverbulkcopy"></a>SQLServerBulkCopy  
 Позволяет эффективно выполнять массовую загрузку таблицы SQL Server с данными из другого источника.  
  
 Microsoft SQL Server включает популярную программу командной строки bcp, используемую для перемещения данных из одной таблицы в другую как на одном сервере, так и между серверами. Класс SQLServerBulkCopy позволяет создавать решения на языке Java, которые предоставляют аналогичные возможности. Существуют другие способы загрузки данных в таблицу SQL Server (например, с помощью инструкции INSERT), но SQLServerBulkCopy делает это значительно быстрее.  
  
 Класс SQLServerBulkCopy можно использовать для записи данных только в таблицы SQL Server. Но источником данных может быть не только SQL Server, а любой источник данных, если данные могут быть прочитаны с помощью экземпляра ResultSet или реализации ISQLServerBulkRecord.  
  
|Конструктор|Описание|  
|-----------------|-----------------|  
|SQLServerBulkCopy(Connection)|Инициализирует новый экземпляр класса SQLServerBulkCopy, используя указанный открытый экземпляр SQLServerConnection. Если для объекта Connection включены транзакции, операции копирования будут выполняться в контексте этой транзакции.|  
|SQLServerBulkCopy (строка URL-адреса подключения)|Инициализирует и открывает новый экземпляр SQLServerConnection, в зависимости от предоставленного URL-адреса подключения. Конструктор использует SQLServerConnection для инициализации нового экземпляра класса SQLServerBulkCopy.|  
  
|property|Описание|  
|--------------|-----------------|  
|DestinationTableName строки|Имя целевой таблицы на сервере.<br /><br /> Если DestinationTableName не было задано при вызове writeToServer, вызывается исключение SQLServerException.<br /><br /> DestinationTableName состоит трехкомпонентным именем (\<базы данных >.\< Схема-владелец >. \<имя >). При необходимости можно уточнить имя таблицы с помощью указания базы данных и схемы-владельца. Но если имя таблицы содержит символ подчеркивания («_») или другие специальные символы, необходимо заключить имя в скобки. Дополнительные сведения см. в разделе «Идентификаторы» в электронной документации по SQL Server.|  
|ColumnMappings|Сопоставления столбцов определяют связи между столбцами в источнике данных и столбцами в месте назначения.<br /><br /> Если сопоставления не определены, столбцы сопоставляются неявно по порядковому номеру. При этом исходная и целевая схемы должны совпадать. В противном случае будет вызвано исключение.<br /><br /> Если сопоставления не пусты, необязательно должны быть заданы все столбцы, присутствующие в источнике данных. Несопоставленные столбцы будут проигнорированы.<br /><br /> Обращаться к исходным и целевым столбцам можно по имени или порядковому номеру.|  
  
|Метод|Описание|  
|------------|-----------------|  
|Void addColumnMapping ((int sourceColumn, int destinationColumn)|Добавляет новое сопоставление столбцов, используя порядковые номера исходного и целевого столбцов.|  
|Void addColumnMapping ((int sourceColumn, destinationColumn строка)|Добавляет новое сопоставление столбцов, используя порядковый номер исходного столбца и имя целевого столбца.|  
|Void addColumnMapping ((строка sourceColumn, int destinationColumn)|Добавляет новое сопоставление столбцов, используя имя исходного столбца и порядковый номер целевого столбца.|  
|Void addColumnMapping (sourceColumn строка, строка destinationColumn)|Добавляет новое сопоставление столбцов, используя имена исходного и целевого столбцов.|  
|Void clearColumnMappings()|Очищает содержимое сопоставления столбцов.|  
|Void close()|Закрывает экземпляр SQLServerBulkCopy.|  
|SQLServerBulkCopyOptions getBulkCopyOptions()|Получает текущий набор SQLServerBulkCopyOptions.|  
|Строка getDestinationTableName()|Получает имя текущей целевой таблицы.|  
|Void setBulkCopyOptions(SQLServerBulkCopyOptions copyOptions)|Обновляет экземпляр SQLServerBulkCopy в соответствии с предоставленными параметрами.|  
|Void setDestinationTableName(String tableName)|Задает имя целевой таблицы.|  
|Void writeToServer(ResultSet sourceData)|Копирует все строки в предоставленном результирующем наборе ResultSet в целевую таблицу, указанную в свойстве DestinationTableName объекта SQLServerBulkCopy.|  
|Void writeToServer(RowSet sourceData)|Копирует все строки в предоставленном наборе строк RowSet в целевую таблицу, указанную в свойстве DestinationTableName объекта SQLServerBulkCopy.|  
|Void writeToServer(ISQLServerBulkRecord sourceData)|Копирует все строки в предоставленной реализации ISQLServerBulkRecord в целевую таблицу указано в свойстве DestinationTableName объекта SQLServerBulkCopy.|  
  
### <a name="sqlserverbulkcopyoptions"></a>SQLServerBulkCopyOptions  
 Коллекция параметров, которые управляют поведением методов writeToServer в экземпляре SQLServerBulkCopy.  
  
|Конструктор|Описание|  
|-----------------|-----------------|  
|SQLServerBulkCopyOptions()|Инициализирует новый экземпляр класса SQLServerBulkCopyOptions, используя значения по умолчанию для всех параметров.|  
  
 Методы get и set существуют для следующих параметров.  
  
|Параметр|Описание|По умолчанию|  
|------------|-----------------|-------------|  
|Логическое CheckConstraints|Проверка ограничений при вставке данных.|False — ограничения не проверяются.|  
|Логическое FireTriggers|Если этот параметр указан, сервер выполняет триггеры вставки для строк, вставляемых в базу данных.|False — триггеры не выполняются.|  
|Логическое KeepIdentity|Сохранять идентификационные значения источника.|False — значения идентификаторов назначаются целевым объектом.|  
|Логическое KeepNulls|Сохранять значения null в целевой таблице независимо от значений параметров по умолчанию.|False — значения null заменяются значениями по умолчанию, где это применимо.|  
|Логическое TableLock|Применить блокировку массового обновления на время операции массового копирования.|False — блокировки строк используются.|  
|Логическое UseInternalTransaction|Если этот параметр указан, каждый пакет операции массового копирования будет выполняться в рамках транзакции. Если SQLServerBulkCopy использует существующее подключение (как указано конструктором), вызывается исключение SQLServerException.  Если объект SQLServerBulkCopy создал выделенное соединение, транзакция будет разрешена.|False — транзакция отсутствует.|  
|Int BatchSize|Количество строк в каждом пакете. В конце каждого пакета строки из пакета передаются на сервер.<br /><br /> Пакет завершается, когда число обработанных строк равно BatchSize или отсутствуют строки для отправки в целевой источник данных.  Если экземпляр SQLServerBulkCopy объявлен без параметра UseInternalTransaction, на сервер передается число строк, равное BatchSize, но не выполняются никакие действия, связанные с транзакциями. Если параметр UseInternalTransaction включен, каждый пакет строк вставляется как отдельная транзакция.|Значение 0 указывает, что каждая операция writeToServer представляет один пакет.|  
|Int BulkCopyTimeout|Время выполнения операции до истечения времени ожидания в секундах. 0 — отсутствие ограничений; операция массового копирования будет ждать бесконечно долго.|60 секунд.|  
|Логическое allowEncryptedValueModifications|Этот параметр доступен с Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server.<br /><br /> Если указано, **allowEncryptedValueModifications** позволяет массовое копирование зашифрованных данных между таблицами или базами данных, без расшифровки данных. Как правило приложение нужно выбирать данные из зашифрованных столбцов из одной таблицы без расшифровки данных (приложение должно подключиться к базе данных с ключевым словом параметр шифрования столбца, отключена) и затем использовать этот параметр, чтобы операции массовой вставки данных который по-прежнему зашифрован. Дополнительные сведения см. в разделе [использование постоянного шифрования с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).<br /><br /> Будьте внимательны при указании **allowEncryptedValueModifications** это может привести к повреждению базы данных, так как драйвер не выполняет проверку, если данные шифруются на самом деле, или если правильность их шифрования с помощью того же шифрования тип алгоритма и ключа, где находится целевой столбец.||  
  
 Методы get и set:  
  
|Методы|Описание|  
|-------------|-----------------|  
|Логическое isCheckConstraints()|Указывает, будут ли проверяться при вставке данных или нет ограничений.|  
|Void setCheckConstraints(Boolean checkConstraints)|Задает ограничения будут проверяться при вставке данных или нет.|  
|Логическое isFireTriggers()|Указывает, если сервер должен срабатывать триггеры вставки для строк, вставляемых в базу данных.|  
|Void setFireTriggers(Boolean fireTriggers)|Задает ли сервера должно быть присвоено срабатывание триггеров для строк, вставляемых в базу данных.|  
|Логическое isKeepIdentity()|Указывает, следует ли сохранять идентификационные значения любого источника.|  
|Void setKeepIdentity(Boolean keepIdentity)|Задает, следует ли сохранять значения идентификаторов.|  
|Логическое isKeepNulls()|Указывает, следует ли сохранять значения null в целевой таблице независимо от параметров значений по умолчанию или если они следует заменить на значения по умолчанию (где применимо).|  
|Void setKeepNulls(Boolean keepNulls)|Задает, следует ли сохранять значения null в целевой таблице независимо от параметров значений по умолчанию, или если они следует заменить на значения по умолчанию (где применимо).|  
|Логическое isTableLock()|Указывает, следует ли SQLServerBulkCopy получить блокировку массовых обновлений в течение операции массового копирования.|  
|Void setTableLock(Boolean tableLock)|Задает ли SQLServerBulkCopy получает блокировку массовых обновлений в течение операции массового копирования.|  
|Логическое isUseInternalTransaction()|Указывает, будет ли каждый пакет операции массового копирования внутри транзакции.|  
|Void setUseInternalTranscation(Boolean useInternalTransaction)|Задает ли каждый пакет операции массового копирования будет выполняться в рамках транзакции или нет.|  
|Int getBatchSize()|Возвращает количество строк в каждом пакете. В конце каждого пакета строк в пакете, отправляются на сервер|  
|Void setBatchSize(int batchSize)|Задает число строк в каждом пакете. В конце каждого пакета строки из пакета передаются на сервер.|  
|Int getBulkCopyTimeout()|Возвращает число секунд для выполнения операции до истечения времени ожидания.|  
|Void setBulkCopyTimeout(int timeout)|Задает число секунд для выполнения операции до истечения времени ожидания.|  
|Логическое isAllowEncryptedValueModifications()|Указывает, включен ли параметр allowEncryptedValueModifications.|  
|void setAllowEncryptedValueModifications(boolean allowEncryptedValueModifications)|Настраивает параметр allowEncryptedValueModifications, который используется для массового копирования с помощью постоянного шифрования столбцов.|  
  
### <a name="isqlserverbulkrecord"></a>ISQLServerBulkRecord  
 Интерфейс ISQLServerBulkRecord можно использовать для создания классов, которые считывают данные из любого источника (например, файла), чтобы позволить экземпляру SQLServerBulkCopy выполнить массовую загрузку данных таблицы SQL Server.  
  
|Методы интерфейса|Описание|  
|-----------------------|-----------------|  
|Задать\<целое число > getColumnOrdinals()|Получение порядковых номеров столбцов, представленных в этой записи данных.|  
|Строка getColumnName(int column)|Получение имени заданного столбца.|  
|Int getColumnType (int столбец)|Получение типа данных JDBC заданного столбца.|  
|Int getPrecision (int столбец)|Получение точности для данного столбца.|  
|Объект getRowData()]|Возвращает данные для текущей строки как массив объектов.<br /><br /> Тип каждого объекта должен соответствовать типу Java, используемому для представления указанного типа данных JDBC этого столбца.  Дополнительные сведения см. в разделе «Основные сведения о типах данных драйвера JDBC» для соответствующих сопоставлений.|  
|Int getScale (int столбец)|Получение масштаба для данного столбца.|  
|Логическое isAutoIncrement (int столбец)|Обозначает, содержит ли столбец идентификаторы.|  
|Логическое next()|Переход на следующую строку данных.|  
  
### <a name="sqlserverbulkcsvfilerecord"></a>SQLServerBulkCSVFileRecord  
 Простая реализация интерфейса ISQLServerBulkRecord, которая может использоваться для чтения базовых типов данных Java из файла с разделителями, где каждая строка представляет строку данных.  
  
 Примечания по реализации и ограничения  
  
1.  Максимальный объем данных в любой строке ограничивается объемом доступной памяти, поскольку данные считываются по одной строке за раз.  
  
2.  Потоковая передача типов данных большого размера, таких как varchar(max), varbinary(max), nvarchar(max), sqlxml и ntext, не поддерживается.  
  
3.  Разделитель, указанный для CSV-файла, не должен содержаться в данных и, если это зарезервированный символ, должен быть экранирован в регулярных выражениях Java.  
  
4.  В реализации CSV-файла двойные кавычки рассматриваются как часть данных. Например, строка hello,"world","hello,world" будет рассматриваться как строка с четырьмя столбцами со значениями hello, "world", "hello, world", если разделитель — запятая.  
  
5.  Символы новой строки используются в качестве признака конца строки и не допускаются в данных.  
  
|Конструктор|Описание|  
|-----------------|-----------------|  
|SQLServerBulkCSVFileRecord (filetoparse указанными строка, строка кодировки, разделитель строк, логическое firstLineIsColumnNamesSQLServerBulkCSVFileRecord (строка, строка, String, boolean)|Инициализирует новый экземпляр класса SQLServerBulkCSVFileRecord, который будет выполнять синтаксический анализ каждой строки в fileToParse с указанными разделителем и кодировкой. Если firstLineIsColumnNames имеет значение True, первая строка файла будет проанализирована как имена столбцов.  Если кодировка имеет значение NULL, будет использоваться кодировка по умолчанию.|  
|SQLServerBulkCSVFileRecord (строка filetoparse указанными, строка кодировки логическое firstLineIsColumnNamesSQLServerBulkCSVFileRecord (String, String, boolean)|Инициализирует новый экземпляр класса SQLServerBulkCSVFileRecord, который будет выполнять синтаксический анализ каждой строки в fileToParse с указанными разделителем-запятой и кодировкой. Если firstLineIsColumnNames имеет значение True, первая строка файла будет проанализирована как имена столбцов.  Если кодировка имеет значение NULL, будет использоваться кодировка по умолчанию.|  
|SQLServerBulkCSVFileRecord (строка filetoparse указанными, логическое firstLineIsColumnNamesSQLServerBulkCSVFileRecord (String, boolean)|Инициализирует новый экземпляр класса SQLServerBulkCSVFileRecord, который будет выполнять синтаксический анализ каждой строки в fileToParse с указанными разделителем-запятой и кодировкой по умолчанию. Если firstLineIsColumnNames имеет значение True, первая строка файла будет проанализирована как имена столбцов.|  
  
|Метод|Описание|  
|------------|-----------------|  
|Void addColumnMetadata (int positionInFile, строка columnName, int jdbcType, int точность, масштаб int)|Добавляет метаданные для указанного столбца в файле.|  
|Void close()|Освобождает все ресурсы, связанные со средством чтения файла.|  
|Void setTimestampWithTimezoneFormat (DateTim eFormatter dateTimeFormatter|Задает формат для синтаксического анализа данных отметки времени из файла как java.sql.Types.TIMESTAMP_WITH_TIMEZONE.|  
|Void setTimestampWithTimezoneFormat(String dateTimeFormat)setTimeWithTimezoneFormat(DateTimeFormatter)|Задает формат для синтаксического анализа данных времени из файла как java.sql.Types.TIME_WITH_TIMEZONE.|  
|Void setTimeWithTimezoneFormat (DateTimeForm atter dateTimeFormatter)|Задает формат для синтаксического анализа данных времени из файла как java.sql.Types.TIME_WITH_TIMEZONE.|  
|Void setTimeWithTimezoneFormat(String timeFormat)|Задает формат для синтаксического анализа данных времени из файла как java.sql.Types.TIME_WITH_TIMEZONE.|  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
