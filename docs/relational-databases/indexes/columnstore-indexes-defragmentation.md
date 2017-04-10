---
title: "Дефрагментация индексов columnstore | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3efda1a-7bdb-47f5-80bf-f075329edee5
caps.latest.revision: 17
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 15
---
# Дефрагментация индексов columnstore
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Задачи по дефрагментации индексов columnstore.  
  
## Дефрагментация индекса columnstore в оперативном режиме с помощью инструкции ALTER INDEX REORGANIZE  
 ПРИМЕНЯЕТСЯ К: SQL Server (начиная с версии 2016), база данных SQL Azure  
  
  После выполнения загрузок любого типа таблица deltastore может содержать несколько небольших групп строк. С помощью инструкции ALTER INDEX REORGANIZE можно принудительно отправить все группы строк в columnstore, а затем объединить их в меньшее число групп строк с большим количеством строк внутри.  Операция реорганизации также приведет к удалению строк, которые были удалены из columnstore.  
  
 Дополнительные сведения см в публикациях Сунила Агарвала (Sunil Agarwal) в блоге группы разработчиков ядра СУБД SQL.  
  
-   [Минимизация фрагментации индекса в индексах columnstore](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/columnstore-index-defragmentation-using-reorganize-command/)  
  
-   [Индексы columnstore и политика слияния для групп строк](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/08/columnstore-index-merge-policy-for-reorganize/)  
  
### Рекомендации по реорганизации  
 Реорганизуйте индекс columnstore после одной или нескольких загрузок данных, чтобы как можно быстрее повысить производительность запросов. Реорганизация изначально потребует дополнительных ресурсов ЦП для сжатия данных, что может снизить общую производительность системы. Однако после сжатия данных производительность запросов может возрасти.  
  
 Для расчета фрагментации воспользуйтесь примером из статьи [sys.dm_db_column_store_row_group_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md). Это поможет вам определить, стоит ли выполнять операцию REORGANIZE.  
  
### Пример. Как работает реорганизация  
 В этом примере показано, как инструкция ALTER INDEX REORGANIZE может принудительно отправить все группы строк deltastore в columnstore, а затем объединить эти группы строк.  
  
1.  Запустите этот код Transact-SQL, чтобы создать промежуточную таблицу, содержащую 300 000 строк. Мы воспользуемся ею для массовой загрузки строк в индекс columnstore.  
  
    ```  
    USE master;  
    GO  
  
    IF EXISTS (SELECT name FROM sys.databases  
        WHERE name = N'[columnstore]')  
        DROP DATABASE [columnstore];  
    GO  
  
    CREATE DATABASE [columnstore];  
    GO  
  
    IF EXISTS (SELECT name FROM sys.tables  
        WHERE name = N'staging'  
        AND object_id = OBJECT_ID (N'staging'))  
    DROP TABLE dbo.staging;  
    GO  
  
    CREATE TABLE [staging] (  
         AccountKey int NOT NULL,  
         AccountDescription nvarchar (50),  
         AccountType nvarchar(50),  
         AccountCodeAlternateKey int  
    );  
    GO  
  
    -- Load data  
    DECLARE @loop int;  
    DECLARE @AccountDescription varchar(50);  
    DECLARE @AccountKey int;  
    DECLARE @AccountType varchar(50);  
    DECLARE @AccountCode int;  
  
    SELECT @loop = 0;  
    BEGIN TRAN  
        WHILE (@loop < 300000)   
          BEGIN  
            SELECT @AccountKey = CAST (RAND()*10000000 AS int);  
            SELECT @AccountDescription = 'accountdesc ' + CONVERT(varchar(20), @AccountKey);  
            SELECT @AccountType = 'AccountType ' + CONVERT(varchar(20), @AccountKey);  
            SELECT @AccountCode =  CAST (RAND()*10000000 AS int);  
  
            INSERT INTO staging VALUES (  
               @AccountKey,   
               @AccountDescription,   
               @AccountType,   
               @AccountCode  
            );  
  
            SELECT @loop = @loop + 1;  
          END  
    COMMIT  
  
    ```  
  
2.  Создайте таблицу, сохраненную в виде индекса columnstore.  
  
    ```  
    IF EXISTS (SELECT name FROM sys.tables  
        WHERE name = N'cci_target'  
        AND object_id = OBJECT_ID (N'cci_target'))  
    DROP TABLE dbo.cci_target;  
    GO  
  
    -- Create a table with a clustered columnstore index  
    -- and the same columns as the rowstore staging table.  
    CREATE TABLE cci_target (  
         AccountKey int NOT NULL,  
         AccountDescription nvarchar (50),  
         AccountType nvarchar(50),  
         AccountCodeAlternateKey int,  
         INDEX idx_cci_target CLUSTERED COLUMNSTORE  
    )  
    GO  
  
    ```  
  
3.  Выполните массовую вставку строк промежуточной таблицы в таблицу columnstore. Инструкция INSERT INTO ... SELECT выполнит массовую вставку.   Инструкция TABLOCK запустит вставку в параллельном режиме.  
  
    ```  
    -- Insert rows in parallel  
    INSERT INTO cci_target WITH (TABLOCK)  
    SELECT TOP (300000) * FROM staging;  
    GO  
  
    ```  
  
4.  Для просмотра групп строк используйте динамическое административное представление (DMV) sys.dm_db_column_store_row_group_physical_stats.  
  
    ```  
    -- Run this dynamic management view (DMV) to see the OPEN rowgroups.   
    -- The number of rowgroups depends on the degree of parallelism.   
    -- You will see multiple OPEN rowgroups depending on the degree of parallelism.   
    -- This is because insert operation can run in parallel in SQL server 2016.  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
  
    ```  
  
     В данном примере результаты показывают 8 групп строк OPEN, в каждой из которых 37 500 строк. Количество групп строк OPEN зависит от параметра max_degree_of_parallelism.  
  
     ![OPEN rowgroups](../../relational-databases/indexes/media/cci-openrowgroups.png "OPEN rowgroups")  
  
5.  С помощью инструкции ALTER INDEX REORGANIZE с параметром COMPRESS_ALL_ROW_GROUPS принудительно отправьте все группы строк для сжатия в columnstore.  
  
    ```  
    -- This command will force all CLOSED and OPEN rowgroups into the columnstore.  
    ALTER INDEX idx_cci_target ON cci_target   
    REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
  
    ```  
  
     В результатах отобразится 8 групп строк COMPRESSED и 8 групп строк TOMBSTONE. Каждая группа строк сжимается в columnstore независимо от ее размера. Группы строк TOMBSTONE будут удалены системой.  
  
     ![TOMBSTONE and COMPRESSED rowgroups](../../relational-databases/indexes/media/cci-tombstone-compressed-rowgroups.png "TOMBSTONE and COMPRESSED rowgroups")  
  
6.  Для повышения производительности запросов гораздо лучше объединять небольшие группы строк вместе.  Инструкция ALTER INDEX REORGANIZE объединит группы строк COMPRESSED. Теперь, когда разностные группы строк сжаты в columnstore, еще раз запустите инструкцию ALTER INDEX REORGANIZE, чтобы объединить небольшие группы строк COMPRESSED. На этот раз не нужно указывать параметр COMPRESS_ALL_ROW_GROUPS.  
  
    ```  
    -- Run this again and you will see that smaller rowgroups   
    -- combined into one compressed rowgroup with 300,000 rows  
    ALTER INDEX idx_cci_target ON cci_target REORGANIZE;  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
    ```  
  
     В результатах будет видно, что 8 групп строк COMPRESSED теперь объединены в одну группу строк COMPRESSED.  
  
     ![Combined rowgroups](../../relational-databases/indexes/media/cci-compressed-rowgroups.png "Combined rowgroups")  
  
##  <a name="rebuild"></a> Дефрагментация индекса columnstore в автономном режиме с помощью инструкции ALTER INDEX REBUILD  
 Для SQL Server 2016 и более поздних версий перестройка индекса columnstore обычно не требуется, так как инструкция REORGANIZE выполняет необходимые действия для перестройки в фоновом режиме как операцию в оперативном режиме.  
  
 Перестройка индекса columnstore устраняет фрагментацию и перемещает все строки в columnstore. Для полного перестроения существующего кластеризованного индекса columnstore можно использовать инструкцию [CREATE COLUMNSTORE INDEX (Transact-SQL)](../../t-sql/statements/create-columnstore-index-transact-sql.md) или [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md). Кроме того, можно использовать инструкцию ALTER INDEX... REBUILD, чтобы перестроить конкретную секцию.  
  
### Процесс перестроения  
 Чтобы перестроить индекс columnstore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выполняет следующие действия.  
  
1.  Приобретает монопольную блокировку на таблице или секции на то время, как происходит перестроение.  Во время перестройки данные находятся в автономном режиме и недоступны даже при использовании NOLOCK, RCSI или SI.  
  
2.  Повторно сжимает все данные в columnstore. Во время перестроения существуют две копии индекса columnstore. После завершения перестроения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удаляет исходный индекс columnstore.  
  
### Рекомендации по перестройке индекса Columnstore  
 Перестройка индекса columnstore полезна для устранения фрагментации, а также для перемещения всех строк в columnstore. Предлагаются следующие рекомендации.  
  
1.  Перестраивайте секцию, а не всю таблицу.  
  
    -   Если индекс большой, то перестроение всей таблицы занимает много времени и на диске должно хватать места для сохранения дополнительной копии во время перестроения. Обычно бывает необходимо перестроить только недавно использованную секцию.  
  
    -   Для секционированных таблиц нет необходимости перестраивать весь индекс columnstore, поскольку фрагментация вероятна только в секциях, которые были недавно изменены. Таблицы фактов и большие таблицы измерений обычно бывают секционированы для выполнения операций резервного копирования и управления с фрагментами данных таблицы.  
  
2.  Перестраивайте секцию после масштабных операций DML.  
  
    -   Перестроение секции дефрагментирует ее и уменьшит занимаемое место на диске. При перестройке из columnstore будут удалены все строки, помеченные для удаления, а все группы строк будут перемещены из deltastore в columnstore. Обратите внимание, что в deltastore может быть несколько групп строк, каждая из которых может содержать менее миллиона строк.  
  
3.  Перестраивайте секцию после загрузки данных.  
  
    -   Это гарантирует, что все данные будут храниться в columnstore. Если каждый из параллельных процессов одновременно загружает менее 100 тысяч строк в одну и ту же секцию, в итоге в секции может оказаться несколько таблиц deltastore. Перестроение переместит все строки из deltastore в columnstore.  
  
## См. также:  
 [Руководство по индексам columnstore](../Topic/Columnstore%20Indexes%20Guide.md)   
 [Загрузка данных индексов ColumnStore](../Topic/Columnstore%20Indexes%20Data%20Loading.md)   
 [Сводка функций индексов columnstore по версиям](../Topic/Columnstore%20Indexes%20Versioned%20Feature%20Summary.md)   
 [Производительность запросов индексов columnstore](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
 [Начало работы с Columnstore для получения операционной аналитики в реальном времени](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 [Индексы сolumnstore для хранилищ данных](../Topic/Columnstore%20Indexes%20for%20Data%20Warehousing.md)   
 [Индексы ColumnStore для задач обслуживания](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)  
  
  