---
title: Дефрагментация индексов columnstore | Документация Майкрософт
ms.custom: ''
ms.date: 01/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d3efda1a-7bdb-47f5-80bf-f075329edee5
caps.latest.revision: 17
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a0729bd3d068c7a50c7f6e9df591909465c29003
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="columnstore-indexes---defragmentation"></a>Дефрагментация индексов columnstore
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Задачи по дефрагментации индексов columnstore.  
  
## <a name="use-alter-index-reorganize-to-defragment-a-columnstore-index-online"></a>Дефрагментация индекса columnstore в оперативном режиме с помощью инструкции ALTER INDEX REORGANIZE  
 **Применимо к:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]), [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
  
После выполнения загрузок любого типа таблица deltastore может содержать несколько небольших групп строк. С помощью инструкции `ALTER INDEX REORGANIZE` можно принудительно отправить все группы строк в columnstore, а затем объединить их в меньшее число групп строк с большим количеством строк внутри.  Операция реорганизации также приведет к удалению строк, которые были удалены из columnstore.  
  
Дополнительные сведения см. в следующих записях в блоге группы разработчиков ядра СУБД SQL:  
-   [Минимизация фрагментации индекса в индексах columnstore](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/columnstore-index-defragmentation-using-reorganize-command/)  
-   [Индексы columnstore и политика слияния для групп строк](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/08/columnstore-index-merge-policy-for-reorganize/)  
  
### <a name="recommendations-for-reorganizing"></a>Рекомендации по реорганизации  
Реорганизуйте индекс columnstore после одной или нескольких загрузок данных, чтобы как можно быстрее повысить производительность запросов. Реорганизация изначально потребует дополнительных ресурсов ЦП для сжатия данных, что может снизить общую производительность системы. Однако после сжатия данных производительность запросов может возрасти.  
  
Для расчета фрагментации воспользуйтесь примером из статьи [sys.dm_db_column_store_row_group_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md). Это поможет вам определить, стоит ли выполнять операцию REORGANIZE.  
  
### <a name="example-how-reorganizing-works"></a>Пример. Как работает реорганизация  
 В этом примере показано, как инструкция ALTER INDEX REORGANIZE может принудительно отправить все группы строк deltastore в columnstore, а затем объединить эти группы строк.  
  
1.  Запустите этот код Transact-SQL, чтобы создать промежуточную таблицу, содержащую 300 000 строк. Мы воспользуемся ею для массовой загрузки строк в индекс columnstore.  
  
    ```sql  
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
  
    ```sql  
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
  
3.  Выполните массовую вставку строк промежуточной таблицы в таблицу columnstore. Инструкция `INSERT INTO ... SELECT` выполнит массовую вставку. `TABLOCK` позволяет инструкции `INSERT` выполняться с параллелизмом.  
  
    ```sql  
    -- Insert rows in parallel  
    INSERT INTO cci_target WITH (TABLOCK)  
    SELECT TOP (300000) * FROM staging;  
    GO  
    ```  
  
4.  Для просмотра групп строк используйте динамическое административное представление (DMV) *sys.dm_db_column_store_row_group_physical_stats*.  
  
    ```sql  
    -- Run this dynamic management view (DMV) to see the OPEN rowgroups.   
    -- The number of rowgroups depends on the degree of parallelism.   
    -- You will see multiple OPEN rowgroups depending on the degree of parallelism.   
    -- This is because insert operation can run in parallel in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
    ```  
  
     В данном примере результаты показывают 8 групп строк OPEN, в каждой из которых 37 500 строк. Количество групп строк OPEN зависит от параметра *max_degree_of_parallelism*.  
  
     ![Группы строк OPEN](../../relational-databases/indexes/media/cci-openrowgroups.png "Группы строк OPEN")  
  
5.  Чтобы принудительно сжать все группы строк в columnstore, используйте инструкцию `ALTER INDEX REORGANIZE` с параметром `COMPRESS_ALL_ROW_GROUPS`.  
  
    ```sql  
    -- This command will force all CLOSED and OPEN rowgroups into the columnstore.  
    ALTER INDEX idx_cci_target ON cci_target   
    REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
    ```  
  
     В результатах отобразится 8 групп строк COMPRESSED и 8 групп строк TOMBSTONE. Каждая группа строк сжимается в columnstore независимо от ее размера. Группы строк TOMBSTONE будут удалены системой.  
  
     ![Группы строк TOMBSTONE и COMPRESSED](../../relational-databases/indexes/media/cci-tombstone-compressed-rowgroups.png "Группы строк TOMBSTONE и COMPRESSED")  
  
6.  Для повышения производительности запросов гораздо лучше объединять небольшие группы строк вместе. Инструкция `ALTER INDEX REORGANIZE` объединит группы строк `COMPRESSED`. Теперь, когда разностные группы строк сжаты в columnstore, еще раз запустите инструкцию ALTER INDEX REORGANIZE, чтобы объединить небольшие группы строк COMPRESSED. На этот раз параметр `COMPRESS_ALL_ROW_GROUPS` не нужен.  
  
    ```sql  
    -- Run this again and you will see that smaller rowgroups   
    -- combined into one compressed rowgroup with 300,000 rows  
    ALTER INDEX idx_cci_target ON cci_target REORGANIZE;  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
    ```  
  
     В результатах будет видно, что 8 групп строк COMPRESSED теперь объединены в одну группу строк COMPRESSED.  
  
     ![Комбинированные группы строк](../../relational-databases/indexes/media/cci-compressed-rowgroups.png "Комбинированные группы строк")  
  
## <a name="rebuild"></a> Дефрагментация индекса columnstore в автономном режиме с помощью инструкции ALTER INDEX REBUILD  
 Для [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] и более поздних версий перестройка индекса columnstore обычно не требуется, так как инструкция `REORGANIZE` выполняет необходимые действия для перестройки в фоновом режиме как операцию в оперативном режиме.  
  
 Перестройка индекса columnstore устраняет фрагментацию и перемещает все строки в columnstore. Для полного перестроения существующего кластеризованного индекса columnstore можно использовать инструкцию [CREATE COLUMNSTORE INDEX (Transact-SQL)](../../t-sql/statements/create-columnstore-index-transact-sql.md) или [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md). Кроме того, можно использовать инструкцию ALTER INDEX... REBUILD, чтобы перестроить конкретную секцию.  
  
### <a name="rebuild-process"></a>Процесс перестроения  
 Чтобы перестроить индекс columnstore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выполняет следующие действия.  
  
1.  Приобретает монопольную блокировку на таблице или секции на то время, как происходит перестроение. Во время перестройки данные находятся в автономном режиме и недоступны даже при использовании `NOLOCK`, RCSI или SI.  
  
2.  Повторно сжимает все данные в columnstore. Во время перестроения существуют две копии индекса columnstore. После завершения перестроения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удаляет исходный индекс columnstore.  
  
### <a name="recommendations-for-rebuilding-a-columnstore-index"></a>Рекомендации по перестройке индекса Columnstore  
 Перестройка индекса columnstore полезна для устранения фрагментации, а также для перемещения всех строк в columnstore. Предлагаются следующие рекомендации.  
  
1.  Перестраивайте секцию, а не всю таблицу.  
    -   Если индекс большой, то перестроение всей таблицы занимает много времени и на диске должно хватать места для сохранения дополнительной копии во время перестроения. Обычно бывает необходимо перестроить только недавно использованную секцию.  
    -   Для секционированных таблиц нет необходимости перестраивать весь индекс columnstore, поскольку фрагментация вероятна только в секциях, которые были недавно изменены. Таблицы фактов и большие таблицы измерений обычно бывают секционированы для выполнения операций резервного копирования и управления с фрагментами данных таблицы.  

2.  Перестраивайте секцию после масштабных операций DML.  
    -   Перестроение секции дефрагментирует ее и уменьшит занимаемое место на диске. При перестройке из columnstore будут удалены все строки, помеченные для удаления, а все группы строк будут перемещены из deltastore в columnstore. Обратите внимание, что в deltastore может быть несколько групп строк, каждая из которых может содержать менее миллиона строк.  
  
3.  Перестраивайте секцию после загрузки данных.  
    -   Это гарантирует, что все данные будут храниться в columnstore. Если каждый из параллельных процессов одновременно загружает менее 100 тысяч строк в одну и ту же секцию, в итоге в секции может оказаться несколько таблиц deltastore. Перестроение переместит все строки из deltastore в columnstore.  

## <a name="automatic-index-and-statistics-management"></a>Автоматическое управление индексами и статистикой

Используйте такие решения, как [Адаптивная дефрагментация индексов](http://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag), чтобы автоматически управлять дефрагментацией индексов и обновлениями статистики для одной базы данных или нескольких. Эта процедура автоматически выбирает, следует ли перестроить или реорганизовать индекс, сверяясь с уровнем фрагментации и другими параметрами, и обновляет статистику на основе линейных пороговых значений.

## <a name="see-also"></a>См. также:        
[Новые возможности индексов columnstore](../../relational-databases/indexes/columnstore-indexes-what-s-new.md)    
[Производительность запросов индексов columnstore](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
[Начало работы с Columnstore для получения операционной аналитики в реальном времени](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
[Индексы сolumnstore для хранилищ данных](../../relational-databases/indexes/columnstore-indexes-data-warehouse.md)  
[Архитектура индексов columnstore](../../relational-databases/sql-server-index-design-guide.md#columnstore_index)    
[Адаптивная дефрагментация индексов](http://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag)    
  
  
